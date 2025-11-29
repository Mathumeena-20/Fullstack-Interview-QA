## 1. Thread Lifecycle

1. What are the different states in the Java thread lifecycle?
2. Difference between `WAITING` and `TIMED_WAITING` states.
3. What happens when `start()` is called on a thread internally?
4. Difference between `sleep()` and `wait()`.
5. What is `yield()` and how does it work?
6. Can a thread be restarted after termination?
7. When does a thread enter the BLOCKED state?
8. How does JVM perform context switching?
9. Difference between user thread and daemon thread.
10. What causes thread starvation?

---

## 2. Runnable vs Thread

1. Difference between implementing `Runnable` and extending `Thread`.
2. Why is `Runnable` preferred over `Thread`?
3. Can a class extend both `Thread` and another class?
4. What happens if you call `run()` instead of `start()`?
5. Is `Runnable` a functional interface?
6. Can lambda be used with Runnable?
7. Can we reuse a thread object?
8. How to return value from a thread?
9. What happens if multiple threads call the same Runnable instance?
10. Real-world scenarios where Runnable is preferred.

---

## 3. ExecutorService

1. What is `ExecutorService`?
2. Difference between `execute()` and `submit()`.
3. Different types of thread pools:

   * FixedThreadPool
   * CachedThreadPool
   * ScheduledThreadPool
   * WorkStealingPool
4. How does thread pool improve performance?
5. What is `shutdown()` vs `shutdownNow()`?
6. What happens if you don't shut down ExecutorService?
7. What is ThreadPoolExecutor?
8. How to create custom thread pool?
9. How task queue works in thread pool?
10. What is rejection handler?

---

## 4. Future & Callable

1. Difference between `Runnable` and `Callable`.
2. What is `Future`?
3. How do you get result from Future?
4. Difference between `get()` and `get(timeout)`?
5. What is blocking vs non-blocking call?
6. How do you cancel a running task?
7. Difference between `invokeAll()` and `invokeAny()`.
8. Explain timeout handling in Future.
9. What is `CompletionService`?
10. How is Callable useful in real applications?

---

## 5. volatile vs synchronized

1. What is the purpose of `volatile` keyword?
2. Difference between `volatile` and `synchronized`.
3. Does volatile guarantee atomicity?
4. What is memory visibility problem?
5. Explain happens-before relationship.
6. Can volatile fix race conditions?
7. Performance difference between synchronized and volatile.
8. Can we use both volatile and synchronized together?
9. Explain double-checked locking with volatile.
10. When should you prefer volatile over synchronized?

---

## 6. Locks & Semaphores

1. Difference between synchronized and Lock interface.
2. What is ReentrantLock?
3. Difference between fair and unfair lock.
4. What is a Semaphore?
5. Difference between Mutex and Semaphore.
6. What is ReadWriteLock?
7. Advantages of Lock over synchronized.
8. What is TryLock?
9. How does Lock handle interruption?
10. Real-world use case for Semaphore.

---

## 7. Concurrent Collections

1. Difference between `HashMap` and `ConcurrentHashMap`.
2. What are concurrent collections in Java?
3. Difference between `CopyOnWriteArrayList` and `Collections.synchronizedList()`.
4. When should you use `BlockingQueue`?
5. Types of BlockingQueue.
6. Producer-consumer using BlockingQueue.
7. What is skip list?
8. Difference between ConcurrentSkipListMap and TreeMap.
9. How concurrent collections avoid locking issues?
10. What is non-blocking algorithm?

---

## 8. CompletableFuture

1. What is CompletableFuture?
2. Difference between `Future` and `CompletableFuture`.
3. What is asynchronous programming?
4. What is `supplyAsync()` and `runAsync()`?
5. Difference between `thenApply()`, `thenAccept()`, and `thenRun()`.
6. Difference between `thenCompose()` and `thenCombine()`.
7. How to handle exceptions using `exceptionally()`?
8. What is `allOf()` and `anyOf()`?
9. How thread pool is selected in CompletableFuture?
10. Real-time use cases of CompletableFuture in microservices.

---

## 🔥 Advanced Scenario-Based Questions

1. Design a thread-safe cache.
2. How to avoid deadlocks?
3. How to limit concurrent user requests in a system?
4. Design rate limiter using Semaphore.
5. How do you handle async non-blocking APIs?
6. Create 10 threads that print numbers sequentially (use synchronization).
7. Implement producer–consumer using wait/notify.
8. Submit 5 tasks to a thread pool and wait for all to finish.
9. Use CompletableFuture to call 3 APIs in parallel and merge results.
10. Explain thread-safety of ConcurrentHashMap internally.
---


