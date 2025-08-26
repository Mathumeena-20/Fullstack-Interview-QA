## 1️⃣ Difference between Process and Thread

* **Process** → Independent execution unit with its own memory space.
* **Thread** → Lightweight unit of execution inside a process; shares process memory.

🔹 Example:

* Process → MS Word app
* Threads → Spell-check, autosave, UI rendering inside MS Word.

---

## 2️⃣ How to Create a Thread (Runnable vs Thread)

Two ways:

1. **Extending Thread class**

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running...");
    }
    public static void main(String[] args) {
        MyThread t = new MyThread();
        t.start(); // calls run internally
    }
}
```

2. **Implementing Runnable (preferred – allows multiple inheritance)**

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable running...");
    }
    public static void main(String[] args) {
        Thread t = new Thread(new MyRunnable());
        t.start();
    }
}
```

---

## 3️⃣ Difference between `start()` and `run()`

* **start()** → Creates a new thread, then calls `run()` in that thread.
* **run()** → Just a normal method call (runs in current thread).

🔹 Example:

```java
class Test extends Thread {
    public void run() { System.out.println("Running in " + Thread.currentThread().getName()); }
    public static void main(String[] args) {
        Test t = new Test();
        t.start(); // new thread
        t.run();   // current main thread
    }
}
```

---

## 4️⃣ Difference between synchronized method and synchronized block

* **Synchronized method** → Locks the entire method (object lock).
* **Synchronized block** → Locks only a portion of code (fine-grained lock).

🔹 Example:

```java
class Counter {
    private int count = 0;

    // Whole method locked
    public synchronized void increment() {
        count++;
    }

    // Only block locked
    public void incrementBlock() {
        synchronized(this) {
            count++;
        }
    }
}
```

---

## 5️⃣ Deadlock, Livelock, Starvation

* **Deadlock** → Two threads waiting on each other’s lock → both stuck forever.
* **Livelock** → Threads keep responding to each other but no progress (they’re “too polite”).
* **Starvation** → A thread waits indefinitely because others keep getting CPU (low priority thread ignored).

---

## 6️⃣ Difference between sleep(), yield(), and join()

* **sleep(ms)** → Pauses current thread for given time.
* **yield()** → Suggests scheduler to pause current thread and give chance to others (not guaranteed).
* **join()** → Makes current thread wait until another thread finishes.

🔹 Example:

```java
class Test extends Thread {
    public void run() {
        for(int i=0;i<3;i++) {
            System.out.println(Thread.currentThread().getName());
            try { Thread.sleep(500); } catch(Exception e){}
        }
    }
    public static void main(String[] args) throws Exception {
        Test t1 = new Test(); Test t2 = new Test();
        t1.start();
        t1.join(); // main waits until t1 completes
        t2.start();
    }
}
```

---

## 7️⃣ What is ThreadLocal in Java?

* Provides **thread-local variables** → each thread gets its own copy.
* Useful for user sessions, DB connections.

🔹 Example:

```java
class Test {
    private static ThreadLocal<Integer> threadLocal = ThreadLocal.withInitial(() -> 0);

    public static void main(String[] args) {
        Runnable r = () -> {
            int val = threadLocal.get();
            threadLocal.set(val + 1);
            System.out.println(Thread.currentThread().getName() + " → " + threadLocal.get());
        };
        new Thread(r).start();
        new Thread(r).start();
    }
}
```

---

## 8️⃣ Difference between Callable and Runnable

* **Runnable** → `run()` method, cannot return value or throw checked exception.
* **Callable** → `call()` method, returns a value (`Future`) and can throw checked exception.

🔹 Example:

```java
import java.util.concurrent.*;

class Test {
    public static void main(String[] args) throws Exception {
        Callable<Integer> task = () -> 5+10;
        ExecutorService service = Executors.newSingleThreadExecutor();
        Future<Integer> future = service.submit(task);
        System.out.println(future.get()); // 15
        service.shutdown();
    }
}
```

---

## 9️⃣ ExecutorService and ThreadPool

* **ExecutorService** → Manages thread lifecycle for you.
* **ThreadPool** → A pool of reusable threads (avoids creating/destroying threads repeatedly).

🔹 Example:

```java
import java.util.concurrent.*;

class Test {
    public static void main(String[] args) {
        ExecutorService service = Executors.newFixedThreadPool(2);

        for(int i=0;i<5;i++) {
            service.execute(() -> System.out.println(Thread.currentThread().getName()));
        }

        service.shutdown();
    }
}
```

---

## 🔟 Difference between wait(), notify(), and notifyAll()

* **wait()** → Makes thread wait until notified. (Releases lock)
* **notify()** → Wakes up one waiting thread.
* **notifyAll()** → Wakes up all waiting threads.

🔹 Example (producer-consumer):

```java
class Shared {
    private boolean available = false;

    synchronized void produce() throws InterruptedException {
        while(available) wait();
        System.out.println("Produced");
        available = true;
        notify();
    }

    synchronized void consume() throws InterruptedException {
        while(!available) wait();
        System.out.println("Consumed");
        available = false;
        notify();
    }
}
```

---

✅ **Interview Pointers (Quick Recap):**

* Process vs Thread → Process = independent, Thread = lightweight inside process.
* start() vs run() → start() → new thread, run() → same thread.
* sync method = whole method lock, sync block = part of code lock.
* Deadlock = stuck, Livelock = busy but no progress, Starvation = ignored thread.
* sleep(), yield(), join() → pause, hint, wait-for-thread.
* ThreadLocal → thread-specific variable.
* Runnable vs Callable → no return vs return value.
* ExecutorService → manages thread pool.
* wait/notify → thread communication.
