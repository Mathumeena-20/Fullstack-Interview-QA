# ✅ 1. **What are PEP8 Guidelines?**

### ✔️ Explanation:

**PEP 8** is the **Python Enhancement Proposal 8**, which defines the **style guide for writing clean, readable Python code.**

It promotes:

* Consistency across Python codebases.
* Improved readability and maintainability.

---

### 📌 Key PEP 8 Rules:

| Topic           | Guideline                                   | Example                          |
| --------------- | ------------------------------------------- | -------------------------------- |
| Indentation     | 4 spaces per indentation level              | `if True:`<br>    `print('Yes')` |
| Line Length     | Maximum 79 characters per line              | `# Use line breaks if too long`  |
| Blank Lines     | Separate functions and classes with 2 lines |                                  |
| Variable Naming | Use lowercase\_with\_underscores            | `my_variable = 10`               |
| Class Naming    | Use CapitalizedWords                        | `class MyClass:`                 |
| Imports         | Standard library → Third-party → Local apps |                                  |
| Spaces          | `a = 5` not `a=5`                           |                                  |
| Docstrings      | Use triple quotes for documentation         | `"""This is a docstring."""`     |

---

### 📌 Example:

```python
# Bad
def Add(x,y):return x+y

# Good (PEP 8 compliant)
def add(x, y):
    """Return the sum of x and y."""
    return x + y
```

---

### ✅ Tools to Check PEP8:

* `flake8` → Linter to check PEP8 violations.
* `black` → Auto-formatting tool.
* `pylint` → Code analysis and linting.

```bash
pip install flake8
flake8 myscript.py
```

---

# ✅ 2. **How Do You Manage Virtual Environments in Python?**

### ✔️ Explanation:

A **virtual environment** is an isolated Python environment where:

* Project-specific dependencies are installed.
* You can avoid conflicts between different projects.

---

### 📌 Steps to Create and Use a Virtual Environment:

```bash
# 1. Create virtual environment
python -m venv venv

# 2. Activate (Linux/Mac)
source venv/bin/activate

# 2. Activate (Windows)
venv\Scripts\activate

# 3. Install project packages
pip install flask

# 4. Deactivate the environment
deactivate
```

✔️ When activated, installed packages are **only available inside that environment.**

---

### ✅ Benefits:

* Dependency isolation.
* Prevent version conflicts.
* Easy to recreate environment using `requirements.txt`.

---

# ✅ 3. **How Do You Handle Dependency Management?**

### ✔️ Explanation:

Dependency management means **tracking and controlling external packages your project needs.**

The most common approach in Python:

* Use a `requirements.txt` file.
* Use tools like **pip, pipenv, poetry, or conda**.

---

### 📌 Example: Using `pip` and `requirements.txt`

```bash
# Install packages
pip install flask requests

# Save installed packages
pip freeze > requirements.txt

# Later, to install all dependencies in a new environment
pip install -r requirements.txt
```

---

### 📌 Example `requirements.txt`

```txt
Flask==3.0.2
requests==2.31.0
```

---

### ✅ Modern Dependency Management Tools:

| Tool   | Features                             |
| ------ | ------------------------------------ |
| pip    | Standard package installer           |
| pipenv | Virtual env + dependency lock        |
| poetry | Advanced tool with packaging support |
| conda  | Manages Python and system packages   |

---

### 📌 Example: Using `pipenv`

```bash
# Install package and create environment
pipenv install flask

# Activate environment
pipenv shell

# Save environment
Pipfile and Pipfile.lock are auto-created
```

---

## ✅ Summary

| Concept               | Purpose                            | Tools / Commands                                            |
| --------------------- | ---------------------------------- | ----------------------------------------------------------- |
| PEP8                  | Code styling and consistency       | flake8, black, pylint                                       |
| Virtual Environments  | Project isolation                  | venv, pipenv, conda                                         |
| Dependency Management | Track and install project packages | pip freeze, pip install -r requirements.txt, pipenv, poetry |

---

### 👉 If you want, I can:

* Help you write a **PEP8-compliant mini project**.
* Show you how to set up **pipenv or poetry** step-by-step.
* Explain **best practices for deployment** with virtual environments.

Let me know!
