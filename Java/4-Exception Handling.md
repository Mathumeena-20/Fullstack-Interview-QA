## 1️⃣ Difference between Checked and Unchecked Exceptions

* **Checked Exceptions**

  * Checked at **compile time**.
  * Must be handled using `try-catch` or declared with `throws`.
  * Examples: `IOException`, `SQLException`, `ClassNotFoundException`.

* **Unchecked Exceptions**

  * Checked at **runtime** (not at compile time).
  * Subclass of `RuntimeException`.
  * Examples: `NullPointerException`, `ArithmeticException`, `ArrayIndexOutOfBoundsException`.

🔹 Example:

```java
import java.io.*;

class Test {
    public static void main(String[] args) {
        try {
            FileReader fr = new FileReader("abc.txt"); // Checked Exception
        } catch (IOException e) {
            System.out.println("File not found");
        }

        int x = 10/0; // Unchecked Exception (ArithmeticException)
    }
}
```

---

## 2️⃣ Difference between `throw` and `throws` keywords

* **throw** → Used to explicitly **throw** an exception (inside method).
* **throws** → Declares that a method **might throw** exceptions (method signature).

🔹 Example:

```java
class Test {
    void checkAge(int age) {
        if(age < 18) {
            throw new ArithmeticException("Not eligible"); // throw
        }
    }

    void readFile() throws IOException { // throws
        FileReader fr = new FileReader("data.txt");
    }
}
```

---

## 3️⃣ Can we write `try` without `catch`?

👉 Yes ✅, but only if you use a **`finally` block** or **try-with-resources**.

🔹 Example:

```java
try {
    int a = 5/0;
} finally {
    System.out.println("Finally always executes"); 
}
```

✅ This is useful when you want cleanup code (close file, release DB connection) without handling exception.

---

## 4️⃣ Difference between Try-with-Resources and Finally Block

* **Finally block** → Used to close resources manually (may lead to resource leaks if not done properly).
* **Try-with-resources (Java 7+)** → Automatically closes resources (objects implementing `AutoCloseable`).

🔹 Example (finally):

```java
FileReader fr = null;
try {
    fr = new FileReader("abc.txt");
} catch(Exception e) {
    System.out.println("Error: " + e);
} finally {
    if(fr != null) {
        try { fr.close(); } catch(Exception e) {}
    }
}
```

🔹 Example (try-with-resources):

```java
try(FileReader fr = new FileReader("abc.txt")) {
    System.out.println("File opened");
} catch(Exception e) {
    System.out.println("Error: " + e);
} 
// Resource automatically closed
```

---

## 5️⃣ What is Custom Exception in Java?

👉 A **user-defined exception class** that extends `Exception` (checked) or `RuntimeException` (unchecked).
Used when predefined exceptions don’t describe your application-specific error.

🔹 Example:

```java
class InvalidAgeException extends Exception {
    public InvalidAgeException(String msg) {
        super(msg);
    }
}

class Test {
    void checkAge(int age) throws InvalidAgeException {
        if(age < 18) throw new InvalidAgeException("Age must be >= 18");
        else System.out.println("Valid Age");
    }

    public static void main(String[] args) {
        try {
            new Test().checkAge(15);
        } catch (InvalidAgeException e) {
            System.out.println("Caught Exception: " + e.getMessage());
        }
    }
}
```

---

✅ **Summary (Interview Pointers):**

* Checked = compile-time, Unchecked = runtime.
* `throw` (inside method), `throws` (method signature).
* `try` without `catch` works with `finally` / try-with-resources.
* Try-with-resources = auto-closing, better than finally.
* Custom exception = extend `Exception` / `RuntimeException`.
