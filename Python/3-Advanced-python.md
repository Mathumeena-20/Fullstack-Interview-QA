## 1. **What is a Decorator? How Do You Write One?**

### Explanation:

* A **decorator** is a function that modifies the behavior of another function.
* It allows adding functionality without changing the original function’s code.

### Example:

```python
def decorator_func(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@decorator_func
def say_hello():
    print("Hello!")

say_hello()

# Output:
# Before function call
# Hello!
# After function call
```

---

## 2. **What are Python’s First-Class Functions?**

### Explanation:

In Python, **functions are first-class citizens**:

* They can be passed as arguments.
* They can be returned from other functions.
* They can be assigned to variables.

### Example:

```python
def greet(name):
    return f"Hello, {name}"

def executor(func, name):
    return func(name)

print(executor(greet, "Alice"))  # Output: Hello, Alice
```

---

## 3. **Explain Context Managers and the `with` Statement.**

### Explanation:

* Context managers handle **setup and cleanup actions**.
* The `with` statement ensures resources (like files) are properly closed even if an error occurs.

### Example:

```python
with open('file.txt', 'r') as file:
    content = file.read()

# The file is automatically closed after the block
```

You can also create custom context managers using `__enter__` and `__exit__`.

---

## 4. **What is a Lambda Function? When Should It Be Used?**

### Explanation:

* A **lambda function** is an anonymous, inline function.
* Used for **small, simple functions** passed as arguments.

### Example:

```python
square = lambda x: x * x
print(square(5))  # Output: 25

# Example with sorted
items = [("apple", 2), ("banana", 3), ("cherry", 1)]
sorted_items = sorted(items, key=lambda x: x[1])
print(sorted_items)
```

✅ **When to Use:**

* In one-liner functions, usually in `map`, `filter`, `sorted`.

---

## 5. **What are Python’s Built-in Modules You Frequently Use?**

| Module        | Use Case                        |
| ------------- | ------------------------------- |
| `os`          | File and directory operations   |
| `sys`         | System-specific parameters      |
| `datetime`    | Date and time manipulation      |
| `re`          | Regular expressions             |
| `math`        | Mathematical operations         |
| `json`        | JSON parsing and generation     |
| `collections` | Advanced data structures        |
| `functools`   | Function tools like `lru_cache` |

---

## 6. **Explain Multi-threading vs. Multi-processing in Python.**

| Feature    | Multi-threading                       | Multi-processing                  |
| ---------- | ------------------------------------- | --------------------------------- |
| Definition | Multiple threads in one process       | Multiple processes                |
| GIL Impact | GIL restricts parallelism (CPU-bound) | True parallel execution           |
| Use Case   | I/O-bound tasks (network, file I/O)   | CPU-bound tasks (data processing) |
| Libraries  | `threading`                           | `multiprocessing`                 |

### Example (Threading):

```python
import threading

def task():
    print("Task running")

thread = threading.Thread(target=task)
thread.start()
```

---

## 7. **What are `functools` and How Are They Used?**

### Explanation:

* `functools` is a Python module that provides higher-order functions for functional programming.

### Common Functions:

* `@lru_cache`: Caching results of expensive function calls.
* `partial`: Fixes some function arguments.
* `wraps`: Used in decorators to preserve function metadata.

### Example:

```python
from functools import lru_cache

@lru_cache(maxsize=100)
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(10))  # Faster with caching
```

---

## 8. **How Does `asyncio` Work in Python?**

### Explanation:

* `asyncio` provides asynchronous, non-blocking programming.
* Best for tasks like network requests, I/O-bound workloads.

### Example:

```python
import asyncio

async def greet():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

asyncio.run(greet())
```

✅ **Key Concepts:**

* `async` keyword defines an asynchronous function.
* `await` pauses the coroutine until the awaited result is ready.

---

## 9. **What is Monkey Patching?**

### Explanation:

* Monkey patching means **dynamically modifying classes or modules at runtime.**
* Often used for testing or quick fixes.

### Example:

```python
class Dog:
    def speak(self):
        print("Bark")

def new_speak():
    print("Woof")

# Monkey patching
Dog.speak = new_speak

dog = Dog()
dog.speak()  # Output: Woof
```

✅ **Note:**
Monkey patching can cause maintenance problems and unexpected behavior. Use carefully.

---

# 🔥 Summary Table

| Concept           | Purpose/Use                       |
| ----------------- | --------------------------------- |
| Decorator         | Modify function behavior          |
| First-class Funcs | Functions treated as objects      |
| Context Manager   | Setup/cleanup management          |
| Lambda Function   | Small anonymous functions         |
| Built-in Modules  | Reusable core functionality       |
| Multi-threading   | I/O-bound parallelism             |
| Multi-processing  | CPU-bound parallelism             |
| functools         | Function tools (caching, partial) |
| asyncio           | Asynchronous event loop           |
| Monkey Patching   | Dynamic runtime modification      |

---

If you want, I can:

* Provide **practice problems** on these topics
* Create a **mock coding test** for you
* Help you write **project-level Python code using decorators, threads, or asyncio**

Let me know!
