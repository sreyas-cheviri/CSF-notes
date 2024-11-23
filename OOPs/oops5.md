
---

### Access Modifiers in Java

-----
![access modifiers](../assets/Screenshot%202024-11-11%20202450.png)
----

### interview answer : 
Access modifiers in Java are keywords that set the accessibility or scope of classes, constructors, methods, and variables. They control where these elements can be accessed from, helping to implement encapsulation and data hiding


----


1. **Private**: 
   - Accessible only within the class in which it is declared.
   - Not visible to any other class, even within the same package.
   - **Example**:
     ```java
     public class Example {
         private int data = 10;

         private void display() {
             System.out.println("Data: " + data);
         }
     }
     ```

2. **Public**: 
   - Accessible from any other class in any package.
   - Widely used for methods or classes meant to be used across various parts of an application.
   - **Example**:
     ```java
     public class Example {
         public int data = 10;

         public void display() {
             System.out.println("Data: " + data);
         }
     }
     ```

3. **Protected**: 
   - Accessible within the same package and subclasses in different packages.
   - Ideal for allowing controlled access to methods or variables.
   - **Example**:
     ```java
     public class Example {
         protected int data = 10;

         protected void display() {
             System.out.println("Data: " + data);
         }
     }
     ```

4. **Default (Package-Private)**:
   - When no modifier is specified, it is accessible only within the same package.
   - **Example**:
     ```java
     class Example {
         int data = 10;

         void display() {
             System.out.println("Data: " + data);
         }
     }
     ```

---

### When to Use Each Modifier

- **Private**: When you want to restrict access strictly to the class itself.
- **Public**: When you need to provide access to other classes and packages without restrictions.
- **Protected**: When you want controlled access for subclasses, potentially across packages.
- **Default**: When you need access within the same package but not outside it.

### Important Note on the Protected Modifier
The protected modifier is often used in inheritance to give subclasses access to superclass members while restricting visibility outside the package, balancing encapsulation and inheritance.

---

### Packages in Java

- Packages group related classes and interfaces, preventing name conflicts and providing access control.
  
#### In-built Java Packages

1. **java.lang**:
   - Automatically imported by Java; contains fundamental classes.
   - **Examples**: `Object`, `String`, `Math`, `System`.

2. **java.io**:
   - Provides input and output functionality.
   - **Example**: `File`, `InputStream`, `OutputStream`.

3. **java.util**:
   - Contains utility classes like collections and date-time handling.
   - **Examples**: `ArrayList`, `HashMap`, `Date`.

4. **java.applet**:
   - For creating applets that can be embedded in web pages (less commonly used now).
   - **Examples**: `Applet`, `AudioClip`.

5. **java.awt**:
   - Used for creating graphical user interface (GUI) applications.
   - **Examples**: `Button`, `Label`, `Frame`.

6. **java.net**:
   - Provides classes for network operations.
   - **Examples**: `Socket`, `URL`, `URLConnection`.

---

### The Object Class

The `Object` class is the root of the Java class hierarchy. Every class implicitly inherits from `Object`.

#### Key Methods of Object Class

1. **hashCode()**:
   - Returns an integer representing the memory address of the object.
   - It’s essential when using objects in hash-based collections like `HashMap`.
   - **Example**:
     ```java
     Object obj = new Object();
     System.out.println(obj.hashCode());
     ```

2. **equals()**:
   - Compares two objects for equality.
   - By default, it compares memory addresses, but can be overridden for content comparison.
   - **Example**:
     ```java
     String str1 = "hello";
     String str2 = "hello";
     System.out.println(str1.equals(str2)); // true
     ```

3. **instanceof Operator**:
   - Checks if an object is an instance of a specific class or interface.
   - **Example**:
     ```java
     String text = "hello";
     System.out.println(text instanceof String); // true
     ```

4. **getClass()**:
   - Returns the runtime class of an object.
   - Useful in reflection.
   - **Example**:
     ```java
     Object obj = new Object();
     System.out.println(obj.getClass().getName());
     ```

---
