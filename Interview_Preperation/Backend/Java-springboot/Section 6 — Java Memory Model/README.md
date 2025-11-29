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
