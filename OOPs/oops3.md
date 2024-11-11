

---

### 1. Principles of OOP

Object-Oriented Programming (OOP) is a programming paradigm that uses objects and classes for organizing software design. The core principles of OOP help structure software in a way that makes it modular, reusable, and easier to maintain. The main principles are:

- **Encapsulation**  
- **Inheritance**  
- **Polymorphism**  
- **Abstraction**

These principles help developers design systems that are easier to understand, extend, and maintain.

---

### 2. Inheritance

**Inheritance** is one of the key features of OOP. It allows a class to inherit properties and methods from another class. The class that inherits is called the **subclass** (or **derived class**), and the class from which it inherits is called the **superclass** (or **base class**).

**Purpose of Inheritance**:
- Code Reusability: Subclasses can reuse code defined in a superclass, which reduces redundancy.
- Hierarchical Classification: Inheritance establishes a relationship between the parent class and the child class, creating a class hierarchy.

**Example**:  
Let’s say we have a `Vehicle` class that has common properties like `brand`, `model`, and `year`. Now, if we create subclasses like `Car` and `Truck`, they would inherit the common properties of the `Vehicle` class.

```java
// Superclass
class Vehicle {
    String brand;
    String model;
    int year;

    public Vehicle(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }

    public void displayInfo() {
        System.out.println("Brand: " + brand + ", Model: " + model + ", Year: " + year);
    }
}

// Subclass
class Car extends Vehicle {
    int doors;

    public Car(String brand, String model, int year, int doors) {
        super(brand, model, year);
        this.doors = doors;
    }

    public void displayCarInfo() {
        displayInfo(); // Inherited method
        System.out.println("Doors: " + doors);
    }
}

public class Main {
    public static void main(String[] args) {
        Car car = new Car("Toyota", "Corolla", 2020, 4);
        car.displayCarInfo();
    }
}
```

**Explanation**:  
In the example above, the `Car` class inherits the properties and methods from the `Vehicle` class. We use the `super()` keyword to call the constructor of the superclass.

---

### 3. The `private` Keyword

The **`private` keyword** is used to restrict access to class members (fields or methods) so that they cannot be accessed from outside the class. This is one of the ways to achieve **Encapsulation**, which helps protect the internal state of an object.

**Why Use `private`?**
- **Data Protection**: Prevents external classes from directly modifying the internal state of an object.
- **Control Access**: Using getters and setters, you can control how the data is accessed or modified.

**Example**:

```java
class BankAccount {
    private double balance;

    public BankAccount(double balance) {
        this.balance = balance;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if(amount > 0) {
            balance += amount;
        }
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(1000);
        account.deposit(500);
        System.out.println("Balance: " + account.getBalance()); // Accessed through a getter
    }
}
```

**Explanation**:  
The `balance` field is marked as `private`, so it cannot be accessed directly outside the `BankAccount` class. Instead, we use the `getBalance()` method to retrieve its value and the `deposit()` method to modify it.

---

### 4. The `super` Keyword

The **`super` keyword** refers to the superclass (parent class) of the current object. It is used in subclasses to:
- Call a superclass constructor.
- Access a superclass method or field that has been overridden or hidden by the subclass.

**Example**:

```java
class Animal {
    String name;

    public Animal(String name) {
        this.name = name;
    }

    public void makeSound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    public Dog(String name) {
        super(name); // Calling the superclass constructor
    }

    @Override
    public void makeSound() {
        super.makeSound(); // Calling the superclass method
        System.out.println("Woof!");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog("Buddy");
        dog.makeSound();
    }
}
```

**Explanation**:  
The `super()` is used in the `Dog` constructor to call the `Animal` constructor and initialize the `name`. Also, `super.makeSound()` calls the `makeSound` method from the `Animal` class before printing the dog’s specific sound.

---

### 5. Types of Inheritance

Inheritance can be categorized into the following types:

1. **Single Inheritance**: A subclass inherits from a single superclass.
   - **Example**: A `Car` class inherits from a `Vehicle` class.

2. **Multiple Inheritance**: A subclass inherits from multiple classes. Java does not allow multiple inheritance directly with classes to avoid ambiguity, but this can be achieved through interfaces.
   - **Example**: If `Car` implements both `ElectricVehicle` and `FuelVehicle` interfaces, it can inherit methods from both.

3. **Hierarchical Inheritance**: A single superclass is inherited by multiple subclasses.
   - **Example**: A `Vehicle` class can be inherited by `Car`, `Bike`, and `Truck`.

4. **Hybrid Inheritance**: A combination of multiple and hierarchical inheritance. This can be achieved using interfaces in Java.

---

### 6. Polymorphism

**Polymorphism** means "many forms" and refers to the ability of a single method or class to take on different forms. It allows objects of different classes to be treated as objects of a common superclass. Polymorphism enables the same method or operator to behave differently based on the object it is applied to.

There are two types of polymorphism:
- **Compile-time polymorphism (Static Polymorphism)**: Achieved through method overloading.
- **Run-time polymorphism (Dynamic Polymorphism)**: Achieved through method overriding.

**Example: Shapes**:

```java
class Shape {
    public void draw() {
        System.out.println("Drawing a shape");
    }
}

class Circle extends Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a circle");
    }
}

class Square extends Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a square");
    }
}

public class Main {
    public static void main(String[] args) {
        Shape shape = new Circle();
        shape.draw();  // Calls the draw method of the Circle class

        shape = new Square();
        shape.draw();  // Calls the draw method of the Square class
    }
}
```

**Explanation**:  
In this example, the `draw()` method is overridden in both the `Circle` and `Square` classes. At runtime, the JVM determines which `draw()` method to call based on the actual type of the object, not the reference type.

---

### 7. Types of Polymorphism

#### Static Polymorphism (Compile-time Polymorphism)
Static polymorphism is resolved during compile time and is achieved by method overloading. Overloading allows multiple methods with the same name but different parameter lists to exist within the same class.

**Example**:

```java
class MathUtils {
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        MathUtils math = new MathUtils();
        System.out.println(math.add(5, 10));       // Calls the int version
        System.out.println(math.add(5.5, 10.5));   // Calls the double version
    }
}
```

**Explanation**:  
In this example, the `add` method is overloaded to handle both `int` and `double` types. The compiler determines which method to call based on the argument types passed during compile time.

#### Dynamic Polymorphism (Run-time Polymorphism)
Dynamic polymorphism is resolved during runtime and is achieved through method overriding, where a subclass provides its specific implementation of a method defined in a superclass.

---

### 8. How Overriding Works

When a subclass overrides a method of its superclass, the subclass provides its specific implementation of that method. The JVM determines at runtime which method to invoke based on the actual object type.

**Example**:

```java
class Animal {
    public void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Dog();
        animal.sound();  // Calls the overridden method in the Dog class
    }
}
```

**Explanation**:  
## **Even though the reference variable is of type `Animal`,**

##  **the `sound()` method of `Dog` is called at runtime because the object is actually of type `Dog`.**

---

### 9. The `final` Keyword

The **`final` keyword** can be used in different contexts in Java:

- **Final variable**: A variable whose value cannot be changed once it is initialized.
- **Final method**: A method that cannot be overridden by subclasses.
- **Final class**: A class that cannot be subclassed.

**Example**:

```java
class Animal {
    final String species = "Canine"; // This value cannot be changed

    public final void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    // This method cannot be overridden
    // public void eat() { } // Error: Cannot override the final method from Animal
}
```

**Explanation**:  
The `species` variable is marked `final`, so it cannot be changed after initialization. The `eat()` method is also marked `final`, meaning it cannot be overridden in any subclass.

---

### 10. Encapsulation vs. Abstraction

- **Encapsulation** involves bundling the data (variables) and methods (functions) that operate on the data into a single unit, i.e., a class. It also involves restricting access to the class members through access modifiers like `private` or `protected`.

- **Abstraction** refers to hiding the implementation details from the user and showing only the necessary features of an object. This is typically achieved through abstract classes and interfaces.

**Example**:

```java
abstract class Vehicle {
    abstract void startEngine();
}

class Car extends Vehicle {
    public void startEngine() {
        System.out.println("Car engine started");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle vehicle = new Car();
        vehicle.startEngine(); // Only the behavior (method) is visible to the user
    }
}
```

**Explanation**:  
In the `Vehicle` class, the `startEngine()` method is abstract, and the subclass `Car` provides its implementation. The user only interacts with the `Vehicle` class, unaware of how the engine starts in the `Car` class.

---

### 11. Data Hiding

**Data Hiding** is achieved by using access modifiers (like `private`, `protected`, and `public`) to restrict direct access to the data in a class. This ensures that the internal representation of an object is hidden from outside manipulation.

By providing access through getter and setter methods, you can control the access and modification of the internal state.

---

## data hiding , encapsulation and data abstraction detailed notes in next chapter.



