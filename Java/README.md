## 🧩 1. **Core Java Basics**

* What is Java and what are its key features?
* Difference between JDK, JRE, and JVM.
* What is bytecode?
* How Java achieves platform independence?
* What are wrapper classes?
* What is autoboxing and unboxing?
* Difference between `==` and `.equals()`.
* What is the purpose of `static` keyword?
* Can we overload `main()` method?
* What are access modifiers?

---

## 🧱 2. **Class and Object**

* What is a class?
* What is an object?
* How to create objects in Java?
* What happens in memory when an object is created?
* Difference between class variable, instance variable, and local variable.
* What is the purpose of the `this` keyword?
* Can a class have multiple constructors?
* What is constructor chaining?
* What is object cloning and how is it implemented?
* Difference between shallow copy and deep copy.
* What is the role of `static` block and `instance` block?
* How does garbage collection work for objects?
* Can you create an object without `new` keyword?

---

## ⚙️ 3. **OOP Concepts**

* Explain the four pillars of OOP.
* Difference between abstraction and encapsulation.
* What is inheritance? Can you inherit multiple classes?
* What is polymorphism?
* Difference between method overloading and overriding.
* What is an abstract class and an interface?
* Difference between abstract class and interface (Java 8+).
* What are default and static methods in interfaces?
* What is the `super` keyword used for?
* Can we override a static method?

---

## 💥 4. **Exception Handling**

* Difference between checked and unchecked exceptions.
* Explain `try`, `catch`, `finally`, `throw`, and `throws`.
* Can we have multiple catch blocks?
* Can `finally` block be skipped?
* How to create custom exceptions?
* Difference between `Error` and `Exception`.
* How do you handle exceptions in layered architecture (Controller → Service → DAO)?

---

## 🧮 5. **Collections Framework**

* Difference between List, Set, and Map.
* Difference between `ArrayList` and `LinkedList`.
* How does a `HashMap` work internally?
* Difference between `HashMap` and `Hashtable`.
* What is the difference between `HashSet` and `TreeSet`?
* What is `ConcurrentHashMap`?
* What are fail-fast and fail-safe iterators?
* How to sort a custom object list using `Comparator` or `Comparable`?

---

## 🧵 6. **Multithreading & Concurrency**

* What is a thread in Java?
* How to create a thread (2 ways)?
* Difference between `start()` and `run()`.
* What is synchronization?
* What is a deadlock and how to prevent it?
* Difference between `wait()` and `sleep()`.
* What is `volatile` keyword?
* What is `ExecutorService` and thread pooling?
* Difference between `Runnable` and `Callable`.

---

## 💾 7. **Memory Management**

* Difference between heap and stack.
* What is garbage collection?
* What are strong, weak, and soft references?
* What is the use of `finalize()` method?
* What is memory leak in Java?
* Difference between `final`, `finally`, and `finalize()`.

---

## 🔤 8. **String Handling**

* Why are Strings immutable in Java?
* Difference between `String`, `StringBuilder`, and `StringBuffer`.
* What is String interning?
* How does String pool work?
* Compare strings using `==` and `.equals()`.
* How to reverse or check palindrome strings in Java?

---

## 🧩 9. **Java 8 Features**

* What are lambda expressions?
* What is a functional interface?
* Explain Stream API and its operations.
* Difference between `map()` and `flatMap()`.
* What is `Optional` class?
* What are method references?
* What are default and static methods in interfaces?
* How do you filter and collect data using Streams?

---

## 🌐 10. **JDBC**

* What is JDBC and its components?
* Steps to connect to a database using JDBC.
* What is `Statement` vs `PreparedStatement`?
* What is `executeQuery()` vs `executeUpdate()`?
* How to prevent SQL injection?
* What is connection pooling?

---

## 🧭 11. **Design Patterns**

* What are design patterns?
* Explain Singleton pattern.
* What is Factory pattern?
* Explain Builder pattern.
* What is Observer pattern?
* What is Dependency Injection?
* How is DI implemented in Spring?

---

## 🌍 12. **Spring Boot (Expanded Section 🚀)**

### 🔹 **Basics**

* What is Spring Boot and why is it used?
* Difference between Spring and Spring Boot.
* What is auto-configuration in Spring Boot?
* What is Spring Boot Starter?
* What is `application.properties` / `application.yml` used for?
* What is `@SpringBootApplication` annotation?

---

### 🔹 **Dependency Injection & Beans**

* What is dependency injection (DI)?
* Difference between `@Autowired` and `@Inject`.
* What is the difference between `@Component`, `@Service`, and `@Repository`?
* What is the role of `@Bean` annotation?
* Explain bean scopes in Spring (`singleton`, `prototype`, etc.).
* How are beans initialized and destroyed in Spring?

---

### 🔹 **REST API Development**

* What is `@RestController`?
* Difference between `@Controller` and `@RestController`.
* What is `@RequestMapping`, `@GetMapping`, `@PostMapping`, etc.?
* How do you handle request parameters and path variables?
* What is `ResponseEntity` and why is it used?
* How to send JSON data from a REST API?
* How to handle exceptions in REST controllers (`@ControllerAdvice`, `@ExceptionHandler`)?

---

### 🔹 **Spring Data JPA / Database Layer**

* What is Spring Data JPA?
* How do you configure a database connection in Spring Boot?
* What is the role of `Entity`, `Repository`, and `Service` layers?
* What is the difference between `CrudRepository`, `JpaRepository`, and `PagingAndSortingRepository`?
* How do you write custom JPQL queries?
* What is `@Query` annotation?
* How does lazy vs. eager loading work?
* What is the `EntityManager`?
* How do you perform transactions in Spring (`@Transactional`)?

---

### 🔹 **Security & Configuration**

* What is Spring Security?
* How to implement basic authentication in Spring Boot?
* What is JWT (JSON Web Token) and how is it used in Spring Security?
* How do you secure REST APIs?
* How to define roles and permissions?
* How to store secrets safely in Spring Boot?

---

### 🔹 **Spring Boot Architecture & Advanced**

* Explain the typical flow in a Spring Boot application (Controller → Service → Repository).
* What is the DispatcherServlet in Spring MVC?
* How does Spring Boot auto-configuration detect dependencies?
* What is Actuator in Spring Boot?
* What is the use of profiles in Spring Boot?
* How to handle cross-origin requests (CORS)?
* How to schedule tasks in Spring Boot (`@Scheduled`)?
* How to connect to an external API using `RestTemplate` or `WebClient`?
* How do you monitor and debug Spring Boot applications?

---

## 🧾 13. **Testing**

* What is JUnit and Mockito?
* Difference between unit test and integration test.
* What is the use of `@Test`, `@BeforeEach`, `@AfterEach`?
* How to mock dependencies in a Spring Boot test?
* How to test REST endpoints using `MockMvc`?
* What is Testcontainers?

---

## ⚡ 14. **Coding Practice**

* Reverse a string or integer.
* Check if a number is prime or palindrome.
* Find duplicate elements in an array.
* Find the second largest number in an array.
* Sort a list of custom objects.
* Count character frequency in a string.
* Use Stream API to filter even numbers and collect into a list.
* Implement Producer-Consumer problem using threads.

---
