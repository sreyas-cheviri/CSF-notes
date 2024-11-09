
---

### **1. Example of a Class**
   - A **class** in Java is a blueprint for creating objects. It defines the attributes and behaviors (methods) that the objects created from the class will have.
   - **Example**:
     ```java
     class Car {
         String color;
         String model;

         void drive() {
             System.out.println("The car is driving.");
         }
     }
     ```
   - Here, `Car` is a class with attributes `color` and `model`, and a behavior `drive()`.

---

### **2. Java Objects**
   - **Objects** are instances of classes. When a class is defined, no memory is allocated until an object of that class is created.
   - Each object has unique attribute values, even if they are created from the same class.
   - **Example**:
     ```java
     Car myCar = new Car(); // Object myCar of type Car
     myCar.color = "Red";
     myCar.model = "Sedan";
     ```

---

### **3. Class vs Object**
   - **Class**: A blueprint or template that defines the structure (attributes) and behavior (methods) that objects will have.
   - **Object**: A concrete instance of a class with specific values for its attributes.

---

### **4. Properties of an Object**
   - **State**: Defined by the values of the object’s attributes (instance variables).
   - **Behavior**: Defined by the object’s methods, which can manipulate its state.
   - **Identity**: Each object has a unique reference, even if multiple objects have the same state.

---

### **5. Objects Introduction**
   - An object is a key concept in Java. It represents an instance of a class and contains its own state and behavior.
   - Objects are created using the `new` keyword followed by the class constructor.

---

### **6. How to Access Instance Variables?**
   - You can access an object’s instance variables using the dot (`.`) operator.
   - **Example**:
     ```java
     Car myCar = new Car();
     myCar.color = "Blue"; // Accessing and setting the color property
     System.out.println(myCar.color); // Output: Blue
     ```

---

### **7. How to Create Objects?**
   - Objects are created using the `new` keyword followed by a call to the class constructor.
   - **Example**:
     ```java
     Car myCar = new Car(); // Creates a new Car object
     ```

---

### **8. Dynamic Memory Allocation**
   - In Java, memory for objects is dynamically allocated on the **heap** when the `new` keyword is used.
   - Each object has a unique memory space on the heap, separate from other objects, even if they are of the same class.

---

### **9. How to Manipulate Objects?**
   - You can manipulate an object’s state by modifying its instance variables and calling its methods.
   - **Example**:
     ```java
     myCar.color = "Green"; // Modifying color attribute
     myCar.drive(); // Calls the drive method
     ```

---

### **10. Java Constructors**
   - A **constructor** is a special method used to initialize objects. It has the same name as the class and no return type.
   - **Default Constructor**: If no constructor is defined, Java automatically provides a no-argument default constructor.

---

### **11. By Default Constructor**
   - Java provides a default constructor if no other constructor is defined. This constructor initializes the object’s variables to default values (0, `null`, etc.).
   - **Example**:
     ```java
     class Car {
         Car() {
             System.out.println("Default constructor called");
         }
     }

     Car myCar = new Car(); // Default constructor called automatically
     ```

---

### **12. Creating Constructors**
   - You can create a constructor to initialize object attributes at the time of creation.
   - **Example**:
     ```java
     class Car {
         String color;

         Car(String c) {
             color = c; // Parameterized constructor
         }
     }

     Car myCar = new Car("Red"); // Creates a Car object with color "Red"
     ```

---

### **13. "this" Keyword**
   - The `this` keyword is used to refer to the current object. It helps avoid confusion between instance variables and parameters.
   - **Example**:
     ```java
     class Car {
         String color;

         Car(String color) {
             this.color = color; // "this.color" refers to the instance variable
         }
     }
     ```

---

### **14. Constructor Overloading**
   - Java supports multiple constructors with different parameter lists in the same class. This is known as **constructor overloading**.
   - **Example**:
     ```java
     class Car {
         String color;
         String model;

         Car() {
             this.color = "Default Color";
         }

         Car(String color, String model) {
             this.color = color;
             this.model = model;
         }
     }

     Car myCar1 = new Car(); // Calls default constructor
     Car myCar2 = new Car("Blue", "Sedan"); // Calls parameterized constructor
     ```

---

### **15. Calling a Constructor from Another Constructor**
   - A constructor can call another constructor within the same class using `this()`. This is useful for code reuse.
   - **Example**:
     ```java
     class Car {
         String color;

         Car() {
             this("Red"); // Calls the parameterized constructor
         }

         Car(String color) {
             this.color = color;
         }
     }
     ```

---

### **16. Why We Don’t Use "new" Keyword for Primitive Data Types?**
   - Primitive data types (`int`, `float`, `char`, etc.) are stored on the stack and don’t require dynamic memory allocation.
   - Using `new` for primitives would consume extra memory and decrease performance.

---

### **17. Memory Allocation of "new" Keyword**
   - The `new` keyword allocates memory for an object on the heap. A reference to this object is stored in stack memory, which the variable holds.
   - **Example**:
     ```java
     Car myCar = new Car(); // myCar is a reference on the stack, pointing to a Car object on the heap
     ```

---

### **18. Wrapper Classes**
   - Wrapper classes allow primitive types to be treated as objects. Examples include `Integer` (for `int`), `Double` (for `double`), etc.
   - They are often used in collections, as collections in Java can only hold objects, not primitives.
   - **Example**:
     ```java
     Integer num = Integer.valueOf(10); // Wraps an int in an Integer object
     ```

---

### **19. "final" Keyword**
   - The `final` keyword is used to define constants, prevent inheritance, and make variables immutable.
   - **Usage**:
     - **final variable**: Can’t be reassigned.
     - **final method**: Can’t be overridden in subclasses.
     - **final class**: Can’t be extended (e.g., `String` class).
   - **Example**:
     ```java
     final int MAX_SPEED = 120; // final variable

     class Vehicle {
         final void display() { // final method
             System.out.println("Vehicle Display");
         }
     }

     final class Car { // final class
         // ...
     }
     ```

---

### **20. Garbage Collection**
   - Java’s garbage collector automatically deallocates memory for objects that are no longer referenced, helping manage memory efficiently.
   - When an object is eligible for garbage collection:
     - **Nullifying the reference**: `myCar = null;`
     - **Reassigning the reference**: `myCar = new Car();` (the previous `Car` object becomes eligible for garbage collection).
   - **Example**:
     ```java
     Car myCar = new Car();
     myCar = null; // Now eligible for garbage collection
     ```

---

