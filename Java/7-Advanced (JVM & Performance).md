## 1️⃣ JVM vs JDK vs JRE

* **JVM (Java Virtual Machine)**
  → Executes Java bytecode. Platform-dependent. Responsible for memory management, GC, JIT compilation.

* **JRE (Java Runtime Environment)**
  → Provides libraries + JVM to run Java programs. Doesn’t have dev tools.

* **JDK (Java Development Kit)**
  → JRE + compilers (javac), debuggers, tools. Needed for development.

🔹 Diagram:

```
JDK = JRE + Development Tools
JRE = JVM + Libraries
JVM = Executes Bytecode
```

👉 Interview tip: If asked "Can JVM exist without JDK?" → Yes, JVM can run already compiled classes, but cannot compile them.

---

## 2️⃣ ClassLoader in Java

* Responsible for **loading classes into JVM**.
* Three types:

  1. **Bootstrap ClassLoader** → loads core Java classes (`rt.jar`, `java.*`).
  2. **Extension ClassLoader** → loads `ext/*` libraries.
  3. **Application (System) ClassLoader** → loads user classes from classpath.

🔹 Example:

```java
public class ClassLoaderTest {
    public static void main(String[] args) {
        System.out.println(String.class.getClassLoader()); 
        // null (Bootstrap)

        System.out.println(ClassLoaderTest.class.getClassLoader()); 
        // AppClassLoader
    }
}
```

👉 Interview tip: You can also write **custom ClassLoaders** for dynamic loading.

---

## 3️⃣ Heap and Stack Memory

* **Stack Memory**:
  → Stores method calls, local variables. Each thread has its own stack.

* **Heap Memory**:
  → Stores objects, shared across threads. Divided into:

  * Young Gen (Eden + Survivor) → short-lived objects.
  * Old Gen → long-lived objects.
  * PermGen/Metaspace → class metadata (Java 8+ uses Metaspace).

🔹 Example:

```java
public class MemoryExample {
    public static void main(String[] args) {
        int a = 10;                 // Stack
        String s = new String("Hi");// Heap
    }
}
```

👉 Interview tip: `StackOverflowError` → too many nested calls; `OutOfMemoryError: Java heap space` → heap full.

---

## 4️⃣ Garbage Collection (GC)

* **Automatic memory management** by JVM.
* Objects with **no live references** become eligible for GC.
* GC algorithms: **Serial, Parallel, CMS, G1**.

🔹 Example:

```java
public class GCExample {
    public static void main(String[] args) {
        GCExample obj = new GCExample();
        obj = null; // eligible for GC
        System.gc(); // Request GC
    }

    @Override
    protected void finalize() {
        System.out.println("GC called!");
    }
}
```

👉 Interview tip: `System.gc()` only **requests**, not guarantees collection.

---

## 5️⃣ References in Java

* **Strong Reference** → Normal reference. GC won’t collect until ref is null.
* **Soft Reference** → Collected only if memory is low. Useful for caches.
* **Weak Reference** → Collected at next GC cycle. Useful for maps (WeakHashMap).
* **Phantom Reference** → Collected but still tracked. Useful for post-cleanup.

🔹 Example:

```java
import java.lang.ref.*;

public class ReferenceExample {
    public static void main(String[] args) {
        // Strong reference
        String strong = new String("Strong");

        // Soft reference
        SoftReference<String> soft = new SoftReference<>(new String("Soft"));

        // Weak reference
        WeakReference<String> weak = new WeakReference<>(new String("Weak"));

        // Phantom reference
        PhantomReference<String> phantom = new PhantomReference<>(
            new String("Phantom"), new ReferenceQueue<>());

        System.out.println("Strong: " + strong);
        System.out.println("Soft: " + soft.get());
        System.out.println("Weak: " + weak.get());
        System.out.println("Phantom: " + phantom.get()); // Always null
    }
}
```

👉 Interview tip: `WeakHashMap` uses weak keys → entries auto-removed if key has no strong refs.

---

## 6️⃣ Serial vs Parallel Garbage Collector

* **Serial GC**

  * Single-threaded.
  * Suitable for small apps (client machines).
  * Low throughput, but simple.
  * JVM flag: `-XX:+UseSerialGC`.

* **Parallel GC (Throughput Collector)**

  * Multi-threaded for young and old gen.
  * Suitable for multi-core servers.
  * Prioritizes throughput over pause time.
  * JVM flag: `-XX:+UseParallelGC`.

👉 Interview tip:

* Serial GC = "stop-the-world" in one thread.
* Parallel GC = "stop-the-world" but uses **multiple threads**.

---

✅ **Quick Recap Table**

| Concept               | Explanation                                            | Example/Tip                    |
| --------------------- | ------------------------------------------------------ | ------------------------------ |
| JVM, JRE, JDK         | JVM runs bytecode, JRE = JVM + libs, JDK = JRE + tools | Must know difference           |
| ClassLoader           | Loads classes dynamically                              | Bootstrap, Extension, App      |
| Heap vs Stack         | Heap = objects, Stack = methods/vars                   | OOM vs StackOverflow           |
| Garbage Collection    | Auto memory mgmt, removes unused objects               | `System.gc()`                  |
| References            | Strong, Soft, Weak, Phantom                            | WeakHashMap for caches         |
| Serial vs Parallel GC | Serial = single-thread, Parallel = multi-thread        | Use flags `-XX:+UseParallelGC` |
