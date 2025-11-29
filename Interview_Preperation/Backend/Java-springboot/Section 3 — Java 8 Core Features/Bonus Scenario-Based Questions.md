# 1. How did Java 8 features improve your project code quality?

You can answer like this in interviews:

### ✔ Java 8 improved code in these ways:

1. **Reduced boilerplate code**

   * Lambdas replaced anonymous classes.
   * Streams replaced verbose loops.

2. **Improved readability**

   * Fluent stream pipelines made transformations clear.

3. **Better Null handling**

   * Optional helped avoid NullPointerException.

4. **More declarative programming**

   * Focus on *what* to do, not *how* to do.

5. **Better parallel processing**

   * Parallel streams improved processing of large datasets.

### Example:

Without Java 8:

```java
List<String> result = new ArrayList<>();
for (String s : list) {
    if (s.startsWith("A")) {
        result.add(s.toUpperCase());
    }
}
```

With Java 8:

```java
List<String> result =
    list.stream()
        .filter(s -> s.startsWith("A"))
        .map(String::toUpperCase)
        .toList();
```

✔ More readable
✔ Less error-prone

---

# 2. Rewrite a traditional loop using Streams & Lambdas

### Traditional loop:

```java
for (Integer n : list) {
    if (n % 2 == 0) {
        System.out.println(n);
    }
}
```

### Java 8 Stream version:

```java
list.stream()
    .filter(n -> n % 2 == 0)
    .forEach(System.out::println);
```

---

# 3. How to handle nulls using Optional in your project?

### Traditional null check:

```java
if (user != null && user.getEmail() != null) {
    sendEmail(user.getEmail());
}
```

### Optional way:

```java
Optional.ofNullable(user)
        .map(User::getEmail)
        .ifPresent(this::sendEmail);
```

✔ Avoids NullPointerException
✔ Cleaner and functional

---

# 4. When would you choose imperative vs functional style?

### Functional (Streams, Lambdas) WHEN:

✔ Easy transformation/filtering
✔ Data processing pipelines
✔ Parallel processing
✔ Readability improves
✔ Less mutation required

### Imperative (loops, if/else) WHEN:

✔ Complex logic
✔ Hard-to-read stream pipelines
✔ Performance sensitive small loops
✔ Break/continue required

### Answer example:

> “I choose functional style for data processing and transformations.
> I use imperative when logic is complex or readability gets worse with Streams.”

---

# 5. Group Employees by Department Using Streams

### Employee class:

```java
class Employee {
    int id;
    String name;
    String dept;

    // constructor + getters
}
```

### Group by department:

```java
Map<String, List<Employee>> result =
    employees.stream()
             .collect(Collectors.groupingBy(Employee::getDept));
```

---

# 6. Find the Second Highest Integer Using Streams

### Code:

```java
int secondHighest =
    list.stream()
        .sorted(Comparator.reverseOrder())
        .distinct()
        .skip(1)
        .findFirst()
        .orElseThrow();
```

Steps:

1. Sort descending
2. Remove duplicates
3. Skip first
4. Take next

---

# 7. Remove Duplicates from a List Using Streams

### Code:

```java
List<Integer> unique =
    list.stream()
        .distinct()
        .toList();
```

---

# 8. Convert List<Employee> into Map<id, Employee>

### Code:

```java
Map<Integer, Employee> map =
    employees.stream()
             .collect(Collectors.toMap(
                 Employee::getId,
                 e -> e
             ));
```

If duplicate keys may exist:

```java
.toMap(Employee::getId, e -> e, (e1, e2) -> e1)
```

---

# ⭐ Final Summary Table

| Requirement              | Java 8 Solution                   |
| ------------------------ | --------------------------------- |
| Improve code quality     | Lambdas, Streams, Optional        |
| Rewrite loop             | filter + forEach                  |
| Handle null              | Optional                          |
| Imperative vs functional | Based on readability & complexity |
| Group employees          | groupingBy()                      |
| Second highest           | sorted + skip                     |
| Remove duplicates        | distinct()                        |
| Convert list to map      | toMap()                           |

---
