## 🧩 **1️⃣ Reverse a String or Integer**

### ✅ Reverse a String

```java
public class ReverseString {
    public static void main(String[] args) {
        String str = "Mathu";
        String reversed = new StringBuilder(str).reverse().toString();
        System.out.println("Reversed: " + reversed);
    }
}
```

🧠 **Output:**

```
Reversed: uhtaM
```

✅ **Explanation:**

* `StringBuilder` is mutable and has a `reverse()` method.
* Using loops is also possible but less efficient.

---

### ✅ Reverse an Integer

```java
public class ReverseInteger {
    public static void main(String[] args) {
        int num = 12345;
        int rev = 0;

        while (num != 0) {
            rev = rev * 10 + num % 10;
            num = num / 10;
        }

        System.out.println("Reversed: " + rev);
    }
}
```

🧠 **Output:**

```
Reversed: 54321
```

---

## 🔢 **2️⃣ Check if a Number is Prime or Palindrome**

### ✅ Prime Number

```java
public class PrimeCheck {
    public static void main(String[] args) {
        int n = 13;
        boolean prime = true;

        for (int i = 2; i <= n / 2; i++) {
            if (n % i == 0) {
                prime = false;
                break;
            }
        }

        System.out.println(n + (prime ? " is Prime" : " is Not Prime"));
    }
}
```

🧠 **Output:**

```
13 is Prime
```

---

### ✅ Palindrome Number

```java
public class PalindromeCheck {
    public static void main(String[] args) {
        int n = 121, temp = n, rev = 0;

        while (n != 0) {
            rev = rev * 10 + n % 10;
            n = n / 10;
        }

        System.out.println(temp == rev ? "Palindrome" : "Not Palindrome");
    }
}
```

🧠 **Output:**

```
Palindrome
```

---

## 🧮 **3️⃣ Find Duplicate Elements in an Array**

### ✅ Using HashSet

```java
import java.util.*;

public class DuplicateElements {
    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 3, 7, 1, 9};
        Set<Integer> seen = new HashSet<>();
        Set<Integer> duplicates = new HashSet<>();

        for (int num : arr) {
            if (!seen.add(num)) {
                duplicates.add(num);
            }
        }

        System.out.println("Duplicates: " + duplicates);
    }
}
```

🧠 **Output:**

```
Duplicates: [1, 3]
```

✅ **Explanation:**

* `HashSet.add()` returns `false` if element already exists — used to detect duplicates.

---

## 🥈 **4️⃣ Find the Second Largest Number in an Array**

### ✅ Using Sorting

```java
import java.util.Arrays;

public class SecondLargest {
    public static void main(String[] args) {
        int[] arr = {10, 5, 8, 12, 3};
        Arrays.sort(arr);
        System.out.println("Second Largest: " + arr[arr.length - 2]);
    }
}
```

🧠 **Output:**

```
Second Largest: 10
```

### ✅ Without Sorting

```java
public class SecondLargestNoSort {
    public static void main(String[] args) {
        int[] arr = {12, 35, 1, 10, 34, 1};
        int first = Integer.MIN_VALUE, second = Integer.MIN_VALUE;

        for (int num : arr) {
            if (num > first) {
                second = first;
                first = num;
            } else if (num > second && num != first) {
                second = num;
            }
        }

        System.out.println("Second Largest: " + second);
    }
}
```

🧠 **Output:**

```
Second Largest: 34
```

---

## 🧾 **5️⃣ Sort a List of Custom Objects**

### ✅ Using `Comparator` (Java 8)

```java
import java.util.*;

class Employee {
    int id;
    String name;
    public Employee(int id, String name) {
        this.id = id; this.name = name;
    }
}

public class SortObjects {
    public static void main(String[] args) {
        List<Employee> list = Arrays.asList(
            new Employee(3, "Kavi"),
            new Employee(1, "Arun"),
            new Employee(2, "Mathu")
        );

        list.sort(Comparator.comparing(e -> e.name));

        list.forEach(e -> System.out.println(e.id + " " + e.name));
    }
}
```

🧠 **Output:**

```
1 Arun
3 Kavi
2 Mathu
```

✅ **Explanation:**

* `Comparator.comparing()` sorts using any field (name, id, salary, etc.).
* You can reverse using `.reversed()`.

---

## 🔤 **6️⃣ Count Character Frequency in a String**

### ✅ Using `HashMap`

```java
import java.util.*;

public class CharFrequency {
    public static void main(String[] args) {
        String str = "java rocks";
        Map<Character, Integer> freq = new HashMap<>();

        for (char c : str.toCharArray()) {
            if (c != ' ')
                freq.put(c, freq.getOrDefault(c, 0) + 1);
        }

        System.out.println(freq);
    }
}
```

🧠 **Output:**

```
{a=2, r=1, c=1, s=1, v=1, j=1, o=1, k=1}
```

---

## 🌊 **7️⃣ Use Stream API to Filter Even Numbers and Collect into a List**

### ✅ Stream Example

```java
import java.util.*;
import java.util.stream.Collectors;

public class StreamFilter {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 15, 20, 25, 30);

        List<Integer> evens = numbers.stream()
                                     .filter(n -> n % 2 == 0)
                                     .collect(Collectors.toList());

        System.out.println("Even numbers: " + evens);
    }
}
```

🧠 **Output:**

```
Even numbers: [10, 20, 30]
```

✅ **Explanation:**

* `stream()` creates stream pipeline.
* `filter()` filters based on condition.
* `collect()` gathers output into list.

---

## 🧵 **8️⃣ Implement Producer-Consumer Problem using Threads**

This is a **classic multithreading question** to test understanding of `wait()` and `notify()`.

---

### 💻 Example:

```java
import java.util.LinkedList;

class Buffer {
    private LinkedList<Integer> list = new LinkedList<>();
    private int capacity = 3;

    public synchronized void produce(int value) throws InterruptedException {
        while (list.size() == capacity) {
            wait();  // wait if buffer full
        }
        list.add(value);
        System.out.println("Produced: " + value);
        notify(); // notify consumer
    }

    public synchronized void consume() throws InterruptedException {
        while (list.isEmpty()) {
            wait();  // wait if buffer empty
        }
        int value = list.removeFirst();
        System.out.println("Consumed: " + value);
        notify(); // notify producer
    }
}

public class ProducerConsumer {
    public static void main(String[] args) {
        Buffer buffer = new Buffer();

        Thread producer = new Thread(() -> {
            for (int i = 1; i <= 5; i++) {
                try { buffer.produce(i); Thread.sleep(500); } catch (InterruptedException e) {}
            }
        });

        Thread consumer = new Thread(() -> {
            for (int i = 1; i <= 5; i++) {
                try { buffer.consume(); Thread.sleep(1000); } catch (InterruptedException e) {}
            }
        });

        producer.start();
        consumer.start();
    }
}
```

🧠 **Sample Output:**

```
Produced: 1
Consumed: 1
Produced: 2
Produced: 3
Consumed: 2
Produced: 4
Consumed: 3
Produced: 5
Consumed: 4
Consumed: 5
```

✅ **Explanation:**

* `wait()` → pauses thread until notified.
* `notify()` → wakes up another waiting thread.
* Ensures producer & consumer operate in sync without race condition.

---

# 🧠 **Summary Table**

| Problem           | Concept Used           | Key Java API        |
| ----------------- | ---------------------- | ------------------- |
| Reverse String    | Mutable objects        | StringBuilder       |
| Prime/Palindrome  | Loops                  | Math logic          |
| Duplicates        | Set                    | HashSet             |
| Second Largest    | Array traversal        | Arrays.sort         |
| Sort Objects      | Functional Programming | Comparator          |
| Char Frequency    | Counting               | HashMap             |
| Filter Even       | Stream API             | filter(), collect() |
| Producer-Consumer | Multithreading         | wait(), notify()    |
