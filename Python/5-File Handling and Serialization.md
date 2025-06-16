# ✅ 1. **How Do You Read and Write Files in Python?**

### 📌 Reading a File

```python
# Open the file in read mode
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
```

✔️ **Explanation:**

* `'r'` mode → Read text file.
* `with` statement automatically closes the file (recommended practice).
* `file.read()` reads the entire file.

---

### 📌 Writing to a File

```python
# Open the file in write mode (creates/overwrites file)
with open('example.txt', 'w') as file:
    file.write("Hello, Python!")
```

✔️ **Explanation:**

* `'w'` mode → Write mode (overwrites file).
* `'a'` mode → Append mode.

---

### 📌 Reading a File Line-by-Line

```python
with open('example.txt', 'r') as file:
    for line in file:
        print(line.strip())  # strip() removes newline characters
```

---

### 📌 Writing Multiple Lines

```python
lines = ["Python\n", "is\n", "awesome!\n"]

with open('example.txt', 'w') as file:
    file.writelines(lines)
```

---

# ✅ 2. **What is the Difference Between `rb` and `r` Modes?**

| Mode   | Description              | Use Case                |
| ------ | ------------------------ | ----------------------- |
| `'r'`  | Read text mode (default) | Text files (.txt, .csv) |
| `'rb'` | Read binary mode         | Images, PDFs, etc.      |

### 📌 Example:

```python
# Text file read
with open('example.txt', 'r') as file:
    content = file.read()

# Binary file read (image)
with open('image.jpg', 'rb') as file:
    content = file.read()
```

✔️ **Key Point:**

* Use `'rb'` for files like images, videos, PDFs (non-text files).
* Use `'r'` for standard text files.

---

# ✅ 3. **How Do You Serialize Data in Python? (Pickle vs JSON)**

### 🔹 **Serialization:**

Serialization is converting a Python object into a byte stream or a JSON string to save it or transfer it.

---

### 📌 **Pickle Module (Python-Specific Serialization)**

* Can serialize **any Python object** (including custom classes, functions).
* Not human-readable.
* Can only be used in Python.

#### Example:

```python
import pickle

data = {'name': 'Alice', 'age': 30}

# Serialize to file
with open('data.pkl', 'wb') as file:
    pickle.dump(data, file)

# Deserialize from file
with open('data.pkl', 'rb') as file:
    loaded_data = pickle.load(file)

print(loaded_data)
```

✔️ **Key Points:**

* Use `'wb'` for writing in binary mode.
* Use `'rb'` for reading in binary mode.
* Pickled files are not portable across different languages.

---

### 📌 **JSON Module (Language-Independent Serialization)**

* Can serialize **standard data types** (dict, list, str, int, etc.).
* Human-readable.
* Can be shared across languages (JavaScript, Python, etc.).

#### Example:

```python
import json

data = {'name': 'Bob', 'age': 25}

# Serialize to JSON file
with open('data.json', 'w') as file:
    json.dump(data, file)

# Deserialize from JSON file
with open('data.json', 'r') as file:
    loaded_data = json.load(file)

print(loaded_data)
```

✔️ **Key Points:**

* JSON supports basic Python types only.
* File is readable by humans and other programming languages.

---

### ✅ **Summary: Pickle vs JSON**

| Feature              | Pickle             | JSON                                     |
| -------------------- | ------------------ | ---------------------------------------- |
| Readable             | No                 | Yes                                      |
| Python-Specific      | Yes                | No                                       |
| Data Types Supported | All Python objects | Basic types (dict, list, str, int, etc.) |
| Language Support     | Python only        | Multi-language                           |

---

### 🔥 Quick Review:

| Concept                | Example                   | Mode   |
| ---------------------- | ------------------------- | ------ |
| File Read (Text)       | `open('file.txt', 'r')`   | `'r'`  |
| File Read (Binary)     | `open('image.jpg', 'rb')` | `'rb'` |
| Pickle Serialization   | `pickle.dump(data, file)` | `'wb'` |
| Pickle Deserialization | `pickle.load(file)`       | `'rb'` |
| JSON Serialization     | `json.dump(data, file)`   | `'w'`  |
| JSON Deserialization   | `json.load(file)`         | `'r'`  |

---

If you want, I can also:

* Give **real-world file handling coding questions**
* Share **common interview pitfalls** related to file handling and serialization
* Provide **mock Python file handling exercises**

Let me know!
