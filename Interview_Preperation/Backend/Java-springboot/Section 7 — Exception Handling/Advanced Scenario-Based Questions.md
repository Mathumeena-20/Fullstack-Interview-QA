# ⭐ 1. Design a Global Exception Handling Mechanism for a REST API (Spring Boot)

Use **@ControllerAdvice + @ExceptionHandler**.

### **Step 1: Create a standard error response**

```java
public class ApiError {
    private int status;
    private String message;
    private long timestamp = System.currentTimeMillis();

    public ApiError(int status, String message) {
        this.status = status;
        this.message = message;
    }
}
```

### **Step 2: Global exception handler**

```java
@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<ApiError> handleNotFound(ResourceNotFoundException ex) {
        return new ResponseEntity<>(new ApiError(404, ex.getMessage()), HttpStatus.NOT_FOUND);
    }

    @ExceptionHandler(InvalidAgeException.class)
    public ResponseEntity<ApiError> handleInvalidAge(InvalidAgeException ex) {
        return new ResponseEntity<>(new ApiError(400, ex.getMessage()), HttpStatus.BAD_REQUEST);
    }

    @ExceptionHandler(Exception.class)
    public ResponseEntity<ApiError> handleGeneric(Exception ex) {
        return new ResponseEntity<>(new ApiError(500, "Internal Server Error"), HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```

✔ Clean
✔ All exceptions handled in one centralized place
✔ Automatically returns proper JSON

---

# ⭐ 2. How do you manage exceptions in multi-threaded applications?

### ✔ Use `Thread.setDefaultUncaughtExceptionHandler`

Handles exceptions that escape a thread:

```java
Thread.setDefaultUncaughtExceptionHandler((t, e) -> {
    System.out.println("Thread failed: " + t.getName());
    e.printStackTrace();
});
```

### ✔ For ExecutorService

Use `Future.get()` to catch exceptions:

```java
ExecutorService service = Executors.newFixedThreadPool(3);
Future<?> f = service.submit(() -> {
    throw new RuntimeException("Task failed");
});

try { f.get(); } catch (ExecutionException e) {
    System.out.println("Exception: " + e.getCause());
}
```

### ✔ Use logging + monitoring

✔ Use fallback mechanisms (Retry, Circuit Breaker)

---

# ⭐ 3. How do you create custom business exceptions?

### Example:

```java
public class BusinessException extends RuntimeException {
    private final String code;

    public BusinessException(String message, String code) {
        super(message);
        this.code = code;
    }

    public String getCode() { return code; }
}
```

Used in service:

```java
if (age < 18) {
    throw new BusinessException("Age must be >= 18", "AGE_001");
}
```

---

# ⭐ 4. How exceptions affect application performance?

### ✔ Throwing exceptions is **expensive** because:

* Capturing stack trace consumes CPU
* Creating exception objects is heavy
* Exception-heavy code prevents JVM optimizations
* Frequent exceptions → GC pressure

### **Best Practices**

* Never use exceptions for normal flow control
* Use validations instead of throwing frequently
* Turn off stack trace computing for high-frequency exceptions:

```java
@Override
public synchronized Throwable fillInStackTrace() {
    return this; // improves performance
}
```

---

# ⭐ 5. Real-world debugging: Handling NullPointerException in production

### Steps:

### ✔ 1. Check logs & stack trace

Identify the exact class + line number.

### ✔ 2. Reproduce with sample data

Use the same inputs from logs.

### ✔ 3. Identify root cause

Common causes:

* Missing JSON fields
* Null from DB
* Missing request parameter
* Race condition in multi-threading

### ✔ 4. Add null validations

```java
Objects.requireNonNull(user, "User cannot be null");
```

### ✔ 5. Add proper default values

Use Optional:

```java
Optional.ofNullable(obj).orElse("default");
```

### ✔ 6. Improve logging

Add context:

```java
log.error("User {} not found for request {}", userId, requestId);
```

### ✔ 7. Deploy fix + add unit tests

---

# ⭐ 6. Create a custom exception InvalidAgeException

```java
public class InvalidAgeException extends RuntimeException {
    public InvalidAgeException(String msg) {
        super(msg);
    }
}
```

Usage:

```java
if (age < 0 || age > 150) {
    throw new InvalidAgeException("Invalid age: " + age);
}
```

---

# ⭐ 7. Write a function that reads a file using try-with-resources

```java
public void readFile(String path) {
    try (BufferedReader br = new BufferedReader(new FileReader(path))) {
        String line;
        while ((line = br.readLine()) != null) {
            System.out.println(line);
        }
    } catch (IOException e) {
        System.out.println("Error reading file: " + e.getMessage());
    }
}
```

✔ File automatically closed
✔ Cleaner than try-finally

---

# ⭐ 8. Explain finally vs return with example

**finally** executes *even if try has return*.

Example:

```java
public int test() {
    try {
        return 1;
    } finally {
        return 2;
    }
}
```

Result:

```
2   // because finally overrides return from try
```

---

# ⭐ 9. Demonstrate catching multiple exceptions in one block

Java 7+ allows multi-catch:

```java
try {
    int[] arr = new int[5];
    arr[10] = 100;
    int x = 10 / 0;
} catch (ArithmeticException | ArrayIndexOutOfBoundsException e) {
    System.out.println("Error: " + e.getMessage());
}
```

✔ Cleaner
✔ No need for duplicate code

---

# ⭐ 10. Convert a checked exception to unchecked (best practices)

Wrap checked exception inside a RuntimeException:

### ✔ Best practice: Exception wrapping

```java
try {
    Files.readAllLines(Paths.get("test.txt"));
} catch (IOException e) {
    throw new UncheckedIOException(e); // built-in wrapper
}
```

Or custom wrapper:

```java
catch (IOException e) {
    throw new RuntimeException("IO failed", e);
}
```

### Why?

* Makes code cleaner
* No try/catch pollution
* Still retains root cause (`e.getCause()`)

---

# ⭐ Final Interview Summary

| Topic                       | Key Point                                   |
| --------------------------- | ------------------------------------------- |
| Global exception handling   | Use @ControllerAdvice                       |
| Multi-threading exceptions  | Use UncaughtExceptionHandler + Future.get() |
| Custom business exceptions  | Extend RuntimeException                     |
| Performance                 | Exceptions expensive; avoid frequent throws |
| NPE debugging               | Logs, reproduce, validations, Optional      |
| InvalidAgeException         | Simple custom exception                     |
| TWR file reading            | Auto closes resources                       |
| finally vs return           | finally overrides return                    |
| Multi-catch                 | Java 7+ feature                             |
| Convert checked → unchecked | Wrap inside RuntimeException                |

---

