# **1. What is a Fail-Fast Iterator?**

A **fail-fast iterator** immediately throws a
✔ `ConcurrentModificationException (CME)`
when a collection is modified **structurally** while iterating.

Structural modifications =

* adding new element
* removing element (not via iterator)
* modifying internal structure

Fail-fast iterators try to **prevent inconsistent data**.

---

# **2. What Causes ConcurrentModificationException?**

You get `ConcurrentModificationException` when:

1. Collection is modified **while iterating**
2. Modification is NOT done using iterator’s own `remove()` method
3. `modCount` changes unexpectedly

### Example:

```java
List<Integer> list = new ArrayList<>();
list.add(1); list.add(2); list.add(3);

for (Integer n : list) {
    list.add(4); // Structural modification during iteration
}
// Throws ConcurrentModificationException
```

---

# **3. Why Are ArrayList Iterators Fail-Fast?**

Because `ArrayList` uses:

### `modCount` (modification count)

* Increments on every structural change
* Iterator stores **expectedModCount**
* If `modCount != expectedModCount` → throw CME

Fail-fast behavior ensures **consistency and safety**.

---

# **4. Example of Fail-Fast Iteration**

```java
List<String> list = new ArrayList<>();
list.add("A");
list.add("B");

Iterator<String> it = list.iterator();

while (it.hasNext()) {
    System.out.println(it.next());
    list.add("C");  // ← Modification
}
```

Output:

```
A
Exception in thread "main" java.util.ConcurrentModificationException
```

---

# **5. What Are Fail-Safe Iterators?**

Fail-safe iterators:

✔ Do NOT throw ConcurrentModificationException
✔ Iterate over a **shallow copy** of the collection
✔ Allow modification during iteration

### But:

❌ Iteration does NOT reflect new changes
❌ Memory overhead (copy created)

---

# **6. Which Collections Provide Fail-Safe Iterators?**

Fail-safe collections (from `java.util.concurrent`):

| Collection               | Iterator Type |
| ------------------------ | ------------- |
| **CopyOnWriteArrayList** | Fail-safe     |
| **ConcurrentHashMap**    | Fail-safe     |
| **CopyOnWriteArraySet**  | Fail-safe     |

These collections are designed for concurrency.

---

# **7. Why ConcurrentHashMap Iterators Are Fail-Safe?**

Because:

* They iterate over a **snapshot** of the map entries
* Structural modifications do NOT affect the current iteration
* No `ConcurrentModificationException`

### Example (valid):

```java
ConcurrentHashMap<Integer, String> map = new ConcurrentHashMap<>();
map.put(1, "A");
map.put(2, "B");

for (Integer key : map.keySet()) {
    map.put(3, "C");  // Allowed
}
```

---

# **8. Can We Modify a Collection While Iterating?**

### Yes, BUT only in specific cases:

### ❌ Normal collections (ArrayList, HashMap)

* You CANNOT modify them during iteration
* Except using iterator’s `remove()` method

### ✔ Example of safe modification:

```java
Iterator<Integer> it = list.iterator();
while (it.hasNext()) {
    int value = it.next();
    if (value == 2) it.remove(); // safe
}
```

### ✔ Concurrent collections

You CAN modify while iterating (fail-safe).

---

# **9. Difference Between Iterator and Enumeration**

| Feature            | Iterator                    | Enumeration                            |
| ------------------ | --------------------------- | -------------------------------------- |
| Introduced         | Java 1.2                    | Java 1.0                               |
| Methods            | hasNext(), next(), remove() | hasMoreElements(), nextElement()       |
| Fail-fast          | ✔ Yes                       | ❌ No                                   |
| Removal supported? | ✔ Yes                       | ❌ No                                   |
| Used for           | All collections             | Legacy collections (Vector, Hashtable) |

Iterator is modern, more powerful → preferred.

---

# **10. Internal Mechanism of Fail-Fast Iterators**

Fail-fast iterators depend on:

### **modCount** in Collection class

* Tracks structural modifications

### **expectedModCount** in Iterator

* Iterator stores modCount at creation time

### During iteration:

If:

```
modCount != expectedModCount
```

→ `ConcurrentModificationException` is thrown.

### Why?

To prevent inconsistent behavior and corrupted iteration.

---

# ⭐ Final Interview Summary

| Topic                   | Explanation                                          |
| ----------------------- | ---------------------------------------------------- |
| Fail-fast               | Throws CME when collection is modified               |
| Fail-safe               | Works on clone → no CME                              |
| HashMap & ArrayList     | Fail-fast                                            |
| ConcurrentHashMap       | Fail-safe                                            |
| CopyOnWriteArrayList    | Fail-safe                                            |
| Modify while iterating  | Only via iterator.remove() or concurrent collections |
| Iterator vs Enumeration | Iterator supports remove + fail-fast                 |

---

