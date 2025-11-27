Here are **clear explanations with examples** for each of your Java Data Types questions (2+ years interview level).

---

## 1. What are primitive and non-primitive data types in Java?

### 🔹 Primitive Data Types

These store **simple values directly** in memory.

| Type    | Size          | Example                |
| ------- | ------------- | ---------------------- |
| byte    | 1 byte        | `byte b = 10;`         |
| short   | 2 bytes       | `short s = 100;`       |
| int     | 4 bytes       | `int n = 1000;`        |
| long    | 8 bytes       | `long l = 999999L;`    |
| float   | 4 bytes       | `float f = 10.5f;`     |
| double  | 8 bytes       | `double d = 99.99;`    |
| char    | 2 bytes       | `char c = 'A';`        |
| boolean | JVM-dependent | `boolean flag = true;` |

---

### 🔹 Non-Primitive Data Types

These store **references (memory address)** to objects.

Examples:
`String`, `Arrays`, `Classes`, `Interfaces`, `Enum`, `Objects`

```java
String name = "Java";
int[] numbers = {1, 2, 3};
```

---

## 2. Difference between `int` and `Integer`

| Feature              | int       | Integer       |
| -------------------- | --------- | ------------- |
| Type                 | Primitive | Wrapper Class |
| Object?              | No        | Yes           |
| Null allowed?        | ❌ No      | ✅ Yes         |
| Stored in            | Stack     | Heap          |
| Used in collections? | ❌ No      | ✅ Yes         |

### Example:

```java
int a = 10;
Integer b = 20;  // Object
```

⚠️ `Integer` can be null:

```java
Integer x = null; // Valid
int y = null; // Compile error
```

---

## 3. Why is `char` 2 bytes in Java?

Java supports **Unicode**, not ASCII.
Since Unicode characters take 2 bytes, Java uses **16-bit char (2 bytes)**.

Example:

```java
char c = 'म';  // Indian character
System.out.println(c);
```

This works only because Java supports Unicode.

---

## 4. Explain Type Casting – Implicit vs Explicit

### 🔹 Implicit Casting (Widening)

Small → Bigger type
Automatically done by JVM.

```java
int a = 10;
double b = a;  // Implicit casting
System.out.println(b); // 10.0
```

---

### 🔹 Explicit Casting (Narrowing)

Bigger → Smaller type
Programmer must force conversion.

```java
double x = 10.5;
int y = (int) x;
System.out.println(y);  // 10
```

---

## 5. What is Autoboxing and Unboxing?

### Autoboxing → Primitive → Object

```java
int a = 5;
Integer obj = a;   // Autoboxing
```

### Unboxing → Object → Primitive

```java
Integer obj = 10;
int b = obj;       // Unboxing
```

Used heavily with Collections.

---

## 6. Default Values of Primitive Types

| Data Type | Default Value        |
| --------- | -------------------- |
| byte      | 0                    |
| short     | 0                    |
| int       | 0                    |
| long      | 0L                   |
| float     | 0.0f                 |
| double    | 0.0                  |
| char      | '\u0000' (null char) |
| boolean   | false                |

Example:

```java
class Test {
    int a;
    boolean flag;

    public static void main(String[] args) {
        Test t = new Test();
        System.out.println(t.a);     // 0
        System.out.println(t.flag);  // false
    }
}
```

---

## 7. How is boolean stored internally?

JVM does not strictly define boolean size.
Usually it's stored as:

* 1 byte
* Sometimes as a bit (depends on JVM implementation)

Example:

```java
boolean flag = true;
```

Internally stored as:

* 1 → true
* 0 → false

---

## 8. Can we store large integers using primitive types? Alternatives?

Maximum size of `long`:

```
9,223,372,036,854,775,807
```

If number > this → Use `BigInteger`

Example:

```java
import java.math.BigInteger;

BigInteger big = new BigInteger("999999999999999999999999");
System.out.println(big.multiply(new BigInteger("2")));
```

✅ Handles unlimited size.

---

## 9. Why Java is not fully object-oriented?

Because Java supports **primitive data types** like `int`, `char`, `boolean` which are **not objects**.

In a fully object-oriented language, everything must be an object.

---

## 10. What is a Wrapper Class and its Importance?

A wrapper class converts primitive types into objects.

| Primitive | Wrapper   |
| --------- | --------- |
| int       | Integer   |
| char      | Character |
| double    | Double    |
| boolean   | Boolean   |

### Importance:

✅ Required for Collections
✅ Supports object operations
✅ Enables autoboxing/unboxing
✅ Can hold null values

Example:

```java
List<Integer> list = new ArrayList<>();
list.add(10);  // Autoboxing happens
```

---

## ✅ Quick Summary Table

| Concept         | Key Point                              |
| --------------- | -------------------------------------- |
| Primitive       | Stores value directly                  |
| Non-Primitive   | Stores reference                       |
| Autoboxing      | Primitive → Wrapper                    |
| Unboxing        | Wrapper → Primitive                    |
| BigInteger      | For very large numbers                 |
| Wrapper Classes | Helps use primitives in object context |

---
