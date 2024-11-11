
---

### 1. **Abstraction**

**Definition**: Abstraction is a concept that simplifies complex systems by modeling classes based on essential characteristics and hiding irrelevant details. It focuses on what an object does rather than how it does it.

**Purpose**: The main goal of abstraction is to reduce complexity by hiding unnecessary details from the user and focusing only on the essential parts. This makes it easier to work with complex systems and to make the code more maintainable and understandable.

**How It Works**:
- **Abstract Classes and Interfaces**: In Java, abstraction can be achieved through abstract classes and interfaces. An abstract class can have both abstract methods (without implementation) and concrete methods (with implementation), while an interface only has abstract methods.
- **Focus on Behavior**: With abstraction, you define behaviors that subclasses must implement, rather than focusing on how each behavior works.

**Example**:
```java
// Abstract class
abstract class Vehicle {
    // Abstract method (doesn't have a body)
    abstract void start();
    
    // Concrete method (has a body)
    void stop() {
        System.out.println("Vehicle stopped");
    }
}

// Concrete subclass
class Car extends Vehicle {
    // Implement the abstract method
    void start() {
        System.out.println("Car started");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle myCar = new Car();
        myCar.start(); // Output: Car started
        myCar.stop();  // Output: Vehicle stopped
    }
}
```

Here, `Vehicle` is an abstract class that only defines the behavior (`start`) without implementing it. This allows the `Car` class to define its specific way of starting.

**Benefits of Abstraction**:
- Simplifies the interface exposed to the user.
- Enhances code readability and reduces complexity.
- Encourages reuse and helps prevent redundancy in code.

---

### 2. **Encapsulation**

**Definition**: Encapsulation is the concept of bundling data (fields) and methods that operate on the data into a single unit, typically a class. Encapsulation restricts direct access to some of an object’s components, which is essential for maintaining control over the state of the object.

**Purpose**: The main goal of encapsulation is to protect the data inside a class from unintended modifications and to provide a controlled way of accessing or modifying it through methods. This is crucial for maintaining a clean and consistent state of the object.

**How It Works**:
- **Private Fields and Public Methods**: In Java, encapsulation is typically achieved by declaring fields as `private` and providing public getter and setter methods to access and modify these fields.
- **Controlled Access**: Encapsulation allows you to control access to the internal data of the class. For example, you can add validation in setter methods to ensure that only valid data is assigned to fields.

**Example**:
```java
public class Student {
    // Private fields (data hidden from outside access)
    private String name;
    private int age;

    // Public getter method for name
    public String getName() {
        return name;
    }

    // Public setter method for name
    public void setName(String name) {
        this.name = name;
    }

    // Public getter method for age
    public int getAge() {
        return age;
    }

    // Public setter method for age with validation
    public void setAge(int age) {
        if(age > 0) { // Simple validation
            this.age = age;
        } else {
            System.out.println("Age must be positive");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Student student = new Student();
        student.setName("Alice");
        student.setAge(20);

        System.out.println("Name: " + student.getName());
        System.out.println("Age: " + student.getAge());
    }
}
```

In this example, the `Student` class encapsulates its data (`name` and `age`) and provides controlled access through getter and setter methods.

**Benefits of Encapsulation**:
- Protects the internal state of the object by restricting direct access.
- Provides controlled access to data, allowing you to implement validation.
- Makes code more flexible and easier to change without affecting other parts of the program.

---

### 3. **Data Hiding**

**Definition**: Data hiding is the process of restricting access to certain details of an object or class. In essence, it's about preventing direct access to the data members of a class, which is often achieved through encapsulation.

**Purpose**: The primary goal of data hiding is to enhance security by preventing unauthorized or unintended access to sensitive data and by ensuring that data can only be accessed or modified through well-defined methods.

**How It Works**:
- **Private Access Modifier**: By declaring variables as `private`, they are hidden from outside classes. Only the methods within the same class can access these variables.
- **Providing Public Methods (Encapsulation)**: You can then use public methods (e.g., getters and setters) to selectively expose or hide parts of the data to outside classes.

**Example**:
```java
public class BankAccount {
    // Private field (data hidden from outside access)
    private double balance;

    // Constructor
    public BankAccount(double initialBalance) {
        if (initialBalance > 0) {
            balance = initialBalance;
        } else {
            balance = 0;
            System.out.println("Initial balance must be positive");
        }
    }

    // Public method to deposit money (encapsulates balance manipulation)
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        } else {
            System.out.println("Deposit amount must be positive");
        }
    }

    // Public method to check balance
    public double getBalance() {
        return balance;
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(100);
        account.deposit(50);
        System.out.println("Balance: " + account.getBalance()); // Output: Balance: 150
    }
}
```

Here, `balance` is private and cannot be accessed directly from outside the `BankAccount` class. It can only be modified through methods like `deposit`, which allows us to control and validate the operation.

**Benefits of Data Hiding**:
- Prevents accidental or unauthorized modifications to sensitive data.
- Protects the integrity of the internal state of an object.
- Makes code more robust and secure.

---

### Summary of Differences

| Concept        | Definition                                                                                            | Purpose                                                                                                   |
|----------------|-------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| **Abstraction** | Hides unnecessary details and exposes only essential features.                                        | Simplifies complexity by focusing on high-level behaviors.                                                |
| **Encapsulation** | Bundles data and methods together, providing controlled access.                                    | Protects data within a class and offers controlled access through methods.                                |
| **Data Hiding**   | Restricts access to the internal state of an object by using private fields and public methods.     | Enhances security and prevents unintended access or modification to sensitive data.                       |

