Here are **clean, interview-ready solutions with explanations and Java examples** for each problem.

---

## 1. Reverse a Number (without built-in methods)

### Logic

Extract last digit using `% 10` and build new number.

### Code

```java
public class ReverseNumber {
    public static void main(String[] args) {
        int num = 12345;
        int reversed = 0;

        while (num != 0) {
            int lastDigit = num % 10;
            reversed = reversed * 10 + lastDigit;
            num = num / 10;
        }

        System.out.println("Reversed number: " + reversed);
    }
}
```

✅ Output: `54321`

---

## 2. Check if a String is a Palindrome

A palindrome reads the same forward and backward.

### Code

```java
public class PalindromeCheck {
    public static void main(String[] args) {
        String str = "madam";
        String reversed = "";

        for (int i = str.length() - 1; i >= 0; i--) {
            reversed += str.charAt(i);
        }

        if (str.equals(reversed)) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not Palindrome");
        }
    }
}
```

✅ Output: `Palindrome`

---

## 3. Count Frequency of Characters in a String

Using `HashMap`.

### Code

```java
import java.util.HashMap;
import java.util.Map;

public class CharacterFrequency {
    public static void main(String[] args) {
        String str = "programming";
        Map<Character, Integer> map = new HashMap<>();

        for (char ch : str.toCharArray()) {
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }

        System.out.println(map);
    }
}
```

✅ Output:

```
{p=1, r=2, o=1, g=2, a=1, m=2, i=1, n=1}
```

---

## 4. Find Largest and Smallest in an Array

### Code

```java
public class MinMaxArray {
    public static void main(String[] args) {
        int[] arr = {5, 2, 8, 1, 9};

        int min = arr[0];
        int max = arr[0];

        for (int num : arr) {
            if (num < min) min = num;
            if (num > max) max = num;
        }

        System.out.println("Smallest: " + min);
        System.out.println("Largest: " + max);
    }
}
```

✅ Output:

```
Smallest: 1  
Largest: 9
```

---

## 5. Swap Two Numbers Without Third Variable

Using arithmetic:

### Code

```java
public class SwapNumbers {
    public static void main(String[] args) {
        int a = 10, b = 20;

        a = a + b;
        b = a - b;
        a = a - b;

        System.out.println("a = " + a);
        System.out.println("b = " + b);
    }
}
```

✅ Output:

```
a = 20  
b = 10
```

---

## 6. Optimized Prime Check (For Large Numbers)

Check only up to `√n`.

### Code

```java
public class PrimeCheck {
    public static void main(String[] args) {
        int num = 97;
        boolean isPrime = true;

        if (num <= 1) {
            isPrime = false;
        } else {
            for (int i = 2; i * i <= num; i++) {
                if (num % i == 0) {
                    isPrime = false;
                    break;
                }
            }
        }

        System.out.println(isPrime ? "Prime" : "Not Prime");
    }
}
```

✅ Faster and efficient.

---

## 7. Custom `MathUtils` Class with Method Overloading

### Code

```java
public class MathUtils {

    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }

    public static void main(String[] args) {
        MathUtils utils = new MathUtils();

        System.out.println(utils.add(5, 10));       // 15
        System.out.println(utils.add(5.5, 2.5));   // 8.0
    }
}
```

---

## 8. JVM Memory Areas (With Simple Example)

### JVM Memory Areas:

| Memory Area  | Stores                              |
| ------------ | ----------------------------------- |
| Heap         | Objects and instance variables      |
| Stack        | Local variables and function calls  |
| Method Area  | Static variables and class metadata |
| PC Register  | Current instruction                 |
| Native Stack | Native method calls                 |

### Example:

```java
class Test {
    static int a = 10;  // Stored in Method Area
    int b = 20;         // Stored in Heap

    void display() {
        int c = 30;     // Stored in Stack
    }
}
```

---

## 9. What Happens When Static Variables Are Used Across Multiple Classes?

Static variables:
✅ Belong to the class
✅ Shared among all instances
✅ Accessible using ClassName

### Example:

```java
class Counter {
    static int count = 0;

    Counter() {
        count++;
    }
}

public class Main {
    public static void main(String[] args) {
        new Counter();
        new Counter();

        System.out.println(Counter.count);
    }
}
```

✅ Output:

```
2
```

### Explanation:

• Only one copy exists
• All objects share the same memory
• Stored in Method Area / Metaspace

---

## ✅ Final Summary Table

| Problem            | Concept Used              |
| ------------------ | ------------------------- |
| Reverse number     | Modulo arithmetic         |
| Palindrome         | Loop & string comparison  |
| Frequency count    | HashMap                   |
| Min & Max          | Array traversal           |
| Swap               | Arithmetic                |
| Prime check        | √n optimization           |
| Method overloading | Same name, different args |
| JVM Memory         | Stack, Heap, Method Area  |
| Static variables   | Class-level shared data   |

---
