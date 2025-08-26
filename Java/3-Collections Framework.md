## 1️⃣ Difference between List, Set, and Map

| Feature    | List                      | Set                                       | Map                               |
| ---------- | ------------------------- | ----------------------------------------- | --------------------------------- |
| Order      | Ordered (insertion order) | Unordered (except LinkedHashSet, TreeSet) | Key-value pairs                   |
| Duplicates | Allowed                   | Not allowed                               | Keys unique, values can duplicate |
| Access     | By index                  | By element                                | By key                            |
| Examples   | ArrayList, LinkedList     | HashSet, LinkedHashSet, TreeSet           | HashMap, TreeMap, LinkedHashMap   |

🔹 Example:

```java
List<Integer> list = new ArrayList<>();   // allows duplicates
list.add(1); list.add(1);

Set<Integer> set = new HashSet<>();       // removes duplicates
set.add(1); set.add(1);

Map<Integer, String> map = new HashMap<>();
map.put(1, "A"); map.put(1, "B");  // replaces value
```

---

## 2️⃣ Difference between ArrayList and LinkedList

| Feature       | ArrayList              | LinkedList             |
| ------------- | ---------------------- | ---------------------- |
| Storage       | Dynamic array          | Doubly linked list     |
| Access        | Fast (O(1))            | Slow (O(n))            |
| Insert/Delete | Slow (shifting needed) | Fast (no shifting)     |
| Best Use      | Frequent access        | Frequent insert/delete |

🔹 Example:

```java
ArrayList<Integer> arr = new ArrayList<>();
arr.add(10); // fast access

LinkedList<Integer> list = new LinkedList<>();
list.addFirst(20); // efficient insertion
```

---

## 3️⃣ Difference between HashSet, LinkedHashSet, and TreeSet

| Feature     | HashSet       | LinkedHashSet             | TreeSet                     |
| ----------- | ------------- | ------------------------- | --------------------------- |
| Order       | No order      | Maintains insertion order | Sorted (natural/comparator) |
| Null        | Allows 1 null | Allows 1 null             | No null                     |
| Performance | Fastest       | Slightly slower           | Slowest                     |

🔹 Example:

```java
Set<String> hs = new HashSet<>();
hs.add("B"); hs.add("A"); // random order

Set<String> lhs = new LinkedHashSet<>();
lhs.add("B"); lhs.add("A"); // preserves insertion order

Set<String> ts = new TreeSet<>();
ts.add("B"); ts.add("A"); // sorted order
```

---

## 4️⃣ Difference between HashMap, LinkedHashMap, and TreeMap

| Feature     | HashMap                      | LinkedHashMap   | TreeMap                           |
| ----------- | ---------------------------- | --------------- | --------------------------------- |
| Order       | No order                     | Insertion order | Sorted by keys                    |
| Null        | 1 null key, many null values | Same            | No null key, multiple null values |
| Performance | Fastest                      | Slightly slower | Slower                            |

🔹 Example:

```java
Map<Integer,String> hm = new HashMap<>();
hm.put(2,"B"); hm.put(1,"A"); // random order

Map<Integer,String> lhm = new LinkedHashMap<>();
lhm.put(2,"B"); lhm.put(1,"A"); // insertion order

Map<Integer,String> tm = new TreeMap<>();
tm.put(2,"B"); tm.put(1,"A"); // sorted by key
```

---

## 5️⃣ Difference between HashMap and Hashtable

| Feature     | HashMap                      | Hashtable                    |
| ----------- | ---------------------------- | ---------------------------- |
| Thread-safe | No                           | Yes (synchronized)           |
| Null        | 1 null key, many null values | No null keys, no null values |
| Performance | Faster                       | Slower                       |
| Introduced  | Java 1.2                     | Java 1.0 (legacy)            |

---

## 6️⃣ How does HashMap work internally?

* HashMap stores **key-value pairs** in **buckets** (array of Node objects).
* When we call `put(key, value)`:

  1. `hashCode()` → generates hash.
  2. Index calculated = `(n - 1) & hash`.
  3. If bucket empty → create new node.
  4. If bucket already has key → replace value.
  5. If collision (same bucket) → forms **Linked List** or **Tree (Red-Black Tree from Java 8)**.
* **Load Factor (default 0.75)** → when map is 75% full, it resizes (rehash).

🔹 Example:

```java
Map<String,Integer> map = new HashMap<>();
map.put("A",1); // hash computed → bucket assigned
map.put("B",2);
```

---

## 7️⃣ What is ConcurrentHashMap? How is it different from HashMap?

* **ConcurrentHashMap** → Thread-safe, introduced in Java 1.5.
* Uses **segments / buckets locking** (not whole map).
* Allows concurrent read + write operations.
* Unlike `Hashtable`, it does not block entire map, only parts of it → better performance.
* **Nulls** → Does NOT allow `null` key or value.

🔹 Example:

```java
ConcurrentHashMap<Integer,String> chm = new ConcurrentHashMap<>();
chm.put(1, "A");
```

---

## 8️⃣ Difference between Iterator and ListIterator

| Feature     | Iterator                  | ListIterator           |
| ----------- | ------------------------- | ---------------------- |
| Direction   | Forward only              | Forward + Backward     |
| Collections | Works for all collections | Works only for List    |
| Modify      | Remove() only             | Add(), remove(), set() |
| Index       | No                        | Yes                    |

🔹 Example:

```java
List<String> list = new ArrayList<>();
list.add("A"); list.add("B");

Iterator<String> it = list.iterator();
while(it.hasNext()) System.out.println(it.next());

ListIterator<String> lit = list.listIterator();
while(lit.hasNext()) System.out.println(lit.next());
while(lit.hasPrevious()) System.out.println(lit.previous());
```

---

## 9️⃣ Fail-fast vs Fail-safe Iterator

* **Fail-fast** → Throws `ConcurrentModificationException` if collection is modified while iterating. (e.g., `ArrayList`, `HashMap`).
* **Fail-safe** → Works on a **copy of collection**, no exception. (e.g., `ConcurrentHashMap`, `CopyOnWriteArrayList`).

🔹 Example (fail-fast):

```java
List<String> list = new ArrayList<>();
list.add("A"); list.add("B");

for(String s : list) {
    list.add("C"); // throws ConcurrentModificationException
}
```

---

## 🔟 Difference between Comparable and Comparator

| Feature | Comparable              | Comparator               |
| ------- | ----------------------- | ------------------------ |
| Package | java.lang               | java.util                |
| Method  | compareTo(obj)          | compare(obj1, obj2)      |
| Sorting | Natural order           | Custom order             |
| Use     | Single sorting sequence | Multiple sorting options |

🔹 Example:

```java
class Student implements Comparable<Student> {
    int age;
    Student(int age) { this.age = age; }
    public int compareTo(Student s) { return this.age - s.age; } // natural order
}

// Comparator Example
Comparator<Student> ageDesc = (s1, s2) -> s2.age - s1.age;
