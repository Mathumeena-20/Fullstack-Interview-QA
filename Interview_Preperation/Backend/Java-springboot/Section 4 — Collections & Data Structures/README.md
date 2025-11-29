## 1. List, Set, Map

### List

1. Difference between `ArrayList` and `LinkedList`.
2. When would you prefer `Vector` over `ArrayList`?
3. How does `CopyOnWriteArrayList` work?
4. How does `ArrayList` grow dynamically?
5. Time complexity of `add()`, `remove()`, `get()` in `ArrayList`.

### Set

6. Difference between `HashSet`, `LinkedHashSet`, and `TreeSet`.
7. How does `HashSet` maintain uniqueness?
8. Can `null` be stored in a `Set`?
9. Difference between `TreeSet` and `HashSet`.
10. What is `NavigableSet`?

### Map

11. Difference between `HashMap`, `LinkedHashMap` and `TreeMap`.
12. Can `HashMap` have null key and null values?
13. Internal working of `HashMap` in Java 8.
14. What is load factor and threshold in HashMap?
15. Time complexity of `get()` and `put()` in HashMap.
16. How collisions are handled in HashMap?
17. Difference between `Hashtable` and `HashMap`.
18. Why is HashMap not thread-safe?
19. What is `WeakHashMap`?
20. When would you use `EnumMap`?

---

## 2. HashMap vs ConcurrentHashMap

1. Why is `HashMap` not thread-safe?
2. How does `ConcurrentHashMap` achieve thread safety?
3. Difference between segmentation locking (Java 7) and bucket-level locking (Java 8).
4. Can ConcurrentHashMap allow null keys and values?
5. Internal working of `ConcurrentHashMap` in Java 8.
6. Performance difference between `synchronizedMap()` and `ConcurrentHashMap`.
7. When should you use ConcurrentHashMap in real projects?
8. Can multiple threads update same bucket in ConcurrentHashMap?
9. Does ConcurrentHashMap block read operations?
10. Why ConcurrentHashMap is preferred in multi-threading environment?

---

## 3. Fail-fast vs Fail-safe

1. What is a fail-fast iterator?
2. What causes `ConcurrentModificationException`?
3. Why are ArrayList iterators fail-fast?
4. Example of fail-fast iteration.
5. What are fail-safe iterators?
6. Which collections provide fail-safe iterators?
7. Why ConcurrentHashMap iterators are fail-safe?
8. Can we modify a collection while iterating?
9. Difference between iterator and enumeration?
10. Internal mechanism of fail-fast.

---

## 4. Comparable vs Comparator

1. Difference between `Comparable` and `Comparator`.
2. When do you use Comparable?
3. When do you use Comparator?
4. Can a class have multiple Comparator implementations?
5. Why does `compareTo()` belong to `Comparable`?
6. Can we override compareTo?
7. How does sorting work using `Collections.sort()`?
8. What happens if compareTo() is inconsistent with equals()?
9. What is stable sorting?
10. How do you sort objects based on multiple fields?

---

## 🔥 Advanced Scenario-Based Questions

1. When would you prefer `Set` over `List` in a real application?
2. How would you design a cache using Map?
3. How do you handle concurrent modification in multithreading?
4. Why does HashMap performance degrade in some situations?
5. How would you design your own custom collection?
6. Implement your own Comparator<Employee> to sort by salary → name.
7. Given a list of strings, return the first non-repeating character.
8. What happens internally when you use HashMap put(key, value)?
9. Write a custom resizable array (ArrayList implementation).
10. Detect a cycle in a linked list (Floyd’s algorithm).
---


