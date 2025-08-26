
## 1️⃣ Four Pillars of OOP

**The four pillars are:**

1. **Encapsulation** → Wrapping data (fields) and methods into a single unit (class).
2. **Abstraction** → Hiding implementation details and showing only the functionality.
3. **Inheritance** → Acquiring properties and behaviors of a parent class.
4. **Polymorphism** → The ability of an object to take many forms (method overriding/overloading).

🔹 **Example:**

```java
// Encapsulation
class Account {
    private double balance; // hidden data
    public void deposit(double amount) { balance += amount; }
    public double getBalance() { return balance; }
}

// Inheritance
class SavingsAccount extends Account {
    private double interestRate = 5.0;
    public double getInterestRate() { return interestRate; }
}

// Polymorphism (Overriding)
class LoanAccount extends Account {
    @Override
    public void deposit(double amount) {
        System.out.println("Loan repayment of: " + amount);
        super.deposit(amount);
    }
}

// Abstraction
abstract class Bank {
    abstract void provideLoan();
}
```

---

## 2️⃣ Difference between Class and Object

* **Class** → Blueprint/template (defines properties & behavior).
* **Object** → Instance of a class (real-world entity created from class).

🔹 **Example:**

```java
class Car {
    String brand;
    void drive() { System.out.println("Car is driving..."); }
}

public class Main {
    public static void main(String[] args) {
        Car car1 = new Car(); // Object
        car1.brand = "Tesla";
        car1.drive();
    }
}
```

---

## 3️⃣ Difference between Abstract Class and Interface

| Feature     | Abstract Class                               | Interface                                                                 |
| ----------- | -------------------------------------------- | ------------------------------------------------------------------------- |
| Inheritance | Can extend one abstract class                | Can implement multiple interfaces                                         |
| Methods     | Can have abstract + concrete methods         | (Before Java 8) only abstract methods. (Java 8+) default & static allowed |
| Fields      | Can have variables with any access modifier  | Only public static final constants                                        |
| Use         | "Is-a" relationship with partial abstraction | Contract/specification for classes                                        |

🔹 **Example:**

```java
abstract class Shape {  // Abstract Class
    abstract void draw();
    void color() { System.out.println("Default color: Red"); }
}

interface Drawable {    // Interface
    void draw();
}
```

---

## 4️⃣ Can an Interface have Default and Static Methods? (Java 8)

👉 Yes! From **Java 8**, interfaces can have **default methods** (with body) and **static methods**.

🔹 **Example:**

```java
interface Vehicle {
    default void start() {
        System.out.println("Vehicle is starting...");
    }
    static void stop() {
        System.out.println("Vehicle stopped.");
    }
}

class Car implements Vehicle {}

public class Main {
    public static void main(String[] args) {
        Car car = new Car();
        car.start();        // default method
        Vehicle.stop();     // static method
    }
}
```

---

## 5️⃣ Method Overloading vs Method Overriding

| Feature         | Overloading                                | Overriding                               |
| --------------- | ------------------------------------------ | ---------------------------------------- |
| Definition      | Same method name, different parameter list | Same method name & signature in subclass |
| Compile/Runtime | Compile-time polymorphism                  | Runtime polymorphism                     |
| Access          | Within the same class                      | Between superclass & subclass            |
| Return type     | Can be different                           | Must be same (or covariant)              |

🔹 **Example:**

```java
class MathUtils {
    int add(int a, int b) { return a + b; }          // Overloading
    double add(double a, double b) { return a + b; }
}

class Animal {
    void sound() { System.out.println("Animal sound"); }
}
class Dog extends Animal {
    @Override
    void sound() { System.out.println("Bark"); }     // Overriding
}
```

---

## 6️⃣ What is Polymorphism in Java?

👉 **Polymorphism = “many forms”**

* **Compile-time polymorphism** → Method overloading
* **Runtime polymorphism** → Method overriding

🔹 **Example:**

```java
class Animal {
    void sound() { System.out.println("Animal makes sound"); }
}
class Dog extends Animal {
    @Override
    void sound() { System.out.println("Dog barks"); }
}
class Cat extends Animal {
    @Override
    void sound() { System.out.println("Cat meows"); }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();  // Polymorphism
        a.sound();  // Dog barks
    }
}
```

---

## 7️⃣ What is Encapsulation and Why Important?

👉 **Encapsulation = Data hiding + Data security**.
We make fields **private** and expose them through **getters/setters**.

🔹 **Example:**

```java
class Employee {
    private String name; // hidden
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}
```

✅ Importance: Improves **security, maintainability, flexibility**.

---

## 8️⃣ Difference between `this` and `super` keywords

* **this** → Refers to current class object
* **super** → Refers to immediate parent class object

🔹 **Example:**

```java
class Parent {
    int value = 10;
}
class Child extends Parent {
    int value = 20;
    void showValues() {
        System.out.println(this.value);  // 20
        System.out.println(super.value); // 10
    }
}
```

---

## 9️⃣ Difference between `==` and `.equals()` in Java

* `==` → Compares **references (memory addresses)**
* `.equals()` → Compares **values** (can be overridden in classes like String)

🔹 **Example:**

```java
String s1 = new String("Hello");
String s2 = new String("Hello");

System.out.println(s1 == s2);       // false (different objects)
System.out.println(s1.equals(s2));  // true (value is same)
```

---

## 🔟 What is a Constructor? Types of Constructors?

* **Constructor** → Special method invoked when an object is created.
* **Types:**

  1. **Default constructor** (no args, compiler provides if not written)
  2. **Parameterized constructor** (takes arguments)
  3. **Copy constructor** (copy another object’s values)

🔹 **Example:**

```java
class Student {
    String name;
    int age;

    Student() {   // default
        System.out.println("Default constructor called");
    }

    Student(String name, int age) {  // parameterized
        this.name = name;
        this.age = age;
    }

    Student(Student s) {   // copy
        this.name = s.name;
        this.age = s.age;
    }
}
```

---

## 1️⃣1️⃣ Can We Make a Class Immutable in Java? How?

👉 Yes. Rules for immutability:

1. Make class **final** (so cannot be extended).
2. Make fields **private and final**.
3. No setter methods.
4. Initialize values via **constructor**.
5. Return deep copies for mutable objects.

🔹 **Example:**

```java
final class Employee {
    private final String name;
    private final int age;

    public Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() { return name; }
    public int getAge() { return age; }
}
