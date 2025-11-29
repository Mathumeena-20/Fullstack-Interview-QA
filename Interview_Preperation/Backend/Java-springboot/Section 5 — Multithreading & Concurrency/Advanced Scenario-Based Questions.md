## 1) Design a thread-safe cache (LRU, bounded)

**Idea:** Use `LinkedHashMap` with access-order and override `removeEldestEntry`, and make operations thread-safe by synchronizing access or by using `ConcurrentHashMap` + `ConcurrentLinkedDeque` for higher concurrency.

### Simple synchronized LRU (good, easy, correct)

```java
import java.util.LinkedHashMap;
import java.util.Map;

public class SynchronizedLRUCache<K,V> {
    private final int capacity;
    private final Map<K,V> map;

    public SynchronizedLRUCache(int capacity) {
        this.capacity = capacity;
        this.map = new LinkedHashMap<>(capacity, 0.75f, true) {
            @Override protected boolean removeEldestEntry(Map.Entry<K,V> eldest) {
                return size() > SynchronizedLRUCache.this.capacity;
            }
        };
    }

    public synchronized V get(K key) {
        return map.get(key);
    }

    public synchronized void put(K key, V value) {
        map.put(key, value);
    }

    public synchronized int size() { return map.size(); }
}
```

**Why:** `LinkedHashMap` handles LRU; `synchronized` makes it thread-safe. Simple and correct for moderate concurrency.

---

## 2) How to avoid deadlocks

**Principles**

* Acquire locks in a **fixed global order**.
* Keep lock scope **small**.
* Use `tryLock(timeout)` to fail fast and recover.
* Prefer higher-level concurrency utilities (e.g. concurrent collections, actors) to manual locks.
* Avoid holding a lock while doing I/O / blocking operations.

### Example (avoid deadlock using tryLock)

```java
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;
import java.util.concurrent.TimeUnit;

Lock a = new ReentrantLock();
Lock b = new ReentrantLock();

void safeTransfer() throws InterruptedException {
    while (true) {
        if (a.tryLock(500, TimeUnit.MILLISECONDS)) {
            try {
                if (b.tryLock(500, TimeUnit.MILLISECONDS)) {
                    try {
                        // do work
                        return;
                    } finally { b.unlock(); }
                }
            } finally { a.unlock(); }
        }
        // retry or back off
        Thread.sleep(10);
    }
}
```

**Why:** `tryLock` with timeout avoids permanent waiting and lets thread back off instead of deadlocking.

---

## 3) How to limit concurrent user requests in a system

**Simple approach:** Use a `Semaphore` with max concurrent permits.

```java
import java.util.concurrent.Semaphore;

public class RequestLimiter {
    private final Semaphore sem;

    public RequestLimiter(int maxConcurrent) {
        this.sem = new Semaphore(maxConcurrent);
    }

    public void handleRequest(Runnable task) {
        boolean acquired = false;
        try {
            sem.acquire();
            acquired = true;
            task.run();
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        } finally {
            if (acquired) sem.release();
        }
    }
}
```

**Why:** Semaphore gives you natural backpressure; extra requests block (or can be rejected if you use `tryAcquire`).

---

## 4) Design a rate limiter using `Semaphore` (simple concurrent limit per window)

**Goal:** Allow N parallel operations per time window. This is not a token-bucket full implementation, but a simple sliding-window-ish limiter using a permit refill scheduler.

```java
import java.util.concurrent.*;
import java.util.concurrent.atomic.AtomicInteger;

public class SimpleRateLimiter {
    private final Semaphore permits;
    private final int maxPermits;
    private final ScheduledExecutorService scheduler = Executors.newSingleThreadScheduledExecutor();

    public SimpleRateLimiter(int permitsPerSecond) {
        this.maxPermits = permitsPerSecond;
        this.permits = new Semaphore(permitsPerSecond);
        // refill permits each second
        scheduler.scheduleAtFixedRate(() -> {
            int toRelease = maxPermits - permits.availablePermits();
            if (toRelease > 0) permits.release(toRelease);
        }, 1, 1, TimeUnit.SECONDS);
    }

    public boolean tryAcquire() {
        return permits.tryAcquire();
    }

    public void shutdown() {
        scheduler.shutdownNow();
    }
}
```

**Why:** Very simple: refill a fixed number of permits each second. For production use consider token-bucket libraries or Guava RateLimiter.

---

## 5) How do you handle async non-blocking APIs?

**Patterns**

* Use `CompletableFuture` + non-blocking IO client.
* Use reactive stacks (Reactor, RxJava) for streams.
* Avoid blocking the common pool — provide custom `ExecutorService` for blocking tasks.

### Example: Use `CompletableFuture` with custom pool for blocking call

```java
ExecutorService ioPool = Executors.newFixedThreadPool(20); // for blocking IO

CompletableFuture.supplyAsync(() -> blockingHttpCall(), ioPool)
    .thenApply(result -> parse(result))
    .exceptionally(ex -> fallback());
```

**Why:** Keeps caller non-blocking; offloads blocking operations to a separate pool.

---

## 6) Create 10 threads that print numbers sequentially (use synchronization)

**Task interpretation:** 10 threads should print numbers 1..N in strict order, where each number is printed by the thread whose turn it is. Implementation below: threads with ids 0..9 print numbers in round-robin order (1..max).

```java
public class SequentialPrinter {
    private final Object lock = new Object();
    private final int threadCount;
    private final int max;
    private int current = 1; // number to print
    private final int startId = 0;

    public SequentialPrinter(int threadCount, int max) {
        this.threadCount = threadCount;
        this.max = max;
    }

    public void start() {
        for (int id = 0; id < threadCount; id++) {
            final int tid = id;
            new Thread(() -> {
                while (true) {
                    synchronized (lock) {
                        while (current <= max && (current - 1) % threadCount != tid) {
                            try { lock.wait(); } catch (InterruptedException e) { Thread.currentThread().interrupt(); return; }
                        }
                        if (current > max) { lock.notifyAll(); return; }
                        System.out.println("Thread-" + tid + " prints " + current);
                        current++;
                        lock.notifyAll();
                    }
                }
            }, "T-" + id).start();
        }
    }

    public static void main(String[] args) {
        new SequentialPrinter(10, 100).start();
    }
}
```

**Why:** Each thread waits until `(current - 1) % threadCount == tid`. Then prints and notifies.

---

## 7) Implement producer–consumer using `wait` / `notify`

Classic bounded buffer:

```java
import java.util.LinkedList;
import java.util.Queue;

public class PCWaitNotify {
    private final Queue<Integer> queue = new LinkedList<>();
    private final int capacity;

    public PCWaitNotify(int capacity) { this.capacity = capacity; }

    public void produce(int item) throws InterruptedException {
        synchronized (queue) {
            while (queue.size() == capacity) queue.wait();
            queue.offer(item);
            queue.notifyAll();
        }
    }

    public int consume() throws InterruptedException {
        synchronized (queue) {
            while (queue.isEmpty()) queue.wait();
            int item = queue.poll();
            queue.notifyAll();
            return item;
        }
    }

    // demo
    public static void main(String[] args) {
        PCWaitNotify buf = new PCWaitNotify(5);
        Thread producer = new Thread(() -> {
            try {
                for (int i=1;i<=20;i++) {
                    buf.produce(i);
                    System.out.println("Produced: " + i);
                    Thread.sleep(50);
                }
            } catch (InterruptedException e) { Thread.currentThread().interrupt(); }
        });

        Thread consumer = new Thread(() -> {
            try {
                for (int i=1;i<=20;i++) {
                    int v = buf.consume();
                    System.out.println("Consumed: " + v);
                    Thread.sleep(100);
                }
            } catch (InterruptedException e) { Thread.currentThread().interrupt(); }
        });

        producer.start(); consumer.start();
    }
}
```

**Why:** `wait()` releases lock; `notifyAll()` wakes producers/consumers.

---

## 8) Submit 5 tasks to a thread pool and wait for all to finish

Use `invokeAll` or submit multiple futures and `get()`.

```java
import java.util.*;
import java.util.concurrent.*;

public class WaitForAll {
    public static void main(String[] args) throws Exception {
        ExecutorService pool = Executors.newFixedThreadPool(3);
        List<Callable<String>> tasks = Arrays.asList(
            () -> { Thread.sleep(500); return "A"; },
            () -> { Thread.sleep(300); return "B"; },
            () -> { Thread.sleep(200); return "C"; },
            () -> { Thread.sleep(400); return "D"; },
            () -> { Thread.sleep(100); return "E"; }
        );

        // Option 1: invokeAll (blocks until all complete)
        List<Future<String>> results = pool.invokeAll(tasks);
        for (Future<String> f : results) System.out.println(f.get());

        // Option 2: submit and wait
        /*List<Future<String>> futures = new ArrayList<>();
        for (Callable<String> t : tasks) futures.add(pool.submit(t));
        for (Future<String> f : futures) System.out.println(f.get());*/

        pool.shutdown();
    }
}
```

**Why:** `invokeAll` submits and blocks until all tasks finish (or timeout if you use timed variant).

---

## 9) Use `CompletableFuture` to call 3 APIs in parallel and merge results

Simulated API calls with `supplyAsync`, then combine with `thenCombine` or `allOf`.

```java
import java.util.concurrent.*;
import java.util.*;

public class ParallelAPIs {
    static ExecutorService pool = Executors.newFixedThreadPool(5);

    static CompletableFuture<String> callA() {
        return CompletableFuture.supplyAsync(() -> { sleep(300); return "A"; }, pool);
    }
    static CompletableFuture<String> callB() {
        return CompletableFuture.supplyAsync(() -> { sleep(200); return "B"; }, pool);
    }
    static CompletableFuture<String> callC() {
        return CompletableFuture.supplyAsync(() -> { sleep(100); return "C"; }, pool);
    }

    static void sleep(long ms) { try { Thread.sleep(ms); } catch (InterruptedException e) { Thread.currentThread().interrupt(); } }

    public static void main(String[] args) throws Exception {
        CompletableFuture<String> fA = callA();
        CompletableFuture<String> fB = callB();
        CompletableFuture<String> fC = callC();

        // Option: allOf then collect results
        CompletableFuture<Void> all = CompletableFuture.allOf(fA, fB, fC);
        CompletableFuture<List<String>> allResults = all.thenApply(v -> {
            return List.of(fA.join(), fB.join(), fC.join()); // join is safe here because all completed
        });

        System.out.println(allResults.get()); // prints [A, B, C] (order depends on calls)
        pool.shutdown();
    }
}
```

**Why:** `allOf` waits for all; `join()` is safe after `allOf` completed.

---

## 10) Explain thread-safety of `ConcurrentHashMap` internally (concise)

**Key points**

* **Non-blocking reads:** `get()` reads volatile references and traverses nodes without locking.
* **CAS-based updates:** Basic insertion into empty bin uses CAS to insert node pointer.
* **Fine-grained locking:** If CAS fails or chain exists, `synchronized` is used on the bin (bucket), limiting locking to that bucket.
* **Treeification:** If a bucket grows beyond a threshold, it becomes a balanced tree (Red-Black), so worst-case lookup becomes `O(log n)`.
* **Resizing:** Carefully implemented using CAS + transfer mechanics so readers remain correct; resizing is done incrementally.
* **No `null` keys/values:** avoids ambiguity in concurrent reads.

**Why safe:** combination of volatile, CAS, minimal synchronized blocks, and lock-free reads give high concurrency with correctness. (Implementation details: `Node[] table`, `transfer` logic, `TreeBin`, `ForwardingNode` etc. — Java 8+.)

---

## Quick summary / when to use which:

* **Use `synchronized`** for simple mutual exclusion.
* **Use `ReentrantLock` / `tryLock` / `lockInterruptibly`** when you need advanced control.
* **Use `Semaphore`** to limit concurrent accesses.
* **Use `BlockingQueue`** or `ExecutorService` for producer/consumer and thread pooling.
* **Use `ConcurrentHashMap`** for highly concurrent maps (no nulls).
* **Use `CompletableFuture`** or reactive libraries for non-blocking async composition.

---

