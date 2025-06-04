
---

### 🔷 OOPS

| Q# | Question                                                                                              | Answer                                                                                 | Concept(s) Tested                     | Difficulty |
| -- | ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------- | ---------- |
| 1  | You're building a ride-sharing app. How would you represent different vehicle types in code?          | Use Inheritance with a base `Vehicle` class and subclasses like `Bike`, `Car`, `Auto`. | Inheritance, Polymorphism             | Medium     |
| 2  | If I remove the constructor from a class that initializes values, what happens?                       | Object will use default constructor; custom values won't be set.                       | Constructors                          | Easy       |
| 3  | How do you restrict access to sensitive data inside a class?                                          | Use `private` access modifier and provide `getters/setters`.                           | Encapsulation                         | Easy       |
| 4  | You want a class that can't be extended. What do you do?                                              | Declare the class as `final`.                                                          | Inheritance control                   | Medium     |
| 5  | How do you ensure all your object types implement a certain method?                                   | Define an Interface and implement it.                                                  | Abstraction, Interface                | Medium     |
| 6  | You have multiple login user types (admin, guest, user). How would you handle this?                   | Use method overriding in subclasses of a base `User` class.                            | Polymorphism                          | Medium     |
| 7  | If two classes have the same method name, how is it resolved?                                         | At runtime if overridden (polymorphism), at compile-time if overloaded.                | Method Overloading & Overriding       | Medium     |
| 8  | How do you prevent someone from creating multiple objects of a class?                                 | Use Singleton pattern.                                                                 | Singleton, Object control             | Medium     |
| 9  | What’s better for defining a blueprint — Interface or Abstract Class?                                 | Interface when behavior is expected from multiple unrelated classes.                   | Abstraction                           | Medium     |
| 10 | Imagine a `Person` class where name should never be changed once set. How will you design it?         | Make the `name` field `private final` and initialize it via constructor only.          | Immutability                          | Medium     |
| 11 | You are given a class where anyone can directly change the data. What issue might this cause?         | Breaks encapsulation; data can become inconsistent or insecure.                        | Encapsulation                         | Easy       |
| 12 | What would happen if a class inherits two methods with the same signature from two interfaces?        | The class must override the method to resolve conflict.                                | Multiple Inheritance (via Interfaces) | Hard       |
| 13 | Why is abstraction helpful in large-scale applications?                                               | Hides implementation details and allows teams to work independently on modules.        | Abstraction                           | Medium     |
| 14 | How can OOP help in reducing code duplication across multiple classes?                                | Through inheritance and polymorphism.                                                  | Code Reusability                      | Medium     |
| 15 | How would you explain the difference between "is-a" and "has-a" relationships in real world examples? | "is-a" for inheritance (Car is-a Vehicle), "has-a" for aggregation (Car has-a Engine). | Inheritance vs Aggregation            | Easy       |

---

### 🔷 OOPS

---

### ✅ Q1. You need to build a class whose state shouldn't change once it's created.

**Task:** Create one immutable class and one mutable class.
**Concept(s):** Immutability, Encapsulation
**Difficulty:** Medium

```java
// Immutable class
public final class ImmutablePerson {
    private final String name;
    private final int age;

    public ImmutablePerson(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() { return name; }
    public int getAge() { return age; }
}

// Mutable class
public class MutablePerson {
    private String name;
    private int age;

    public MutablePerson(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public int getAge() { return age; }
    public void setAge(int age) { this.age = age; }
}
```

---

### ✅ Q2. You want to enforce that all shape types must implement an area method.

**Task:** Create an interface and two classes implementing it.
**Concept(s):** Interface, Abstraction
**Difficulty:** Medium

```java
interface Shape {
    double area();
}

class Circle implements Shape {
    private double radius;

    public Circle(double r) { this.radius = r; }

    public double area() {
        return Math.PI * radius * radius;
    }
}

class Rectangle implements Shape {
    private double width, height;

    public Rectangle(double w, double h) {
        this.width = w;
        this.height = h;
    }

    public double area() {
        return width * height;
    }
}
```

---

### ✅ Q3. You want to allow to process different types of payments (UPI, Card).

**Task:** Write a class with overloaded methods.
**Concept(s):** Polymorphism, Overloading
**Difficulty:** Easy

```java
class PaymentProcessor {
    public void pay(String upiId, double amount) {
        System.out.println("Paid " + amount + " via UPI: " + upiId);
    }

    public void pay(String cardNumber, String cvv, double amount) {
        System.out.println("Paid " + amount + " via Card: " + cardNumber);
    }
}
```

---

### ✅ Q4. Ensure that only one object of Logger class is created across the app.

**Task:** Implement Singleton pattern.
**Concept(s):** Object control, Singleton
**Difficulty:** Hard

```java
public class Logger {
    private static Logger instance;

    private Logger() {
        // private constructor
    }

    public static synchronized Logger getInstance() {
        if (instance == null) {
            instance = new Logger();
        }
        return instance;
    }

    public void log(String message) {
        System.out.println("Log: " + message);
    }
}
```

---

### ✅ Q5. Model a school system where `Teacher` and `Student` both extend `Person`.

**Task:** Create a class hierarchy.
**Concept(s):** Inheritance
**Difficulty:** Medium

```java
class Person {
    private String name;

    public Person(String name) { this.name = name; }

    public String getName() { return name; }
}

class Teacher extends Person {
    private String subject;

    public Teacher(String name, String subject) {
        super(name);
        this.subject = subject;
    }

    public String getSubject() { return subject; }
}

class Student extends Person {
    private int grade;

    public Student(String name, int grade) {
        super(name);
        this.grade = grade;
    }

    public int getGrade() { return grade; }
}
```

---

### ✅ Q6. Create a method that behaves differently in child class but with same method name.

**Task:** Use method overriding.
**Concept(s):** Runtime Polymorphism
**Difficulty:** Medium

```java
class Animal {
    public void sound() {
        System.out.println("Some generic animal sound");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Bark");
    }
}
```

---

### ✅ Q7. Prevent a class from being subclassed and show a use case.

**Task:** Create a `final` class.
**Concept(s):** Inheritance Restriction
**Difficulty:** Easy

```java
public final class Constants {
    public static final String APP_NAME = "MyApp";
    // No subclassing allowed
}
```

---

### ✅ Q8. Build a class that has a `Student` list as its field and can print total students.

**Task:** Demonstrate Aggregation (has-a).
**Concept(s):** Aggregation
**Difficulty:** Medium

```java
import java.util.List;

class School {
    private List<Student> students;

    public School(List<Student> students) {
        this.students = students;
    }

    public int totalStudents() {
        return students.size();
    }
}

class Student {
    private String name;

    public Student(String name) { this.name = name; }

    public String getName() { return name; }
}
```

---

### ✅ Q9. Create a base class `Account` and two subclasses `SavingsAccount`, `CurrentAccount`.

**Task:** Implement and override a common method.
**Concept(s):** Inheritance, Overriding
**Difficulty:** Medium

```java
class Account {
    protected double balance;

    public Account(double balance) { this.balance = balance; }

    public void showAccountType() {
        System.out.println("General Account");
    }
}

class SavingsAccount extends Account {
    public SavingsAccount(double balance) { super(balance); }

    @Override
    public void showAccountType() {
        System.out.println("Savings Account");
    }
}

class CurrentAccount extends Account {
    public CurrentAccount(double balance) { super(balance); }

    @Override
    public void showAccountType() {
        System.out.println("Current Account");
    }
}
```

---

### ✅ Q10. Restrict access to sensitive user details and allow only read-only access.

**Task:** Use private fields and only public getters.
**Concept(s):** Encapsulation
**Difficulty:** Easy

```java
class User {
    private String username;
    private String email;

    public User(String username, String email) {
        this.username = username;
        this.email = email;
    }

    public String getUsername() { return username; }

    public String getEmail() { return email; }

    // No setters - read-only access
}
```

---
