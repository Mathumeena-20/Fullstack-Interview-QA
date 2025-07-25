## 1. **Explain Python’s OOP Concepts: Inheritance, Polymorphism, Encapsulation**

### 🔹 Inheritance

**Explanation:**
Inheritance allows one class to acquire the properties and methods of another class.


**Example:**

```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):
    def bark(self):
        print("Dog barks")

dog = Dog()
dog.speak()  # Inherited
dog.bark()   # Own method
```

---

### 🔹 Polymorphism

**Explanation:**
Polymorphism allows different classes to use the same method name but with different behaviors.

**Example:**

```python
class Cat:
    def sound(self):
        print("Meow")

class Dog:
    def sound(self):
        print("Bark")

# Polymorphism in action
for animal in (Cat(), Dog()):
    animal.sound()
```

---

### 🔹 Encapsulation

**Explanation:**
Encapsulation hides internal data and restricts direct access to it.
It is done by using **private members**.

**Example:**

```python
class Person:
    def __init__(self, name):
        self.__name = name  # Private variable

    def get_name(self):
        return self.__name

person = Person("Alice")
print(person.get_name())  # Access through method
# print(person.__name)    # Error: can't access private variable directly
```

---

## 2. **What are Class Methods, Instance Methods, and Static Methods?**

### 🔹 Instance Method

**Explanation:**
Instance method is a function defined within a class that operate specific instance of a class
**Example:**

```python
class Sample:
    def instance_method(self):
        print("Instance method called")
```

---

### 🔹 Class Method

**Explanation:**
Class method is the method that is bound to the class itself,rather than the instance of the class

**Example:**

```python
class Sample:
    count = 0

    @classmethod
    def class_method(cls):
        print("Class method called. Count:", cls.count)
```

---

### 🔹 Static Method

**Explanation:**
No class or instance context.
Behaves like a regular function but inside a class.

**Example:**

```python
class Sample:
    @staticmethod
    def static_method():
        print("Static method called")
```

---

## 3. **What is Method Overriding?**

### Explanation:

When a subclass defines a method with the same name as a method in the parent class, the subclass method overrides the parent method.

**Example:**

```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):
    def speak(self):  # Overriding
        print("Dog barks")

dog = Dog()
dog.speak()  # Output: Dog barks
```

---

## 4. **What is the Use of the `super()` Function?**

### Explanation:

* `super()` is used to call methods from the parent class inside a child class.
* Helps in extending parent class functionality.

**Example:**

```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):
    def speak(self):
        super().speak()  # Call parent method
        print("Dog barks")

dog = Dog()
dog.speak()

# Output:
# Animal speaks
# Dog barks
```

---

## 5. **How are Private, Protected, and Public Members Handled in Python?**

| Access Level | Syntax        | Access Scope                                              |
| ------------ | ------------- | --------------------------------------------------------- |
| Public       | `self.name`   | Accessible everywhere                                     |
| Protected    | `self._name`  | Accessible in class & subclass (convention, not enforced) |
| Private      | `self.__name` | Name mangling restricts access                            |

### Example:

```python
class Sample:
    def __init__(self):
        self.public = "Public"
        self._protected = "Protected"
        self.__private = "Private"

obj = Sample()
print(obj.public)       # Allowed
print(obj._protected)   # Allowed but discouraged
# print(obj.__private)  # Error: Cannot access directly

# Access private using name mangling:
print(obj._Sample__private)  # Allowed but not recommended
```

---

## ✅ Summary Table

| Concept                  | Key Point                             |
| ------------------------ | ------------------------------------- |
| Inheritance              | Reuse parent class methods/attributes |
| Polymorphism             | Same method name, different classes   |
| Encapsulation            | Hide internal details                 |
| Instance Method          | Works on object data                  |
| Class Method             | Works on class data                   |
| Static Method            | Independent of class/object           |
| Method Overriding        | Redefine parent method in child class |
| super()                  | Call parent class methods             |
| Private/Protected/Public | Access control in classes             |

---

If you want, I can help you with:

* More **OOP coding problems**
* **Practice exercises**
* Mock interview style Q\&A

Let me know!
