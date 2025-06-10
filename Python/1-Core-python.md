Here’s a **detailed answer, explanation, and example** for each of the Python interview questions you listed:

---

## 1. **What are Python's Key Features?**

### Explanation:

* **Easy to Learn and Readable:** Clear syntax.
* **Interpreted Language:** Executes line by line.
* **Dynamically Typed:** No need to declare variable types.
* **High-Level Language:** Memory management handled automatically.
* **Extensive Libraries:** Wide range of standard and third-party libraries.
* **Portable:** Runs across platforms (Windows, Mac, Linux).
* **Object-Oriented and Functional:** Supports both paradigms.

---

## 2. **Explain Python's Memory Management.**

### Explanation:

* Python uses **reference counting** as its primary memory management technique.
* **Garbage collection** cleans up objects with circular references.
* Python’s memory is managed in private heaps (inaccessible to the programmer directly).

---

## 3. **What are Python's Data Types?**

### Common Data Types:

* **Numeric:** `int`, `float`, `complex`
* **Sequence:** `list`, `tuple`, `range`
* **Text:** `str`
* **Set:** `set`, `frozenset`
* **Mapping:** `dict`
* **Boolean:** `True`, `False`
* **Binary:** `bytes`, `bytearray`, `memoryview`

---

## 4. **Explain the difference between `is` and `==`.**

### Explanation:

* `is`: Checks **identity** (whether two references point to the same object).
* `==`: Checks **equality** (whether the values are the same).

### Example:

```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a is b)  # True
print(a == b)  # True

print(a is c)  # False
print(a == c)  # True
```

---

## 5. **What are Mutable and Immutable Types in Python?**

### Explanation:

* **Mutable:** Can be changed after creation.
* **Immutable:** Cannot be changed after creation.

| Type    | Example    | Mutable? |
| ------- | ---------- | -------- |
| List    | \[1, 2, 3] | Yes      |
| Tuple   | (1, 2, 3)  | No       |
| Set     | {1, 2, 3}  | Yes      |
| Dict    | {"a": 1}   | Yes      |
| String  | "abc"      | No       |
| Integer | 1          | No       |

---

## 6. **What are Python's Built-in Data Structures?**

* **List:** Ordered, mutable collection.
* **Tuple:** Ordered, immutable collection.
* **Set:** Unordered, unique items.
* **Dictionary:** Key-value pairs.

---

## 7. **How are Lists, Tuples, Sets, and Dictionaries Different?**

| Feature    | List | Tuple | Set | Dictionary              |
| ---------- | ---- | ----- | --- | ----------------------- |
| Ordered    | Yes  | Yes   | No  | Yes                     |
| Mutable    | Yes  | No    | Yes | Yes                     |
| Duplicates | Yes  | Yes   | No  | Keys: No, Values: Yes   |
| Indexing   | Yes  | Yes   | No  | Keys instead of indexes |

---

## 8. **What is List Comprehension? Give Examples.**

### Explanation:

A compact way to generate lists using a single line of code.

### Example:

```python
squares = [x * x for x in range(5)]
print(squares)  # [0, 1, 4, 9, 16]
```

---

## 9. \*\*What are \*args and **kwargs?**

### Explanation:

* `*args`: Accepts variable positional arguments.
* `**kwargs`: Accepts variable keyword arguments.

### Example:

```python
def demo(*args, **kwargs):
    print(args)
    print(kwargs)

demo(1, 2, 3, name="John", age=30)

# Output:
# (1, 2, 3)
# {'name': 'John', 'age': 30}
```

---

## 10. **How is Exception Handling Done in Python?**

### Example:

```python
try:
    num = 10 / 0
except ZeroDivisionError as e:
    print("Error:", e)
finally:
    print("This always executes.")

# Output:
# Error: division by zero
# This always executes.
```

---

## 11. **What is the Difference Between Deep Copy and Shallow Copy?**

### Explanation:

* **Shallow Copy:** Copies references of nested objects.
* **Deep Copy:** Creates new nested objects.

### Example:

```python
import copy

original = [[1, 2], [3, 4]]

shallow = copy.copy(original)
deep = copy.deepcopy(original)

original[0][0] = 99

print(shallow)  # [[99, 2], [3, 4]] affected
print(deep)     # [[1, 2], [3, 4]] unaffected
```

---

## 12. **How Does Python's Garbage Collection Work?**

### Explanation:

* Python uses **reference counting**.
* When reference count drops to zero, the object is destroyed.
* Python also has a **cyclic garbage collector** to detect reference cycles.

---

## 13. **Explain the Global Interpreter Lock (GIL).**

### Explanation:

* GIL ensures that only one thread executes Python bytecode at a time.
* This can limit multi-threading in CPU-bound tasks.
* Multi-processing is used to bypass GIL for parallel execution.

---

## 14. **How Do Python's Iterators and Generators Work?**

### Explanation:

* **Iterator:** Object with `__iter__()` and `__next__()` methods.
* **Generator:** Special function that yields values one by one using `yield`.

### Example (Iterator):

```python
my_list = [1, 2, 3]
iterator = iter(my_list)

print(next(iterator))  # 1
print(next(iterator))  # 2
```

### Example (Generator):

```python
def my_gen():
    yield 1
    yield 2
    yield 3

for val in my_gen():
    print(val)

# Output:
# 1
# 2
# 3
```

---

## 15. **What is the Difference Between a Generator and a Normal Function?**

| Feature     | Normal Function   | Generator Function        |
| ----------- | ----------------- | ------------------------- |
| Returns     | Single value      | Yields sequence of values |
| Memory      | Stores all values | Generates on demand       |
| Performance | Higher memory use | More memory efficient     |

---

### ✅ Would you like:

* **More real coding problems?**
* **Mock interview questions with answers?**
* **Python system design topics?**

Let me know and I can prepare those for you!
