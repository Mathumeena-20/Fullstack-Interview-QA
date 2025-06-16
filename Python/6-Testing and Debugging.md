
# ✅ 1. What Python Frameworks Do You Use for Testing? (pytest, unittest)

### 📌 Common Testing Frameworks:

| Framework  | Features                          |
| ---------- | --------------------------------- |
| `unittest` | Built-in, xUnit style, structured |
| `pytest`   | Most popular, simple, powerful    |
| `nose`     | Legacy, less commonly used now    |

✔️ **Most Recommended:**

* `pytest` for its simple syntax and better reporting.
* `unittest` is great when you need to stick to standard libraries.

---

# ✅ 2. How Do You Write Unit Tests in Python?

### 📌 Using `unittest` (Built-in Framework)

```python
import unittest

def add(a, b):
    return a + b

class TestMath(unittest.TestCase):
    def test_add(self):
        self.assertEqual(add(2, 3), 5)

if __name__ == '__main__':
    unittest.main()
```

✔️ **Explanation:**

* Create test classes inheriting from `unittest.TestCase`.
* Test methods should start with `test_`.
* `assertEqual` checks if the result matches the expected value.

---

### 📌 Using `pytest` (External Framework, more popular)

```python
def add(a, b):
    return a + b

def test_add():
    assert add(2, 3) == 5
```

✔️ **Explanation:**

* Very simple: no class, just functions.
* Use `assert` statements directly.
* Run using `pytest` command in terminal.

---

### ✔️ Comparison:

| Feature    | unittest             | pytest                  |
| ---------- | -------------------- | ----------------------- |
| Complexity | More boilerplate     | Very simple             |
| Built-in   | Yes                  | No (needs installation) |
| Popularity | Less modern projects | Widely used             |

---

# ✅ 3. How Does Python Logging Work?

### 📌 Basic Logging Example:

```python
import logging

# Configure logging
logging.basicConfig(level=logging.INFO)

logging.debug("This is a debug message")
logging.info("This is an info message")
logging.warning("This is a warning")
logging.error("This is an error")
logging.critical("This is critical")
```

✔️ **Explanation:**

* **Logging Levels:** DEBUG < INFO < WARNING < ERROR < CRITICAL
* You can control what level of logs are printed using `basicConfig(level=...)`.
* Default log format: `LEVEL:root:message`

---

### 📌 Custom Logging Example:

```python
import logging

# Configure with custom format
logging.basicConfig(filename='app.log', level=logging.DEBUG,
                    format='%(asctime)s - %(levelname)s - %(message)s')

logging.info("Logging to a file with timestamp")
```

✔️ **Explanation:**

* `filename` writes logs to a file.
* `format` customizes log output (timestamp, level, message).

---

### ✔️ Key Benefits of Logging:

* Helps track program flow and errors.
* Better than print statements for production.
* You can log to files, streams, or external systems.

---

# ✅ 4. How Do You Debug a Python Program?

### 📌 Common Debugging Methods:

1. **Using `print()` statements**

   * Basic, but not scalable.

2. **Using Logging (preferred in real projects)**

   ```python
   import logging
   logging.basicConfig(level=logging.DEBUG)
   logging.debug("Variable x: %s", x)
   ```

3. **Using Python Debugger (`pdb`)**

   ```python
   import pdb

   def test_debug():
       x = 5
       pdb.set_trace()  # Pause execution here
       y = 10
       z = x + y
       print(z)

   test_debug()
   ```

   ✔️ **When you run the program:**

   * Execution will pause at `set_trace()`.
   * You can type commands like `n` (next), `c` (continue), `p x` (print x), etc.

4. **Using IDE Debuggers**

   * Most Python IDEs (like VS Code, PyCharm) have built-in debugging tools with breakpoints, step-through, and variable watching.

---

### ✅ Debugging Commands in `pdb`

| Command | Description            |
| ------- | ---------------------- |
| `n`     | Next line              |
| `c`     | Continue execution     |
| `p var` | Print variable value   |
| `q`     | Quit debugging session |

---

# ✅ Summary Table

| Concept      | Tool/Approach   | Key Advantage             |
| ------------ | --------------- | ------------------------- |
| Unit Testing | unittest        | Built-in, structured      |
| Unit Testing | pytest          | Simple, modern            |
| Logging      | logging module  | Production-grade tracking |
| Debugging    | print()         | Basic, quick              |
| Debugging    | logging.debug() | Trace variables cleanly   |
| Debugging    | pdb             | Step-by-step analysis     |
| Debugging    | IDE Breakpoints | Visual step debugging     |

---

If you want:

* **Sample Python unit test interview problems**
* **Real-world debugging exercises**
* **Advanced logging configuration**

👉 Let me know, and I can help you prepare step-by-step!
