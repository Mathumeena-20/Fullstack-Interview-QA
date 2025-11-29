# ✅ **1. When would you prefer Set over List in a real application?**

Use **Set** when:

| Requirement                  | Reason                   |
| ---------------------------- | ------------------------ |
| No duplicates allowed        | Set enforces uniqueness  |
| Fast search/lookup           | HashSet gives O(1)       |
| Order not important          | Sets are optimal         |
| Need sorted or unique values | TreeSet or LinkedHashSet |

### Examples (Real-World):

* Maintaining **unique users logged in** → HashSet
* Storing **unique roles/permissions** → LinkedHashSet
* Keeping sorted **employee IDs** → TreeSet

---

# ✅ **2. How would you design a cache using Map?**

A simple cache uses a **HashMap** to store key → value.
For auto-expire or LRU behavior, use **LinkedHashMap**.

### LRU Cache using LinkedHashMap:

```java
class LRUCache<K, V> extends LinkedHashMap<K, V> {
    private final int capacity;

    LRUCache(int capacity) {
        super(capacity, 0.75f, true); // accessOrder = true
        this.capacity = capacity;
    }

    @Override
    protected boolean removeEldestEntry(Map.Entry<K, V> eldest) {
        return size() > capacity;
    }
}
```

### Usage:

```java
LRUCache<Integer, String> cache = new LRUCache<>(3);
cache.put(1, "A"); cache.put(2, "B"); cache.put(3, "C");
cache.get(1);       // 1 becomes most recently used
cache.put(4, "D");  // removes least used key: 2
```

---

# ✅ **3. How do you handle concurrent modification in multithreading?**

### Avoid **ConcurrentModificationException**

Use:

### ✔ Option 1: Concurrent Collections

* `ConcurrentHashMap`
* `CopyOnWriteArrayList`
* `ConcurrentLinkedQueue`

### ✔ Option 2: Iterator.remove()

```java
Iterator<Integer> it = list.iterator();
while (it.hasNext()) {
    if (it.next() == 5) it.remove();
}
```

### ✔ Option 3: Synchronization

```java
synchronized(list) {
    for (int i : list) {}
}
```

---

# ✅ **4. Why does HashMap performance degrade in some situations?**

### Reasons:

1. **Poor hashCode() implementation** → leads to collisions.
2. Many keys fall into same bucket → long linked list → O(n) lookup.
3. Under heavy load factor > 0.75 → resize cost.
4. Lots of data → treeification threshold not met  → slower.
5. Memory pressure causing GC.

### Java 8 fix:

* Converts long chains into **Red-Black Trees** → O(log n).

---

# ✅ **5. How would you design your own custom collection?**

### Steps:

1. Create a class and implement `Collection` or `List` or extend `AbstractList`.
2. Maintain an **internal array**.
3. Implement required methods:

   * `add()`
   * `get()`
   * `size()`
   * `remove()`

### Example (Simple IntList):

```java
class IntList {
    private int[] arr = new int[10];
    private int size = 0;

    void add(int value) {
        if (size == arr.length) resize();
        arr[size++] = value;
    }

    int get(int index) {
        return arr[index];
    }

    private void resize() {
        int[] newArr = new int[arr.length * 2];
        System.arraycopy(arr, 0, newArr, 0, arr.length);
        arr = newArr;
    }
}
```

---

# ✅ **6. Implement Comparator to sort by salary → name**

```java
Comparator<Employee> comp =
    Comparator.comparing(Employee::getSalary)
              .thenComparing(Employee::getName);
```

### Full example:

```java
Collections.sort(list, comp);
```

---

# ✅ **7. Given a list of strings, return the first non-repeating character**

### Approach:

* Count frequency using a Map
* Iterate again to find first unique character

### Code:

```java
public static Character firstUnique(String s) {
    Map<Character, Integer> map = new LinkedHashMap<>();

    for (char c : s.toCharArray())
        map.put(c, map.getOrDefault(c, 0) + 1);

    for (char c : s.toCharArray())
        if (map.get(c) == 1)
            return c;

    return null;
}
```

### Test:

```java
System.out.println(firstUnique("swiss")); // w
```

---

# ✅ **8. What happens internally when you use HashMap put(key, value)?**

### Put sequence:

1. Compute `hash = hashCode(key)`
2. Convert to bucket index
3. If bucket is empty → insert
4. If key exists → replace value
5. If collision → add to linked list or tree
6. If bucket size > 8 → treeify to Red-Black tree
7. If size > threshold → resize & rehash

---

# ✅ **9. Write a custom resizable array (ArrayList implementation)**

### Minimal version:

```java
class MyArrayList<T> {
    private Object[] arr = new Object[10];
    private int size = 0;

    public void add(T value) {
        if (size == arr.length) grow();
        arr[size++] = value;
    }

    public T get(int index) {
        return (T) arr[index];
    }

    private void grow() {
        arr = Arrays.copyOf(arr, arr.length * 2);
    }

    public int size() {
        return size;
    }
}
```

---

# ✅ **10. Detect a cycle in a linked list (Floyd’s algorithm)**

### Floyd’s Slow–Fast pointer algorithm:

```java
public boolean hasCycle(ListNode head) {
    ListNode slow = head, fast = head;

    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;

        if (slow == fast) return true;
    }
    return false;
}
```

### Why it works?

* Fast pointer moves 2x speed
* If cycle exists, they will meet
* If no cycle, fast pointer reaches end

---

# ⭐ Complete Summary Table

| Question                       | Short Answer                                 |
| ------------------------------ | -------------------------------------------- |
| Prefer Set?                    | When uniqueness needed                       |
| Cache design                   | LinkedHashMap (LRU)                          |
| Handle concurrent modification | Concurrent collections                       |
| HashMap degrade?               | Poor hash, collisions, resize                |
| Custom collection              | Implement growable array                     |
| Comparator (salary→name)       | Comparator.comparing().thenComparing()       |
| First non-repeat char          | LinkedHashMap                                |
| HashMap put() internal         | hash → bucket → collision → treeify → resize |
| Resizable array                | grow() using copyOf                          |
| Detect cycle                   | Floyd algorithm                              |

---

