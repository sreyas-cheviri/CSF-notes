In Java, `final`, `finally`, and `finalize` serve different purposes and have unique meanings in specific contexts. Here’s a detailed breakdown:

### 1. `final`
The `final` keyword can be used with **variables**, **methods**, and **classes**. 

#### Usage:
- **Final Variables**: Once a variable is declared as `final`, its value cannot be changed once assigned. This makes the variable a constant.
  ```java
  final int MAX_VALUE = 10;
  // MAX_VALUE = 15; // This will give an error
  ```
  
- **Final Methods**: A method marked as `final` cannot be overridden by subclasses. This is useful when you want to ensure that the implementation remains the same in all subclasses.
  ```java
  public class Parent {
      public final void display() {
          System.out.println("This is a final method.");
      }
  }
  
  public class Child extends Parent {
      // Cannot override `display()` method here
  }
  ```
  
- **Final Classes**: A class declared as `final` cannot be subclassed. This is often done to prevent inheritance, particularly if the class contains sensitive or critical code that should not be altered.
  ```java
  public final class FinalClass {
      // Class code
  }
  
  // class SubClass extends FinalClass {} // This will give an error
  ```

### 2. `finally`
The `finally` block is used with **try-catch** statements to ensure that certain code is executed regardless of whether an exception is thrown or not. This is useful for cleanup operations, such as closing files or releasing resources.

#### Usage:
- **Try-Finally**: When no exception handling is needed but cleanup is required.
  ```java
  try {
      // Code that may throw an exception
  } finally {
      // Cleanup code that executes whether an exception occurs or not
  }
  ```
  
- **Try-Catch-Finally**: When exception handling and cleanup are both required.
  ```java
  try {
      // Code that may throw an exception
  } catch (Exception e) {
      // Exception handling code
  } finally {
      // Cleanup code that executes after the try-catch block
  }
  ```

> **Note**: Even if a `return` statement is used within the `try` or `catch` block, the `finally` block will still execute before the method exits.

### 3. `finalize`
The `finalize` method is associated with **garbage collection** and is used to perform cleanup operations before an object is destroyed. The `finalize()` method is called by the garbage collector when it determines that there are no more references to an object. This method is defined in the `Object` class and can be overridden to release resources like file handles or database connections.

#### Usage:
```java
@Override
protected void finalize() throws Throwable {
    try {
        // Resource release code
    } finally {
        super.finalize();
    }
}
```

> **Note**: `finalize()` is now deprecated in Java and is generally discouraged. The garbage collector might not call `finalize()` on an object, so relying on it for cleanup is unreliable. Instead, you should use the `try-with-resources` statement or `close()` methods.

### Summary Table

| Keyword    | Purpose                                                         | Usage Example |
|------------|-----------------------------------------------------------------|---------------|
| `final`    | Used to make variables constant, prevent method overriding, and prevent inheritance of classes. | `final int x = 5;` |
| `finally`  | Used in try-catch blocks to execute code regardless of exception outcome. | `finally { /* cleanup */ }` |
| `finalize` | Called by the garbage collector before object destruction (not reliable and deprecated). | `protected void finalize() { /* cleanup */ }` |

These keywords serve different roles in Java, helping enforce immutability (`final`), guarantee code execution (`finally`), and perform cleanup (`finalize`).