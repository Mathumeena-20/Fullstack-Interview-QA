## 1️⃣ Difference between Primitive and Wrapper Classes

* **Primitive types** → Predefined, hold simple values, stored in stack (e.g., `int`, `char`, `boolean`).
* **Wrapper classes** → Object representations of primitives, stored in heap (e.g., `Integer`, `Character`, `Boolean`).

✅ Wrapper classes allow primitives to be used in **Collections** and support **null values**.

🔹 **Example:**

```java
int a = 10;              // primitive
Integer b = Integer.valueOf(10); // wrapper

System.out.println(a);   // 10
System.out.println(b);   // 10
```

---

## 2️⃣ What is String Pool in Java?

* Java maintains a **special memory area (String Pool) inside the Heap**.
* If you create a string using **literals**, JVM checks the pool first → avoids duplicate objects → saves memory.

🔹 **Example:**

```java
String s1 = "Hello";
String s2 = "Hello"; // same object from pool
String s3 = new String("Hello"); // new object in heap

System.out.println(s1 == s2); // true
System.out.println(s1 == s3); // false
```

---

## 3️⃣ Difference between String, StringBuilder, StringBuffer

| Feature       | String (Immutable)                    | StringBuilder (Mutable) | StringBuffer (Mutable + Thread-safe) |
| ------------- | ------------------------------------- | ----------------------- | ------------------------------------ |
| Mutability    | Immutable                             | Mutable                 | Mutable                              |
| Thread-safety | No                                    | No                      | Yes (synchronized)                   |
| Performance   | Slower (new object created on change) | Faster                  | Slower than StringBuilder            |

🔹 **Example:**

```java
String s = "Java";
s.concat("World"); // creates new string, doesn't change original
System.out.println(s); // Java

StringBuilder sb = new StringBuilder("Java");
sb.append("World");
System.out.println(sb); // JavaWorld
```

---

## 4️⃣ Why are Strings Immutable in Java?

* **Security** → prevents changing values (e.g., passwords, class names).
* **Caching** → String pool reuses strings safely.
* **Thread-safety** → Multiple threads can share strings without risk.

---

## 5️⃣ Difference between `final`, `finally`, and `finalize`

* **final** → keyword (for variables, methods, classes).

  * final variable → constant
  * final method → cannot override
  * final class → cannot extend
* **finally** → block in exception handling → executes always.
* **finalize()** → method called by GC before object is removed (not reliable, rarely used).

🔹 **Example:**

```java
final int x = 10; // final variable

try {
    System.out.println(10/0);
} catch(Exception e) {
    System.out.println("Error");
} finally {
    System.out.println("Always executed");
}

@Override
protected void finalize() {
    System.out.println("Object is garbage collected");
}
```

---

## 6️⃣ Pass by Value vs Pass by Reference in Java

* Java is **always pass by value** (copies of variables are passed).
* For **objects**, the value passed is the **reference** → so methods can modify the object’s content, but not reassign it.

🔹 **Example:**

```java
void modify(int x) { x = 20; }

void modifyObj(StringBuilder sb) { sb.append(" World"); }

public static void main(String[] args) {
    int a = 10;
    StringBuilder s = new StringBuilder("Hello");

    modify(a);
    System.out.println(a); // 10 (unchanged)

    modifyObj(s);
    System.out.println(s); // Hello World (changed)
}
```

---

## 7️⃣ Difference between Static and Instance Variables/Methods

* **Static** → Belongs to class, shared across all objects.
* **Instance** → Belongs to object, each object has its own copy.

🔹 **Example:**

```java
class Counter {
    static int staticCount = 0;  // shared
    int instanceCount = 0;       // per object

    Counter() {
        staticCount++;
        instanceCount++;
    }
}

public static void main(String[] args) {
    Counter c1 = new Counter();
    Counter c2 = new Counter();

    System.out.println(c1.staticCount);  // 2
    System.out.println(c1.instanceCount); // 1
}
```

---

## 8️⃣ What is Autoboxing and Unboxing?

* **Autoboxing** → Converting primitive → wrapper automatically.
* **Unboxing** → Converting wrapper → primitive automatically.

🔹 **Example:**

```java
int a = 10;
Integer b = a;  // autoboxing

Integer c = 20;
int d = c;      // unboxing
```

---

## 9️⃣ Difference between `==`, `.equals()`, and `hashCode()`

* **==** → Compares **references** (memory address).
* **.equals()** → Compares **values** (can be overridden).
* **hashCode()** → Returns integer hash value (used in collections like HashMap).

🔹 **Example:**

```java
String s1 = new String("Hello");
String s2 = new String("Hello");

System.out.println(s1 == s2);       // false
System.out.println(s1.equals(s2));  // true
System.out.println(s1.hashCode());  // same hash for equal strings
```

---

## 🔟 Explain Transient and Volatile Keywords

* **transient** → Used in serialization → field marked as transient is **not saved**.
* **volatile** → Ensures visibility of variable across threads (reads/writes go directly to main memory).

🔹 **Example (transient):**

```java
class Employee implements Serializable {
    String name;
    transient String password; // will not be serialized
}
```

🔹 **Example (volatile):**

```java
class SharedData {
    volatile boolean flag = true;
}
