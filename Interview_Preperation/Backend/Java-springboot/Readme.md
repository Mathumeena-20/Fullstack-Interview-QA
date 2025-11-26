**Section 1 — Java Fundamentals (Core Java)**

## 🔹 1. JVM, JRE, JDK

1. What is the difference between **JVM, JRE, and JDK**?
2. Explain the **architecture of JVM** (Class Loader, Runtime Data Area, Execution Engine).
3. What are the steps involved in **Java program execution**?
4. What is a **ClassLoader**? Types of ClassLoaders?
5. What is **bytecode** and why is Java platform-independent?
6. What is the difference between **HotSpot JVM and other JVMs**?
7. What are **JIT and Just-In-Time compilation**?
8. What is **Metaspace** and how is it different from PermGen?
9. How does JVM handle memory allocation?
10. What happens when you run `javac` and `java` commands?

---

## 🔹 2. Data Types

1. What are **primitive** and **non-primitive** data types in Java?
2. Difference between `int` and `Integer`?
3. Why is `char` 2 bytes in Java?
4. Explain **type casting** – implicit vs explicit.
5. What is **autoboxing and unboxing**?
6. What is default value of all primitive data types?
7. How is `boolean` stored internally?
8. Can we store large integers using primitive data types? Alternatives?
9. Why is Java not a fully object-oriented language?
10. What is wrapper class and its importance?

---

## 🔹 3. Loops, Conditions & Control Statements

1. Difference between `for`, `while`, and `do-while` loops?
2. When would you prefer `do-while` over `while`?
3. What is an **enhanced for loop**? Limitations?
4. How does `break` differ from `continue`?
5. What is a **labeled break**?
6. Can we use conditions inside a switch?
7. From Java 7+, what changes happened in switch?
8. Can we use String in switch? How does JVM process it?
9. What is fall-through in switch case?
10. How does `if-else` differ from ternary operator?

---

## 🔹 4. Static vs Instance

1. What does the `static` keyword mean?
2. When is a static block executed?
3. Difference between **static variables and instance variables**?
4. Can we access a non-static variable inside a static method?
5. Can a class be static?
6. Why is `main()` method static?
7. What happens when both static and instance blocks are present?
8. Static method vs instance method?
9. Can static methods be overridden?
10. Where are static variables stored in JVM?

---

## 🔹 5. Constructors & Method Overloading

1. What is a constructor?
2. Difference between constructor and method?
3. Types of constructors?
4. What happens if you don’t define a constructor?
5. Can constructors be overloaded?
6. Can constructors be overridden?
7. What is constructor chaining?
8. What is `this()` and `super()`?
9. What are rules of method overloading?
10. Can we overload main() method?

---

## 🔹 6. Packages

1. What is a package in Java?
2. Difference between **package and module** (Java 9+)?
3. Why are packages used?
4. Difference between public, default and protected access modifiers?
5. What is classpath?
6. Can a package have sub-packages?
7. Difference between `import` and `static import`?
8. How does JVM locate a class using package name?
9. Can a class belong to multiple packages?
10. How to create a custom package?

---

## ✅ Bonus: Expected Coding Questions (2+ Years Level)

1. Reverse a number without using built-in method.
2. Check if a string is palindrome.
3. Count frequency of characters in a string.
4. Find largest and smallest number in an array.
5. Swap two numbers without using third variable.
6. Check if a number is prime (optimize for large numbers).
7. Write a custom MathUtils class with overloaded methods add(int,int) and add(double,double).
8. Explain JVM memory areas (with examples).
9. What happens when static variables are used across multiple classes?
---

**Section 2 — OOP (Object-Oriented Programming)

Here are **topic-wise OOP interview questions** tailored for a **2+ years experienced developer**. These focus on both concepts and practical usage you might face in real projects.

---

## 1. Encapsulation

1. What is encapsulation and why is it important in object-oriented programming?
2. How do you achieve encapsulation in Java?
3. Difference between `public`, `private`, `protected` and default access modifiers.
4. Why should class variables be private?
5. What is data hiding? How is it different from encapsulation?
6. Can we achieve encapsulation without getters and setters?
7. Give a real-world example where you used encapsulation in your project.
8. How does encapsulation improve security and maintainability?
9. What happens if all class variables are public?
10. Can you override private methods?

---

## 2. Inheritance

1. What is inheritance? Why do we use it?
2. Types of inheritance supported in Java?
3. Why does Java not support multiple inheritance with classes?
4. Difference between `extends` and `implements`.
5. What is the use of `super` keyword?
6. What is constructor chaining?
7. What is method overriding? What rules must be followed?
8. Difference between method overloading and overriding.
9. What happens if parent and child have same variable name?
10. Can a child class reduce visibility of an overridden method?

---

## 3. Polymorphism (Compile-time vs Runtime)

### Compile-time Polymorphism (Overloading)

1. What is method overloading?
2. Can we overload a method by changing only the return type?
3. Can constructors be overloaded?
4. Difference between overloading and overriding.
5. How does Java decide which overloaded method to call?

### Runtime Polymorphism (Overriding)

6. What is runtime polymorphism?
7. How does Java implement runtime polymorphism internally?
8. Can static methods be overridden?
9. Why is method overriding not possible with private methods?
10. What is dynamic method dispatch?

---

## 4. Abstraction

1. What is abstraction? How is it different from encapsulation?
2. Why do we need abstraction in real projects?
3. How is abstraction implemented in Java?
4. What is an abstract class?
5. Can an abstract class have a constructor?
6. Can an abstract class have non-abstract methods?
7. Why can’t we create an object of an abstract class?
8. When would you choose abstract class over interface?
9. Give an example of abstraction from your project.
10. What are real-world use cases of abstraction?

---

## 5. Interfaces & Abstract Classes

### Interfaces

1. What is an interface in Java?
2. Difference between abstract class and interface.
3. Can an interface have a constructor?
4. What are default and static methods in interfaces (Java 8+)?
5. What are functional interfaces?
6. What is marker interface? Give examples.
7. Can we implement multiple interfaces? How?
8. Can an interface extend another interface?
9. What happens if two interfaces have same default method?
10. Can we define variables in an interface?

### Abstract Classes

11. Difference between abstract method and concrete method.
12. Can abstract class implement an interface?
13. Can abstract class be final?
14. Can an abstract class have static methods?
15. Can abstract methods be private?

---

## Bonus Advanced Scenario-Based Questions

1. You are designing a payment system. How would you apply OOP principles?
2. Show how you implemented polymorphism in your current/previous project.
3. When would you prefer composition over inheritance?
4. How do SOLID principles relate to OOP?
5. How does Java handle multiple inheritance via interfaces?
6. Create an interface Vehicle with methods start() and stop(). Implement it with Car and Bike.
7. What is the difference between abstract class vs interface? Give code examples.
8. Write a program showing runtime polymorphism using method overriding.
9. Model a Library system using OOP concepts.
10. Why is composition preferred over inheritance? Explain with a class example.

---

Section **3 — Java 8 Core Features**

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

1. How did Java 8 features improve your project code quality?
2. Rewrite a traditional loop using Streams and lambdas.
3. How to handle nulls using Optional in your project?
4. When would you choose imperative vs functional style?
5. Write a program to group employees by department using streams.
6. Given a list of integers, find the second highest using Java 8 Streams.
7. Remove duplicates from a list using Streams.
8. Convert a list of employees into a map <id, employee> using Streams.
9. Use Optional to avoid null checks when fetching customer address.


---

**Section 4 — Collections & Data Structures**

Here are **topic-wise interview questions for Section 4 — Collections & Data Structures** tailored for a **2+ years experienced Java developer**.

---

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

---

**Section 5 — Multithreading & Concurrency**

Here are **topic-wise interview questions** for
**Section 5 — Multithreading & Concurrency**
suitable for **2+ years experienced Java developers**.

I’ve grouped them clearly by each topic 👇

---

## 1. Thread Lifecycle

1. What are the different states of a thread in Java?
2. Explain the transitions between NEW → RUNNABLE → BLOCKED → WAITING → TIMED_WAITING → TERMINATED.
3. Difference between `WAITING` and `BLOCKED` state.
4. What happens internally when `Thread.start()` is called?
5. Difference between `Thread.sleep()` and `Object.wait()`.
6. What does `Thread.join()` do?
7. What is a daemon thread?
8. Can a thread be restarted after it reaches TERMINATED state?
9. What causes a thread to enter BLOCKED state?
10. What is thread starvation and how does it happen?

---

## 2. Runnable vs Thread

1. Difference between `Runnable` and `Thread`.
2. Why is implementing `Runnable` preferred over extending `Thread`?
3. What happens if you call `run()` instead of `start()`?
4. Is `Runnable` a functional interface?
5. Can a lambda expression be used with Runnable? Provide example.
6. Can two threads share the same Runnable instance?
7. How do you return a result from a Runnable?
8. Why does Java not support multiple inheritance with Thread class?
9. Real-world use cases where Runnable is more suitable.
10. How does Thread internally call the run() method?

---

## 3. ExecutorService

1. What is `ExecutorService`?
2. Difference between `Executor` and `ExecutorService`.
3. How does thread pool improve application performance?
4. Difference between `submit()` and `execute()`.
5. Explain different thread pools:

   * `FixedThreadPool`
   * `CachedThreadPool`
   * `SingleThreadExecutor`
   * `ScheduledThreadPool`
6. Difference between `shutdown()` and `shutdownNow()`.
7. What is `ThreadPoolExecutor`?
8. What happens if task queue is full?
9. How do you create a custom thread pool?
10. What is a RejectedExecutionHandler?

---

## 4. Future & Callable

1. Difference between `Callable` and `Runnable`.
2. What is `Future`?
3. How do you retrieve result from a Future?
4. What is blocking call?
5. Difference between `Future.get()` and `Future.get(long timeout)`.
6. How do you cancel a running task?
7. Difference between `invokeAll()` and `invokeAny()`.
8. What is a `CompletionService`?
9. Can you return multiple values from a Callable?
10. How do you handle exceptions from Future?

---

## 5. volatile vs synchronized

1. What does the `volatile` keyword do?
2. Difference between `volatile` and `synchronized`.
3. Does volatile guarantee thread safety? Why or why not?
4. Explain memory visibility problem.
5. What is the happens-before relationship?
6. Why doesn’t volatile guarantee atomicity?
7. Can volatile variables be used without synchronization?
8. Where would you use volatile in real projects?
9. What is double-checked locking?
10. Can we use volatile and synchronized together?

---

## 6. Locks & Semaphores

1. Difference between synchronized and Lock interface.
2. What is `ReentrantLock`?
3. What are fair locks and unfair locks?
4. What is `tryLock()`?
5. What is ReadWriteLock?
6. What is Semaphore and how does it work?
7. Difference between semaphore and mutex.
8. Real-world use cases of semaphores.
9. How does Lock handle thread interruption?
10. Difference between ReentrantLock and synchronized block?

---

## 7. Concurrent Collections

1. What are concurrent collections in Java?
2. Difference between `HashMap` and `ConcurrentHashMap`.
3. How does `ConcurrentHashMap` achieve thread safety?
4. Difference between `synchronizedMap()` and `ConcurrentHashMap`.
5. What is `CopyOnWriteArrayList`?
6. Difference between `CopyOnWriteArrayList` and `Collections.synchronizedList()`.
7. What is BlockingQueue?
8. Types of `BlockingQueue` you have used.
9. What is ConcurrentSkipListMap?
10. When should you use concurrent collections in your project?

---

## 8. CompletableFuture

1. What is `CompletableFuture`?
2. Difference between `Future` and `CompletableFuture`.
3. What is asynchronous programming?
4. Difference between `runAsync()` and `supplyAsync()`.
5. Difference between `thenApply()`, `thenAccept()`, and `thenRun()`.
6. Difference between `thenCompose()` and `thenCombine()`.
7. How do you handle exceptions in CompletableFuture?
8. What’s the difference between `handle()` and `exceptionally()`?
9. What are `allOf()` and `anyOf()`?
10. How is thread pool chosen for CompletableFuture tasks?

---

## 🔥 Bonus Real Project-Based Questions

1. How did you avoid deadlocks in your project?
2. How do you handle high concurrency in your application?
3. Implement a rate limiter using Semaphore.
4. How do you handle async API calls in microservices?
5. Design a thread-safe Singleton.
6. Create 10 threads that print numbers sequentially (use synchronization).
7. Implement producer–consumer using wait/notify.
8. Submit 5 tasks to a thread pool and wait for all to finish.
9. Use CompletableFuture to call 3 APIs in parallel and merge results.
10. Explain thread-safety of ConcurrentHashMap internally.

---
**Section 6 — Java Memory Model**

Here are **topic-wise interview questions** on
**Heap, Stack, Garbage Collection, References, Escape Analysis and JIT** for a **2+ years experienced Java developer**.

---

## 1. Heap vs Stack

1. Difference between Heap memory and Stack memory?
2. What kind of data is stored in Stack vs Heap?
3. Why is Stack memory faster than Heap?
4. What is stack overflow and heap overflow?
5. How does JVM manage Stack memory per thread?
6. Where are instance variables stored?
7. Where are local variables and method calls stored?
8. How does memory allocation happen in Stack vs Heap?
9. What is the lifetime of objects stored in heap?
10. How does Stack memory help in thread safety?

---

## 2. Garbage Collection (Minor GC & Major GC)

1. What is Garbage Collection in Java?
2. Difference between Minor GC and Major GC?
3. What is Young Generation and Old Generation?
4. What is Eden, Survivor S0 and S1 spaces?
5. What is Stop-The-World event?
6. How objects move from young gen to old gen?
7. What is GC root?
8. How does JVM identify garbage objects?
9. What is Full GC and when does it happen?
10. Types of GC algorithms (Serial, Parallel, CMS, G1, ZGC – basics).

---

## 3. WeakReference & SoftReference

1. What are Strong, Soft, Weak and Phantom references?
2. Difference between SoftReference and WeakReference?
3. When should you use WeakReference?
4. When should you use SoftReference?
5. How are these references used in caching?
6. Does WeakReference prevent GC?
7. What happens to SoftReference during low memory?
8. What is ReferenceQueue?
9. What is PhantomReference used for?
10. Real-world example of WeakReference.

---

## 4. Escape Analysis

1. What is escape analysis in JVM?
2. What is object escape?
3. Stack allocation vs Heap allocation.
4. How does escape analysis improve performance?
5. What are the types of escape?

   * No escape
   * Method escape
   * Thread escape
6. How does escape analysis reduce GC pressure?
7. What is lock elimination?
8. What is scalar replacement?
9. Can you disable escape analysis?
10. How escape analysis helps in multi-threading optimization?

---

## 5. Just-In-Time (JIT) Compiler

1. What is JIT compiler?
2. Difference between JIT and Interpreter.
3. How does JIT improve performance?
4. What is HotSpot JVM?
5. What is bytecode?
6. What is method inlining?
7. What is tiered compilation?
8. What is dynamic compilation?
9. Difference between C1 and C2 compiler.
10. What is profiling in JIT?

---

## 🔥 Advanced Scenario-Based Questions

1. How does JVM manage memory during high load?
2. How do you analyze GC performance issues?
3. How to tune GC parameters in production?
4. How escape analysis helps reduce synchronization overhead?
5. Real-time scenario: Application memory leak debugging steps.
6. What is GC tuning? When is it needed?
7. Difference between stack memory & heap memory?
8. Write a program that causes OutOfMemory error and fix it.
9. Explain how Objects are stored in heap with diagrams.
10. What is the role of volatile in the Java Memory Model?

---

**Section 7 — Exception Handling**

Here are **topic-wise interview questions** for Java **Exception Handling** concepts, specifically curated for a **2+ years experienced Java developer**.

---

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
**Section 8 — File Handling (I/O & NIO)**

## 1. Files API (java.nio.file)

1. What is the Java NIO Files API?
2. Difference between `Files` and `File` class.
3. How do you read a file using `Files.readAllLines()`?
4. Difference between `Paths.get()` and `File`?
5. How do you write data to a file using `Files` class?
6. What is `Path` interface?
7. How do you check if a file exists using NIO?
8. How to copy, move and delete files using `Files` API?
9. How do you get file attributes using Files?
10. Explain `StandardOpenOption` with examples.
11. Difference between blocking IO and non-blocking IO.
12. How do you create temporary files and directories?
13. What is atomic file operation?
14. How do you read large files efficiently using `Files`?
15. Real-time use case where you preferred NIO Files over traditional IO.

---

## 2. Directory Stream

1. What is `DirectoryStream` in Java?
2. Difference between `DirectoryStream` and `File.listFiles()`?
3. How is DirectoryStream more memory efficient?
4. What is `DirectoryStream.Filter`?
5. How do you filter files using DirectoryStream?
6. Can DirectoryStream handle very large directories?
7. What is the use of `Files.newDirectoryStream()`?
8. Difference between `DirectoryStream` and `Stream<Path>`?
9. How does lazy loading work in DirectoryStream?
10. What happens if the directory content changes during iteration?
11. How do you manage exceptions while using DirectoryStream?
12. Is DirectoryStream thread-safe?
13. How do you close DirectoryStream resources?
14. How to scan directories recursively?
15. Where did you use DirectoryStream in a real project?

---

## 3. Buffers & Channels (Java NIO)

1. What are Buffers and Channels in Java NIO?
2. Difference between InputStream/OutputStream and Channels?
3. Difference between blocking IO and non-blocking IO.
4. Types of buffers in Java (ByteBuffer, CharBuffer, etc.)?
5. Difference between HeapBuffer and DirectBuffer.
6. What are the main properties of Buffer? (`capacity`, `limit`, `position`, `mark`)
7. What is a Channel?
8. Types of channels in Java NIO.
9. Difference between `ReadableByteChannel` and `WritableByteChannel`.
10. What is Selector in Java NIO?
11. How does Java NIO support multiplexing?
12. What is zero-copy in Java NIO?
13. Explain FileChannel vs SocketChannel.
14. How does non-blocking IO improve performance in servers?
15. Real-world use of NIO in high-performance applications.

---

## 4. Serialization

1. What is serialization in Java?
2. Difference between serialization and deserialization.
3. Why is serialization needed?
4. What is `Serializable` interface?
5. Difference between Serializable and Externalizable.
6. What is `serialVersionUID`?
7. What happens if `serialVersionUID` is not defined?
8. Role of `transient` keyword in serialization.
9. Can static variables be serialized?
10. How to customize serialization using `writeObject()` and `readObject()`?
11. What is deep vs shallow copy in serialization?
12. What is object graph?
13. How do you prevent sensitive data from being serialized?
14. What are common serialization issues?
15. Real-world example where you used serialization (ex: caching, session replication).

---

## 🔥 Scenario-Based Questions

1. How do you read and process large log files efficiently?
2. How would you design a file upload/download feature using NIO?
3. How do you serialize objects safely in a microservices environment?
4. What are the performance differences between IO and NIO?
5. How do you prevent serialization vulnerabilities?
6. Read a large CSV file and count distinct values efficiently.
7. Serialize a Student object and deserialize it back.
8. Use NIO to copy a file faster than I/O streams.
9. Monitor a folder for new files (WatchService).
10. List all files larger than 100 MB.

---


**Section 9 — Build Tools & Libraries**

Here are **topic-wise interview questions** for
**Maven, Gradle, Lombok, and Logging (Logback / Log4j2)**
designed for a **2+ years experienced Java developer**.

---

## 1. Maven

1. What is Maven and why do we use it?
2. Explain the Maven build lifecycle.
3. What are the different phases in Maven? (`validate`, `compile`, `test`, `package`, `install`, `deploy`)
4. What is a `pom.xml`?
5. Difference between `dependencies` and `dependencyManagement`.
6. What is a transitive dependency?
7. Explain Maven scopes (`compile`, `test`, `runtime`, `provided`, `system`).
8. How does Maven resolve dependency conflicts?
9. What is a BOM (Bill of Materials)?
10. What are Maven plugins?
11. Difference between `clean` and `install`.
12. Difference between `install` and `deploy`.
13. What is a multi-module Maven project?
14. What are parent POMs?
15. How do you skip tests in Maven build?

---

## 2. Gradle

1. Difference between Maven and Gradle.
2. What is Gradle and why is it faster than Maven?
3. Explain Gradle build lifecycle.
4. What is `build.gradle`?
5. Difference between Groovy DSL and Kotlin DSL.
6. How do dependencies work in Gradle?
7. What is Gradle Wrapper?
8. Difference between `implementation` and `api` configuration.
9. How does Gradle support incremental builds?
10. What is Gradle task?
11. How do you create a custom task in Gradle?
12. What is multi-project build in Gradle?
13. How do you skip tests in Gradle?
14. What is a plugin in Gradle?
15. How does Gradle handle dependency version conflicts?

---

## 3. Lombok

1. What is Lombok and why do we use it?
2. How does Lombok reduce boilerplate code?
3. What is annotation processing?
4. Common Lombok annotations you used:

   * `@Getter`
   * `@Setter`
   * `@Data`
   * `@Builder`
   * `@AllArgsConstructor`
   * `@NoArgsConstructor`
5. Difference between `@Data` and `@Value`.
6. Difference between `@Builder` and `@SuperBuilder`.
7. How Lombok integrates with IDE?
8. Common problems with Lombok.
9. How to debug Lombok generated code?
10. Why some companies avoid Lombok?

---

## 4. Logging (Logback / Log4j2)

1. Difference between Logback and Log4j2.
2. What is SLF4J and why is it needed?
3. Logging levels and their usages.
4. How do you configure Logback?
5. How do you configure Log4j2?
6. File appenders vs console appenders.
7. What is async logging?
8. What is MDC (Mapped Diagnostic Context)?
9. How to log in multi-threaded applications?
10. What is log rolling policy?
11. How do you manage logging in Spring Boot?
12. Difference between synchronous and asynchronous logging.
13. How do you avoid logging sensitive data?
14. How to debug logging configuration issues?
15. How do you enable different log levels for different packages?

---

## 🔥 Scenario-Based Questions

1. How did you optimize your Maven or Gradle build?
2. How do you handle dependency conflicts in real project?
3. How do you enforce logging standards in your team?
4. What issues you faced with Lombok in real projects?
5. How do you troubleshoot a production logging issue?
6. Convert a Maven project to Gradle.
7. Write a Lombok-based POJO using @Builder.
8. Configure Logback with rolling logs.
9. Write your own custom Maven plugin explanation.
10. Demonstrate Multi-module Maven project.
---

**Section 10 — Spring Boot (Mandatory for Backend Interviews)**

Here are **topic-wise Spring Boot interview questions** for a **2+ years experienced Java developer** on the topics you mentioned.

---

## 1. REST Controllers

1. Difference between `@Controller` and `@RestController`.
2. What does `@RequestBody` do?
3. Difference between `@GetMapping`, `@PostMapping`, `@PutMapping`, and `@DeleteMapping`.
4. How do you handle path variables and request parameters?
5. Difference between `@PathVariable` and `@RequestParam`.
6. How does Spring Boot convert JSON to Java objects?
7. How do you return different HTTP status codes?
8. What is `ResponseEntity` and why is it used?
9. Difference between REST and SOAP.
10. How do you version REST APIs?

---

## 2. Dependency Injection

1. What is Dependency Injection?
2. Difference between field injection, constructor injection and setter injection.
3. Why is constructor injection recommended?
4. What is `@Autowired` and how does it work?
5. Difference between `@Component`, `@Service`, `@Repository`, `@Bean`.
6. What are Spring beans?
7. Bean lifecycle in Spring.
8. What is `@Lazy`?
9. What is circular dependency and how to resolve it?
10. How does Spring manage singleton beans?

---

## 3. Spring Data JPA

1. What is Spring Data JPA?
2. Difference between JPA and Hibernate.
3. What is an Entity?
4. What is a Repository?
5. Difference between `CrudRepository` and `JpaRepository`.
6. What is `@Transactional`?
7. What is LAZY and EAGER loading?
8. What is JPQL?
9. What is paging and sorting?
10. What are projections?
11. What is N+1 problem?
12. How do you solve N+1 issues?
13. Difference between native query and JPQL.
14. What is dirty checking?
15. How do you define composite primary key?

---

## 4. Validation

1. What is Bean Validation (JSR 380)?
2. Difference between `@Valid` and `@Validated`.
3. Common validation annotations (`@NotNull`, `@Email`, `@Size`).
4. How do you create custom validators?
5. What is validation groups?
6. Where does the validation happen in Spring?
7. How to validate path variables and request parameters?
8. How do you return custom validation messages?
9. Difference between server-side and client-side validation.
10. What happens if validation fails?

---

## 5. Filters & Interceptors

### Filters

1. What is a Servlet Filter?
2. How do you create a custom filter in Spring Boot?
3. Difference between Filter and Interceptor.
4. Use case of filters in real projects.
5. When does a filter get executed?

### Interceptors

6. What is a Spring Interceptor?
7. How do you implement `HandlerInterceptor`?
8. Difference between `preHandle()`, `postHandle()`, `afterCompletion()`.
9. Real-time scenario where you used interceptor.
10. How do you register multiple interceptors?

---

## 6. Global Exception Handling

1. What is `@ControllerAdvice`?
2. Difference between `@ExceptionHandler` and global handler.
3. How do you return custom error response?
4. How do you handle validation errors globally?
5. Difference between checked and unchecked exception handling in Spring.
6. How do you return HTTP status codes using exceptions?
7. How do you log exceptions globally?
8. Can you have multiple ControllerAdvice?
9. Best practices for exception handling in REST APIs.
10. Example of production-level exception handling.

---

## 7. Scheduling

1. What is Spring Scheduler?
2. What is `@EnableScheduling`?
3. What is `@Scheduled`?
4. Difference between fixedRate and fixedDelay.
5. What is cron expression?
6. Can we run scheduled jobs in cluster environment?
7. How do you avoid overlapping jobs?
8. How do you stop scheduled jobs?
9. What happens if a scheduled method throws exception?
10. Real-world example of scheduling tasks.

---

## 8. OpenFeign / RestTemplate

### RestTemplate

1. What is RestTemplate?
2. Difference between RestTemplate and WebClient.
3. How do you configure timeout in RestTemplate?
4. How to handle errors in RestTemplate?

### OpenFeign

5. What is OpenFeign?
6. How does Feign work internally?
7. How do you enable Feign client in Spring Boot?
8. How do you add headers to Feign request?
9. How do you configure Feign timeout?
10. Feign vs RestTemplate vs WebClient.

---

## 🔥 Real-Time Scenario Questions

1. How do you design microservices communication?
2. How do you handle retries and fallbacks in Feign?
3. How do you secure REST APIs?
4. How do you manage distributed transactions?
5. How do you handle exception logging across services?
6. Build a CRUD API for Employee using Spring Boot + JPA.
7. Create a global exception handler using @ControllerAdvice.
8. Implement a scheduled task that runs every hour.
9. Write a custom interceptor to log incoming requests.
10. Build an API that calls another API using OpenFeign.
---

**Section 11 — Database + JPA/Hibernate**

Here are **topic-wise Spring Data JPA / Hibernate interview questions** for a
**2+ years experienced developer** on the topics you mentioned.

---

## 1. Entity Mapping

1. What is an Entity in JPA?
2. What is the purpose of `@Entity` and `@Table` annotations?
3. Difference between `@Id`, `@GeneratedValue`, and generation strategies.
4. What is `@Column` and when do you customize it?
5. Difference between `@OneToOne`, `@OneToMany`, `@ManyToOne`, and `@ManyToMany`.
6. What is owning side and inverse side in relationships?
7. Difference between `@JoinColumn` and `@JoinColumns`.
8. What is cascade type? Explain different cascade options.
9. What is `orphanRemoval` and how does it work?
10. What is the difference between unidirectional and bidirectional mapping?
11. How do you map composite primary keys?
12. Difference between `@EmbeddedId` and `@IdClass`.
13. How do you map a join table?
14. What is the use of `@MappedSuperclass`?
15. Difference between `@Inheritance` strategies (SINGLE_TABLE, JOINED, TABLE_PER_CLASS).
16. What is entity life cycle?
17. What problems did you face while mapping entities in real projects?

---

## 2. Lazy vs Eager Loading

1. What is Lazy loading in JPA?
2. What is Eager loading?
3. Default fetch strategies of:

   * `@ManyToOne`
   * `@OneToMany`
4. Difference between LazyInitializationException and Eager behavior.
5. What is `FetchType.LAZY` and `FetchType.EAGER`?
6. Real project scenario where Lazy loading caused an issue.
7. How do you fix LazyInitializationException?
8. Difference between join fetch and default fetch.
9. How does Hibernate proxy work in lazy loading?
10. Can you change fetch type at query level without changing annotation?
11. Why is EAGER fetching dangerous in production?
12. When would you intentionally use EAGER fetching?
13. Difference between `@EntityGraph` and fetch join.
14. What is bytecode enhancement in relation to lazy loading?
15. Best practices for Lazy loading in REST APIs.

---

## 3. N+1 Problem

1. What is the N+1 query problem?
2. Give a real-world example of N+1 problem.
3. How does N+1 degrade application performance?
4. How do you identify N+1 issue?
5. How to solve N+1 problem using `JOIN FETCH`?
6. How `@EntityGraph` helps solve N+1?
7. Difference between fetch join and normal join.
8. How to prevent N+1 in Spring Data JPA repositories?
9. What tools have you used to detect N+1 problem?
10. What is subselect fetching in Hibernate?
11. Difference between batch fetching and join fetching.
12. What is Hibernate `@BatchSize`?
13. How pagination behaves with fetch join?
14. Can caching solve N+1 problem?
15. Real-world case where you optimized N+1 problem.

---

## 4. Criteria API

1. What is Criteria API?
2. Difference between Criteria API and JPQL.
3. What are advantages of Criteria API?
4. When do you prefer Criteria API over JPQL?
5. What is `CriteriaBuilder`?
6. What is `CriteriaQuery`?
7. What is `Root` in Criteria API?
8. How do you perform dynamic queries using Criteria API?
9. How do you add predicates dynamically?
10. How do you handle joins in Criteria API?
11. How do you implement pagination using Criteria API?
12. How do you use Criteria API for complex filtering?
13. What is `Specification` in Spring Data JPA?
14. Difference between Criteria API and QueryDSL.
15. How did you use Criteria/Specification in your project?

---

## 🔥 Real Project Scenario Questions

1. How did you optimize performance in large entity relationships?
2. How did you solve Lazy loading issues in REST APIs?
3. How to design entities for microservices?
4. How to avoid infinite recursion while returning entities in JSON?
5. How do you manage bidirectional relationships safely?
6. Map OneToMany: Department → Employees.
7. Write a JPQL query to fetch all employees hired in the last 1 year.
8. Solve N+1 problem using join fetch.
9. Implement pagination & sorting using JPA.
10. Write a custom repository method using Criteria API.
---

**Section 12 — System Design + Patterns**

Here are **topic-wise interview questions** on
**Design Patterns, Dependency Injection, Caching, and REST API Architecture**
tailored for a **2+ years experienced developer**.

---

## 1. Singleton Pattern

1. What is the Singleton design pattern? Why is it used?
2. Different ways to implement Singleton in Java.
3. How do you make a thread-safe Singleton?
4. Difference between eager and lazy initialization.
5. Why is double-checked locking used?
6. How can reflection break Singleton? How do you prevent it?
7. Does Singleton break with serialization? How to fix it?
8. How does enum-based Singleton work?
9. When should you avoid Singleton?
10. Real project scenario where you used Singleton.

---

## 2. Factory Pattern

1. What is the Factory design pattern?
2. Difference between Factory and Abstract Factory.
3. What problem does Factory pattern solve?
4. How do you implement Factory pattern in Java?
5. Difference between Factory and Builder pattern.
6. When would you use Factory pattern in a real project?
7. Example of Factory used in Spring framework.
8. How Factory improves scalability?
9. Draw UML design of Factory pattern.
10. How do you test code that uses Factory pattern?

---

## 3. Builder Pattern

1. What is the Builder pattern?
2. Difference between Builder and Constructor pattern.
3. When should you use Builder instead of setter?
4. How does Builder help with immutability?
5. What problem does Builder solve with complex objects?
6. How is Lombok’s `@Builder` different from manual Builder?
7. Builder vs Factory pattern.
8. Example of Builder used in real project.
9. What is step Builder pattern?
10. Draw UML for Builder pattern.

---

## 4. Observer Pattern

1. What is the Observer pattern?
2. Difference between Observer and Pub-Sub pattern.
3. How is Observer implemented in Java?
4. Real-world example of Observer pattern.
5. Where does Spring use Observer pattern?
6. What is the advantage of loose coupling in Observer?
7. How do you avoid memory leaks in Observer?
8. Difference between pull and push model.
9. How do you implement custom Observer pattern?
10. Write a use case for Observer pattern in microservices.

---

## 5. Strategy Pattern

1. What is the Strategy pattern?
2. How does Strategy pattern help in avoiding if-else?
3. Difference between Strategy and Factory.
4. Real-world example of Strategy pattern.
5. How do you combine Strategy with Dependency Injection?
6. How does Spring apply Strategy pattern?
7. Advantages and disadvantages of Strategy pattern.
8. Example of selecting different algorithms using Strategy.
9. How do you make strategies extensible?
10. Compare Strategy vs Template Method.

---

## 6. Dependency Injection (Design Pattern Concept)

1. What is Dependency Injection?
2. Why is DI important in design patterns?
3. Difference between Constructor injection and Setter injection.
4. How does DI improve testability?
5. What is Inversion of Control?
6. Difference between tightly coupled and loosely coupled code.
7. How does Spring implement DI internally?
8. How does DI relate to Singleton and Factory patterns?
9. What are the disadvantages of DI?
10. DI real-world use cases.

---

## 7. Caching

1. What is caching and why is it used?
2. Types of caching (In-memory vs distributed).
3. Difference between Redis cache and in-memory cache.
4. What are cache eviction strategies? (LRU, LFU, FIFO)
5. What is cache invalidation?
6. Write-through vs write-back cache.
7. How does Spring Cache work?
8. What is cache stampede problem?
9. How do you handle stale data in cache?
10. How do you design a caching layer in microservices?

---

## 8. REST API Architecture

1. What is REST and RESTful architecture?
2. Difference between REST and SOAP.
3. Explain statelessness in REST.
4. What are REST constraints?
5. What is idempotency?
6. Difference between PUT vs PATCH.
7. How do you design versioning in REST APIs?
8. How do you handle pagination and filtering?
9. Best practices for REST API error handling.
10. How do you design scalable REST APIs?
11. What is HATEOAS?
12. How do you secure REST APIs?
13. What is rate limiting?
14. How do you handle backward compatibility?
15. How do you design REST API for microservices?

---

## 🔥 Scenario-Based Design Questions

1. Design a payment processing system using design patterns.
2. Design a notification system using Observer pattern.
3. Implement strategy pattern for different tax calculation rules.
4. Design a caching system for product catalog.
5. Design a REST API for an e-commerce platform.
6. Design a Rate Limiter (token bucket) in Java.
7. Implement an in-memory cache with TTL.
8. Build a mini event-driven system using Observer pattern.
9. Implement a thread-safe Singleton (4 ways).
10. Design a URL shortener backend using Java.
---

