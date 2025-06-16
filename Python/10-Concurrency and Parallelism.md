# ✅ 1. Difference Between Threading, Multiprocessing, and Asynchronous Programming in Python

| Feature        | Threading                 | Multiprocessing             | Asynchronous Programming     |
| -------------- | ------------------------- | --------------------------- | ---------------------------- |
| Purpose        | Concurrency using threads | Parallelism using processes | Non-blocking async tasks     |
| CPU Usage      | Single-core (due to GIL)  | Multi-core                  | Single-core                  |
| Suitable For   | I/O-bound tasks           | CPU-bound tasks             | I/O-bound tasks              |
| Speed-up       | Context switching         | True parallelism            | Non-blocking awaitable tasks |
| Common Modules | `threading`               | `multiprocessing`           | `asyncio`                    |

---

### 📌 1.1 Threading Example (Good for I/O Tasks)

```python
import threading
import time

def task(name):
    print(f'Starting {name}')
    time.sleep(2)
    print(f'Ending {name}')

# Create threads
t1 = threading.Thread(target=task, args=('Thread 1',))
t2 = threading.Thread(target=task, args=('Thread 2',))

# Start threads
t1.start()
t2.start()

# Wait for threads to finish
t1.join()
t2.join()
```

✔️ **Threads share memory** but cannot truly run Python code in parallel because of the **Global Interpreter Lock (GIL)**.
Useful for tasks like network requests or file I/O.

---

### 📌 1.2 Multiprocessing Example (Good for CPU Tasks)

```python
import multiprocessing
import time

def task(name):
    print(f'Starting {name}')
    time.sleep(2)
    print(f'Ending {name}')

if __name__ == '__main__':
    p1 = multiprocessing.Process(target=task, args=('Process 1',))
    p2 = multiprocessing.Process(target=task, args=('Process 2',))

    p1.start()
    p2.start()

    p1.join()
    p2.join()
```

✔️ **Multiprocessing bypasses the GIL** and achieves **true parallelism** using separate processes with their own memory space.

---

### 📌 1.3 Asynchronous Programming Example (Best for I/O-bound Tasks)

```python
import asyncio

async def task(name):
    print(f'Starting {name}')
    await asyncio.sleep(2)
    print(f'Ending {name}')

async def main():
    await asyncio.gather(
        task('Task 1'),
        task('Task 2')
    )

asyncio.run(main())
```

✔️ Uses **event loop** to switch between tasks without creating threads or processes.
Best for network I/O, APIs, and tasks where you don’t want to block the application.

---

## 🔸 Key Differences:

* **Threading**: Concurrency, shared memory, not truly parallel.
* **Multiprocessing**: Parallelism, separate memory, heavy on CPU.
* **Async**: Non-blocking I/O, very lightweight, runs in a single thread.

---

# ✅ 2. What Are Race Conditions? How Do You Avoid Them in Python?

### ✔️ Explanation:

A **race condition** happens when:

* **Two or more threads/processes access shared data simultaneously.**
* The final result depends on the order of execution (which is unpredictable).

---

### 📌 Example of a Race Condition

```python
import threading

counter = 0

def increment():
    global counter
    for _ in range(1000000):
        counter += 1

t1 = threading.Thread(target=increment)
t2 = threading.Thread(target=increment)

t1.start()
t2.start()
t1.join()
t2.join()

print("Final counter:", counter)  # Expected: 2000000, but may not be!
```

✔️ The **counter may not reach 2,000,000** because both threads can read and write at the same time → causing a race.

---

## ✅ How to Avoid Race Conditions?

### 🔹 Solution 1: Use Locks

```python
import threading

counter = 0
lock = threading.Lock()

def increment():
    global counter
    for _ in range(1000000):
        with lock:  # Locking critical section
            counter += 1

t1 = threading.Thread(target=increment)
t2 = threading.Thread(target=increment)

t1.start()
t2.start()
t1.join()
t2.join()

print("Final counter:", counter)  # Now reliably 2000000
```

✔️ `with lock:` ensures that **only one thread can access the critical section at a time.**

---

### 🔹 Solution 2: Use `multiprocessing.Value` (for Multiprocessing)

```python
import multiprocessing

def increment(counter, lock):
    for _ in range(1000000):
        with lock:
            counter.value += 1

if __name__ == '__main__':
    counter = multiprocessing.Value('i', 0)
    lock = multiprocessing.Lock()

    p1 = multiprocessing.Process(target=increment, args=(counter, lock))
    p2 = multiprocessing.Process(target=increment, args=(counter, lock))

    p1.start()
    p2.start()
    p1.join()
    p2.join()

    print("Final counter:", counter.value)  # Correct result
```

✔️ `multiprocessing.Value` is a shared variable between processes, protected by a `Lock`.

---

## ✅ Summary Table

| Concept           | Explanation                             | Solution                         |
| ----------------- | --------------------------------------- | -------------------------------- |
| Threading         | Concurrency, shared memory              | `threading` module               |
| Multiprocessing   | True parallelism, separate memory       | `multiprocessing` module         |
| Async Programming | Non-blocking I/O, lightweight           | `asyncio` module                 |
| Race Condition    | Data conflict between threads/processes | Use Locks, use atomic operations |

---

If you want:

* I can **build a multi-threaded downloader** or an **async API client** with you.
* I can explain **synchronization techniques** in real-world applications.

Let me know if you want to go deeper into these topics!
