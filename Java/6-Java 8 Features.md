## 1️⃣ Functional Interfaces

* **Definition** → An interface with exactly **one abstract method**.
* Can have **default** and **static methods** too.
* Used as target types for **Lambda expressions**.

🔹 Example:

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void greet(String name);
}

public class Test {
    public static void main(String[] args) {
        MyFunctionalInterface f = (n) -> System.out.println("Hello " + n);
        f.greet("Mathumeena"); // Hello Mathumeena
    }
}
```

👉 Interview tip: `Runnable`, `Callable`, `Comparator`, `Consumer`, `Supplier` are built-in functional interfaces.

---

## 2️⃣ Lambda Expressions

* **Definition** → Short-hand for implementing functional interfaces.
* Syntax: `(parameters) -> expression/body`.

🔹 Example:

```java
List<String> names = Arrays.asList("John", "Alice", "Bob");

// Without Lambda
Collections.sort(names, new Comparator<String>() {
    public int compare(String a, String b) {
        return a.compareTo(b);
    }
});

// With Lambda
Collections.sort(names, (a, b) -> a.compareTo(b));
System.out.println(names); // [Alice, Bob, John]
```

👉 Interview tip: Lambda improves readability, especially with **Streams API**.

---

## 3️⃣ Streams in Java 8

* **Definition** → Streams represent a sequence of elements supporting **functional-style operations** (map, filter, reduce).
* They are **not data structures**; they process collections efficiently.
* Two types: **Intermediate ops** (map, filter, sorted) and **Terminal ops** (collect, forEach, reduce).

🔹 Example:

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> squared = numbers.stream()
                               .map(n -> n * n)
                               .toList();
System.out.println(squared); // [1, 4, 9, 16, 25]
```

👉 Interview tip: Streams use **internal iteration** (not `for` loops).

---

## 4️⃣ Difference between map() and flatMap()

* **map()** → Transforms each element into **one result** (1-to-1 mapping).
* **flatMap()** → Transforms each element into a **stream of results**, then flattens (1-to-many mapping).

🔹 Example:

```java
List<String> words = Arrays.asList("Hello", "World");

// map → Stream of arrays
List<String[]> mapResult = words.stream()
                                .map(w -> w.split(""))
                                .toList();

// flatMap → Stream of characters
List<String> flatMapResult = words.stream()
                                  .flatMap(w -> Arrays.stream(w.split("")))
                                  .toList();

System.out.println(mapResult);     // [[H, e, l, l, o], [W, o, r, l, d]]
System.out.println(flatMapResult); // [H, e, l, l, o, W, o, r, l, d]
```

👉 Interview tip: **Use flatMap for nested lists or streams**.

---

## 5️⃣ Default and Static Methods in Interfaces

* **Default methods** → Provide method implementation inside interface.
* **Static methods** → Belong to interface, called using `InterfaceName.method()`.

🔹 Example:

```java
interface Vehicle {
    void drive();

    default void honk() {
        System.out.println("Beep beep!");
    }

    static void service() {
        System.out.println("Service checkup!");
    }
}

class Car implements Vehicle {
    public void drive() { System.out.println("Driving car..."); }
}

public class Test {
    public static void main(String[] args) {
        Car c = new Car();
        c.drive();    // Driving car...
        c.honk();     // Beep beep!
        Vehicle.service(); // Service checkup!
    }
}
```

👉 Interview tip: Default methods were introduced to avoid breaking old implementations when adding methods to interfaces.

---

## 6️⃣ Optional vs Null Checks

* **Problem**: NullPointerException is common in Java.
* **Solution**: `Optional<T>` is a container that may or may not hold a value.

🔹 Example:

```java
Optional<String> name = Optional.ofNullable(null);

// Traditional null check
if (name.isPresent()) {
    System.out.println(name.get());
} else {
    System.out.println("No value");
}

// Using orElse
System.out.println(name.orElse("Default Name")); // Default Name
```

👉 Interview tip: `Optional` promotes **functional style null-safety**.

---

## 7️⃣ Method References

* Short-hand for Lambda expressions that just call a method.
* Types:

  * **Static** → `ClassName::staticMethod`
  * **Instance** → `object::instanceMethod`
  * **Constructor** → `ClassName::new`

🔹 Example:

```java
import java.util.*;

public class Test {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("John", "Alice", "Bob");

        // Lambda
        names.forEach(n -> System.out.println(n));

        // Method reference
        names.forEach(System.out::println);
    }
}
```

👉 Interview tip: Method references make Lambdas more concise.

---

✅ **Quick Recap (Cheatsheet Style):**

| Feature              | Explanation                          | Example                   |
| -------------------- | ------------------------------------ | ------------------------- |
| Functional Interface | One abstract method                  | `Runnable`, `Callable`    |
| Lambda Expression    | `(args) -> body`                     | `(a,b) -> a+b`            |
| Streams              | Functional processing of collections | `filter`, `map`, `reduce` |
| map vs flatMap       | map = 1→1, flatMap = 1→many          | Splitting strings         |
| Default Method       | Method with body in interface        | `default void log()`      |
| Static Method in IF  | Belongs to interface                 | `Interface.method()`      |
| Optional             | Avoids `null`                        | `Optional.ofNullable()`   |
| Method Reference     | Shorthand for lambda                 | `System.out::println`     |
