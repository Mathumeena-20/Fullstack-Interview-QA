## 1. Vehicle Interface with Car and Bike

### Code:

```java
interface Vehicle {
    void start();
    void stop();
}

class Car implements Vehicle {
    public void start() {
        System.out.println("Car started");
    }

    public void stop() {
        System.out.println("Car stopped");
    }
}

class Bike implements Vehicle {
    public void start() {
        System.out.println("Bike started");
    }

    public void stop() {
        System.out.println("Bike stopped");
    }
}
```

### Explanation:

* `Vehicle` defines a common contract.
* `Car` and `Bike` provide specific implementations.
* Demonstrates **abstraction + polymorphism**.

---

## 2. Abstract Class vs Interface

### Differences:

| Feature              | Abstract Class      | Interface                   |
| -------------------- | ------------------- | --------------------------- |
| Methods              | Abstract + Concrete | Abstract + default + static |
| Variables            | Instance & static   | Only `public static final`  |
| Multiple Inheritance | No                  | Yes                         |
| Constructors         | Yes                 | No                          |

### Example:

```java
// Abstract class
abstract class Shape {
    abstract double area();

    void display() {
        System.out.println("This is a shape");
    }
}

// Interface
interface Drawable {
    void draw();
}
```

---

## 3. Runtime Polymorphism (Method Overriding)

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();  // Upcasting
        a.sound();             // Calls Dog's sound() at runtime
    }
}
```

### Output:

```
Dog barks
```

✅ Method overriding decides behavior at **runtime**.

---

## 4. Library System Using OOP

```java
class Book {
    private String title;
    private boolean isIssued;

    public Book(String title) {
        this.title = title;
    }

    public void issueBook() {
        isIssued = true;
    }

    public void returnBook() {
        isIssued = false;
    }

    public String getTitle() {
        return title;
    }
}

class Member {
    private String name;

    public Member(String name) {
        this.name = name;
    }

    public void borrow(Book book) {
        book.issueBook();
        System.out.println(name + " borrowed " + book.getTitle());
    }
}

public class LibraryTest {
    public static void main(String[] args) {
        Book book = new Book("Java Programming");
        Member member = new Member("Mathu");

        member.borrow(book);
    }
}
```

✅ Uses: Encapsulation, Objects, Association, Abstraction.

---

## 5. Why is Composition Preferred Over Inheritance?

### Reason:

Composition gives more flexibility, avoids tight coupling, and follows **Has-A** relationship.

### Example:

```java
class Engine {
    public void start() {
        System.out.println("Engine started");
    }
}

class Car {
    private Engine engine = new Engine();   // Composition

    public void drive() {
        engine.start();
        System.out.println("Car is moving");
    }
}
```

✅ `Car` *has an* `Engine`, not *is an* `Engine`.

---

## 6. OOP in Payment System Design

```java
interface Payment {
    void pay(double amount);
}

class CreditCardPayment implements Payment {
    public void pay(double amount) {
        System.out.println("Paid via Credit Card: " + amount);
    }
}

class UPIPayment implements Payment {
    public void pay(double amount) {
        System.out.println("Paid via UPI: " + amount);
    }
}

class PaymentService {
    public void process(Payment payment, double amount) {
        payment.pay(amount);
    }
}
```

### OOP Used:

* Abstraction: `Payment` interface
* Polymorphism: Different implementations
* Encapsulation: Hides payment details
* Open-Closed principle

---

## 7. Polymorphism in Real Project

Example from a notification system:

```java
interface NotificationService {
    void send(String message);
}

class EmailNotification implements NotificationService {
    public void send(String message) {
        System.out.println("Email: " + message);
    }
}

class SmsNotification implements NotificationService {
    public void send(String message) {
        System.out.println("SMS: " + message);
    }
}
```

```java
public void notifyUser(NotificationService service) {
    service.send("Order Placed");
}
```

✅ Same method works with different objects.

---

## 8. When to Prefer Composition Over Inheritance

Use composition when:

* Relationship is **has-a**, not **is-a**
* You want loose coupling
* Behavior can change dynamically
* You want better testability and flexibility

Example: `Car HAS Engine`, not `Car IS Engine`.

---

## 9. How SOLID Principles Relate to OOP

| Principle | Meaning               |
| --------- | --------------------- |
| S         | Single Responsibility |
| O         | Open/Closed           |
| L         | Liskov Substitution   |
| I         | Interface Segregation |
| D         | Dependency Inversion  |

SOLID ensures:
✅ Clean OOP design
✅ Maintainable code
✅ Scalable architecture
✅ Low coupling & High cohesion

---

## 10. Multiple Inheritance in Java Using Interfaces

Java allows multiple inheritance through interfaces using `implements`.

```java
interface A {
    default void show() {
        System.out.println("From A");
    }
}

interface B {
    default void show() {
        System.out.println("From B");
    }
}

class C implements A, B {
    @Override
    public void show() {
        A.super.show();   // resolve conflict
    }
}
```

### Explanation:

* Java avoids diamond problem by forcing override.
* You must explicitly specify which default method to call.

---
