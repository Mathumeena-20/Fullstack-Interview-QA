## 1. try / catch / finally

1. What is the purpose of `try`, `catch`, and `finally` blocks?
2. Can you have multiple `catch` blocks for a single `try`?
3. What happens if an exception is thrown but not caught?
4. Will `finally` always execute? Are there any exceptions?
5. What happens if an exception occurs in `finally` block?
6. Can we have a `try` block without a `catch`?
7. Can we nest try-catch blocks?
8. Difference between `throw` and `throws`.
9. What is exception propagation in Java?
10. What happens if both try and finally blocks return a value?

---

## 2. Custom Exceptions

1. How do you create a custom exception in Java?
2. Difference between extending `Exception` and `RuntimeException`.
3. When should you create a custom exception?
4. How do you pass custom messages to your exception?
5. Can custom exceptions be made serializable?
6. Can you override the `fillInStackTrace()`?
7. Best practices while creating custom exceptions.
8. What is exception chaining?
9. How do you handle custom exceptions in service layers?
10. Real project scenario where you used custom exception.

---

## 3. Checked vs Unchecked Exceptions

1. Difference between checked and unchecked exceptions.
2. Why did Java designers introduce checked exceptions?
3. Examples of checked and unchecked exceptions.
4. Why RuntimeException is unchecked?
5. Can we catch unchecked exceptions?
6. Does JVM force handling checked exceptions?
7. When should you use checked exception?
8. When should you prefer unchecked exception?
9. How exceptions affect transaction management?
10. How do microservices handle checked vs unchecked exceptions?

---

## 4. Try-With-Resources

1. What is try-with-resources in Java 7+?
2. How does it help in resource management?
3. Which interface must a class implement to be used in try-with-resources?
4. Can we use custom resources in try-with-resources?
5. How does it handle suppressed exceptions?
6. Can we use multiple resources in try-with-resources?
7. Difference between finally and try-with-resources?
8. What is AutoCloseable interface?
9. Order of closing resources in try-with-resources.
10. What happens if both close() and try block throws exceptions?

---

## 🔥 Advanced Scenario-Based Questions

1. Design a global exception handling mechanism for a REST API.
2. How do you manage exceptions in multi-threaded applications?
3. How do you create custom business exceptions?
4. How exceptions affect application performance?
5. Real-world debugging: Handling NullPointerException in production.
6. Create a custom exception InvalidAgeException.
7. Write a function that reads a file using try-with-resources.
8. Explain finally vs return in an example.
9. Demonstrate catching multiple exceptions in one block.
10. Convert a checked exception to unchecked (best practices).

---


