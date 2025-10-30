# 🎯 **1️⃣ What are Design Patterns?**

**Definition:**
Design patterns are **proven reusable solutions** to common software design problems.
They help developers write **flexible, maintainable, and scalable** code.

### ✅ Categories:

| Type           | Example Patterns            |
| -------------- | --------------------------- |
| **Creational** | Singleton, Factory, Builder |
| **Structural** | Adapter, Decorator, Proxy   |
| **Behavioral** | Observer, Strategy, Command |

---

# 🧩 **2️⃣ Singleton Pattern**

**Definition:**
Ensures **only one instance** of a class exists and provides a global access point to it.

**Use Case:**

* Database connection pool
* Logging class
* Configuration manager

---

### 🔹 Example:

```java
public class DatabaseConnection {
    // Step 1: Create a private static instance
    private static DatabaseConnection instance;

    // Step 2: Make constructor private to prevent direct instantiation
    private DatabaseConnection() {
        System.out.println("Database Connected!");
    }

    // Step 3: Provide global access method
    public static synchronized DatabaseConnection getInstance() {
        if (instance == null) {
            instance = new DatabaseConnection();
        }
        return instance;
    }
}
```

**Usage:**

```java
public class Main {
    public static void main(String[] args) {
        DatabaseConnection conn1 = DatabaseConnection.getInstance();
        DatabaseConnection conn2 = DatabaseConnection.getInstance();
        System.out.println(conn1 == conn2); // true
    }
}
```

✅ **Explanation:**

* Only one object of `DatabaseConnection` is created.
* `synchronized` ensures **thread safety**.

---

# 🏭 **3️⃣ Factory Pattern**

**Definition:**
Factory Pattern provides a **way to create objects** without exposing the creation logic to the client.
The client uses a **common interface** and the Factory decides which subclass to instantiate.

**Use Case:**

* When object creation logic is complex or depends on conditions (e.g., Shape Factory, Payment Factory).

---

### 🔹 Example:

```java
interface Shape {
    void draw();
}

class Circle implements Shape {
    public void draw() { System.out.println("Drawing Circle"); }
}

class Square implements Shape {
    public void draw() { System.out.println("Drawing Square"); }
}

class ShapeFactory {
    public static Shape getShape(String type) {
        if (type.equalsIgnoreCase("CIRCLE")) return new Circle();
        else if (type.equalsIgnoreCase("SQUARE")) return new Square();
        return null;
    }
}

public class Main {
    public static void main(String[] args) {
        Shape shape1 = ShapeFactory.getShape("CIRCLE");
        shape1.draw();

        Shape shape2 = ShapeFactory.getShape("SQUARE");
        shape2.draw();
    }
}
```

✅ **Explanation:**

* The client doesn’t directly create objects (`new Circle()`), it calls `ShapeFactory`.
* Makes code easier to extend — just add new shapes, no changes in main logic.

---

# 🧱 **4️⃣ Builder Pattern**

**Definition:**
Used to **construct complex objects step-by-step** without directly calling the constructor.

**Use Case:**

* Creating objects with **many optional parameters** (e.g., Employee, Car, HTTP Request).

---

### 🔹 Example:

```java
class User {
    private String name;
    private int age;
    private String email;

    // Private constructor
    private User(UserBuilder builder) {
        this.name = builder.name;
        this.age = builder.age;
        this.email = builder.email;
    }

    public static class UserBuilder {
        private String name;
        private int age;
        private String email;

        public UserBuilder setName(String name) {
            this.name = name;
            return this;
        }

        public UserBuilder setAge(int age) {
            this.age = age;
            return this;
        }

        public UserBuilder setEmail(String email) {
            this.email = email;
            return this;
        }

        public User build() {
            return new User(this);
        }
    }

    @Override
    public String toString() {
        return name + " (" + age + "), " + email;
    }
}

public class Main {
    public static void main(String[] args) {
        User user = new User.UserBuilder()
                        .setName("Mathu")
                        .setAge(25)
                        .setEmail("mathu@example.com")
                        .build();

        System.out.println(user);
    }
}
```

✅ **Explanation:**

* Each setter returns the Builder itself → allows **method chaining**.
* Prevents telescoping constructors (many overloaded constructors).
* Commonly used in frameworks like **Lombok (`@Builder`)** and **Spring Beans**.

---

# 👁 **5️⃣ Observer Pattern**

**Definition:**
Defines a **one-to-many dependency** between objects.
When one object (subject) changes state, all its dependents (observers) are notified.

**Use Case:**

* Event-driven systems (e.g., notifications, listeners, stock price updates).
* Java’s `java.util.Observer` or reactive programming (RxJava, Spring Events).

---

### 🔹 Example:

```java
import java.util.ArrayList;
import java.util.List;

// Subject (Publisher)
class Channel {
    private List<Subscriber> subscribers = new ArrayList<>();

    public void subscribe(Subscriber sub) {
        subscribers.add(sub);
    }

    public void notifySubscribers(String message) {
        for (Subscriber sub : subscribers) {
            sub.update(message);
        }
    }
}

// Observer
interface Subscriber {
    void update(String message);
}

class User implements Subscriber {
    private String name;

    User(String name) { this.name = name; }

    public void update(String message) {
        System.out.println(name + " received update: " + message);
    }
}

// Main
public class Main {
    public static void main(String[] args) {
        Channel channel = new Channel();
        User u1 = new User("Alice");
        User u2 = new User("Bob");

        channel.subscribe(u1);
        channel.subscribe(u2);

        channel.notifySubscribers("New video uploaded!");
    }
}
```

✅ **Explanation:**

* `Channel` → Subject (publishes events)
* `Subscriber` → Observers (react to events)
* Useful for event systems, pub-sub models, GUI listeners, etc.

---

# 💉 **6️⃣ What is Dependency Injection (DI)?**

**Definition:**
A design pattern where **dependencies are provided (injected)** by an external system (Spring), not created inside the class.

**Problem Without DI:**

```java
class Car {
    Engine engine = new Engine(); // tightly coupled
}
```

**With DI:**

```java
@Component
class Engine {}

@Component
class Car {
    private final Engine engine;

    @Autowired
    Car(Engine engine) { // injected by Spring
        this.engine = engine;
    }
}
```

✅ **Explanation:**

* Makes code **loosely coupled** and **testable**.
* Spring’s **IoC container** manages object creation and wiring automatically.

---

# 🧠 **7️⃣ How is DI implemented in Spring?**

Spring provides DI in 3 ways:

| Type                      | Example                          |
| ------------------------- | -------------------------------- |
| **Constructor Injection** | Preferred – ensures immutability |
| **Setter Injection**      | Optional dependencies            |
| **Field Injection**       | Simple but less testable         |

---

### 🔹 Example (Constructor Injection)

```java
@Service
class CarService {
    private final Engine engine;

    @Autowired
    public CarService(Engine engine) {
        this.engine = engine;
    }

    public void start() {
        engine.run();
    }
}

@Component
class Engine {
    public void run() {
        System.out.println("Engine started...");
    }
}
```

**Spring Container:**

* Scans `@Component` classes
* Creates Beans (`CarService`, `Engine`)
* Injects `Engine` into `CarService` automatically

---

✅ **Summary Table**

| Pattern              | Type       | Use Case                    | Key Concept                           |
| -------------------- | ---------- | --------------------------- | ------------------------------------- |
| Singleton            | Creational | One instance                | Private constructor + static instance |
| Factory              | Creational | Centralized object creation | Polymorphism                          |
| Builder              | Creational | Complex object creation     | Step-by-step build                    |
| Observer             | Behavioral | Event notification          | Subject–Observer relationship         |
| Dependency Injection | Structural | Loose coupling              | Inversion of Control (IoC)            |

