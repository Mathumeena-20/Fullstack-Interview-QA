Here are **topic-wise Java 8 Core Features interview questions** designed for a **2+ years experienced Java developer**.

---

## 1. Lambdas

1. What is a lambda expression in Java 8?
2. Why were lambdas introduced in Java?
3. How does a lambda expression differ from an anonymous inner class?
4. What is the syntax of a lambda expression?
5. Can lambda expressions access local variables? What are the restrictions?
6. What is variable capture?
7. Are lambda expressions objects in Java?
8. How are lambdas implemented internally by the JVM?
9. Can we throw checked exceptions inside lambdas?
10. Give a real project use-case of lambdas.

---

## 2. Functional Interfaces

1. What is a functional interface?
2. What is `@FunctionalInterface` annotation?
3. Can a functional interface have multiple methods?
4. Examples of built-in functional interfaces in Java 8:

   * `Predicate`
   * `Function`
   * `Consumer`
   * `Supplier`
5. Difference between `Function` and `Consumer`.
6. What are primitive functional interfaces like `IntPredicate`?
7. What are custom functional interfaces?
8. Why default methods don’t break functional interfaces?
9. How does method reference relate to functional interfaces?
10. Can you extend a functional interface?

---

## 3. Streams API

1. What is Stream in Java 8?
2. Difference between **Stream** and **Collection**.
3. What are intermediate and terminal operations?
4. What is lazy evaluation in Streams?
5. Difference between `map()` and `flatMap()`.
6. What is a parallel stream? When should you avoid it?
7. Explain `filter()`, `sorted()`, `limit()`, `distinct()`.
8. Difference between `forEach()` and `forEachOrdered()`.
9. What is collectors class?
10. Explain `groupingBy()`, `partitioningBy()`.
11. What is `reduce()` and how does it work?
12. How streams improve readability and performance?

---

## 4. Optional Class

1. What is `Optional`?
2. Why was Optional introduced?
3. Difference between `Optional.of()` and `Optional.ofNullable()`.
4. Difference between `orElse()` and `orElseGet()`.
5. When should you not use Optional?
6. Is Optional serializable?
7. Does Optional replace null checks everywhere?
8. Difference between `isPresent()` and `ifPresent()`.
9. Can Optional be used as method parameters or fields?
10. How does Optional help avoid `NullPointerException`?

---

## 5. Method References

1. What is a method reference?
2. Types of method references:

   * Static reference: `Class::method`
   * Instance reference: `object::method`
   * Constructor reference: `Class::new`
3. Difference between lambda expression and method reference.
4. When should you prefer method references?
5. Can method references replace all lambdas?
6. How does method reference bind arguments?
7. Give real-time use cases.
8. What happens if method signature doesn't match?
9. Can private methods be used in method references?
10. Method reference vs stream operations.

---

## 6. LocalDate and LocalDateTime

1. Difference between `LocalDate`, `LocalTime`, and `LocalDateTime`.
2. Difference between old Date API vs Java 8 Date-Time API.
3. How do you format `LocalDateTime`?
4. What is `Period` and `Duration`?
5. How to calculate difference between two LocalDate values?
6. How to get current date and time?
7. What is `ZonedDateTime`?
8. Difference between `Instant` and `LocalDateTime`.
9. Thread-safety of Java 8 Date-Time API.
10. Real-world use case of Java 8 Date-Time classes.

---

## 🔥 Bonus Scenario-Based Questions
1. Create an interface `Vehicle` with methods `start()` and `stop()`. Implement it with `Car` and `Bike`.
2. What is the difference between an abstract class and an interface? Give code examples.
3. Write a program showing runtime polymorphism using method overriding.
4. Model a Library system using OOP concepts.
5. Why is composition preferred over inheritance? Explain with a class example.
6. You are designing a payment system. How would you apply OOP principles?
7. Show how you implemented polymorphism in your current/previous project.
8. When would you prefer composition over inheritance?
9. How do SOLID principles relate to OOP?
10. How does Java handle multiple inheritance via interfaces?

---
