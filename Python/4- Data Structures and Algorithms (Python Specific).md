
# ✅ 1. How Do You Implement a Stack/Queue in Python?

### 📌 **Stack** (LIFO – Last In First Out)

The most common stack operations are **push** (insert) and **pop** (remove the last item).

```python
# Stack using list
stack = []

# Push elements
stack.append(10)
stack.append(20)
stack.append(30)

# Pop elements
print(stack.pop())  # Output: 30
print(stack)        # Remaining stack: [10, 20]
```

✔️ **Time Complexity:**

* Push: O(1)
* Pop: O(1)

---

### 📌 **Queue** (FIFO – First In First Out)

The most efficient queue implementation is using `collections.deque`.

```python
from collections import deque

# Queue using deque
queue = deque()

# Enqueue elements
queue.append(10)
queue.append(20)
queue.append(30)

# Dequeue elements
print(queue.popleft())  # Output: 10
print(queue)            # Remaining queue: deque([20, 30])
```

✔️ **Time Complexity:**

* Enqueue: O(1)
* Dequeue: O(1)

---

# ✅ 2. What is the Time Complexity of Key List, Dict, and Set Operations in Python?

| Operation           | List | Dict | Set  |
| ------------------- | ---- | ---- | ---- |
| Access              | O(1) | O(1) | N/A  |
| Search (in)         | O(n) | O(1) | O(1) |
| Insert (append/add) | O(1) | O(1) | O(1) |
| Delete              | O(n) | O(1) | O(1) |

✔️ **Summary:**

* **Lists:** Fast for indexing, slow for searching/deletion by value.
* **Dicts/Sets:** Extremely fast (hash table) for lookup, insertion, and deletion.

---

# ✅ 3. How Do You Reverse a List in Python? (Different Ways)

### Method 1: Using Slicing

```python
lst = [1, 2, 3, 4]
reversed_list = lst[::-1]
print(reversed_list)  # Output: [4, 3, 2, 1]
```

### Method 2: Using `reversed()`

```python
lst = [1, 2, 3, 4]
print(list(reversed(lst)))  # Output: [4, 3, 2, 1]
```

### Method 3: Using `reverse()` (In-place)

```python
lst = [1, 2, 3, 4]
lst.reverse()
print(lst)  # Output: [4, 3, 2, 1]
```

✔️ **Key Difference:**

* `[::-1]` and `reversed()` create a new list.
* `reverse()` modifies the original list.

---

# ✅ 4. How Would You Remove Duplicates from a List?

### Method 1: Using Set (Unordered)

```python
lst = [1, 2, 2, 3, 4, 4]
unique = list(set(lst))
print(unique)  # Output: [1, 2, 3, 4] (order not guaranteed)
```

### Method 2: Using `dict.fromkeys()` (Preserves Order)

```python
lst = [1, 2, 2, 3, 4, 4]
unique = list(dict.fromkeys(lst))
print(unique)  # Output: [1, 2, 3, 4]
```

### Method 3: Manual Loop (Preserves Order)

```python
lst = [1, 2, 2, 3, 4, 4]
unique = []
for item in lst:
    if item not in unique:
        unique.append(item)
print(unique)  # Output: [1, 2, 3, 4]
```

✔️ **Best Practice:**

* Use `dict.fromkeys()` if order is important.
* Use `set()` for speed when order doesn't matter.

---

# ✅ 5. Python String Manipulation Questions

### 🔹 **Reversal:**

```python
s = "hello"
print(s[::-1])  # Output: 'olleh'
```

### 🔹 **Splitting:**

```python
s = "apple,banana,cherry"
print(s.split(','))  # Output: ['apple', 'banana', 'cherry']
```

### 🔹 **Searching:**

```python
s = "hello world"
print(s.find('world'))  # Output: 6 (position)
print('world' in s)     # Output: True
```

### 🔹 **Replacing:**

```python
s = "I love Python"
print(s.replace("love", "like"))  # Output: I like Python
```

### 🔹 **Joining:**

```python
words = ['Python', 'is', 'awesome']
print(' '.join(words))  # Output: Python is awesome
```

---

# ✅ 6. How Do You Sort a List of Custom Objects?

### Example:

```python
class Employee:
    def __init__(self, name, age):
        self.name = name
        self.age = age

employees = [
    Employee("Alice", 30),
    Employee("Bob", 25),
    Employee("Charlie", 35)
]

# Sort by age
employees.sort(key=lambda x: x.age)

for emp in employees:
    print(emp.name, emp.age)
```

✔️ **Explanation:**

* `key=lambda x: x.age` tells Python to sort based on the `age` attribute.
* You can sort by any attribute using this method.

---

# ✅ 7. Explain Slicing and Its Use Cases

### 🔹 Syntax:

```python
list[start:stop:step]
```

### 🔹 Example:

```python
lst = [0, 1, 2, 3, 4, 5]

print(lst[1:4])    # Output: [1, 2, 3]
print(lst[:3])     # Output: [0, 1, 2]
print(lst[::2])    # Output: [0, 2, 4]
print(lst[::-1])   # Output: [5, 4, 3, 2, 1, 0]
```

### 🔹 Use Cases:

* Extracting sublists
* Skipping elements
* Reversing lists
* Quick manipulation of lists, tuples, and strings

---

# 🔥 Summary Table

| Topic               | Quick Explanation                          |
| ------------------- | ------------------------------------------ |
| Stack               | LIFO, use `append()` and `pop()`           |
| Queue               | FIFO, use `collections.deque`              |
| Time Complexity     | List: O(n) search, Dict/Set: O(1) search   |
| Reverse List        | Use `[::-1]`, `reverse()`, or `reversed()` |
| Remove Duplicates   | Use `set()`, `dict.fromkeys()`, or a loop  |
| String Manipulation | Split, search, replace, join, reverse      |
| Sort Custom Objects | Use `sort(key=lambda x: attr)`             |
| Slicing             | Extract, skip, reverse efficiently         |

---

If you want, I can provide:

* **Practice coding problems** on these topics
* **Sample Python coding tests**
* **Python mock interview questions and answers**

Let me know if you’d like to continue!
