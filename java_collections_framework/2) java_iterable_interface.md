
# Iterable Interface in Java

## Overview
The `Iterable` interface is the root interface for all collection classes in the Java Collection Framework. It allows an object to be the target of the enhanced `for` loop, enabling easy traversal of its elements.

## Key Characteristics
- **Single Method**: The `Iterable` interface contains a single abstract method, which needs to be implemented by any class that implements this interface.
- **Support for Iteration**: Provides a standard way to access elements of a collection one at a time without exposing the underlying data structure.

## Key Method
The `Iterable` interface has one main method:

### 1. **`Iterator<T> iterator()`**
- Returns an `Iterator` for the elements in the collection.
- Allows traversal of the collection using the `Iterator` interface methods (`hasNext()`, `next()`, and `remove()`).

**Example**:
```java
public class MyCollection implements Iterable<String> {
    private String[] elements = {"A", "B", "C"};

    @Override
    public Iterator<String> iterator() {
        return new Iterator<String>() {
            private int index = 0;

            @Override
            public boolean hasNext() {
                return index < elements.length;
            }

            @Override
            public String next() {
                return elements[index++];
            }

            @Override
            public void remove() {
                throw new UnsupportedOperationException("Remove not supported.");
            }
        };
    }
}
```
Here's an example demonstrating how to use the Iterable interface with a custom collection class:


```java
import java.util.Iterator;

public class MyIterableCollection implements Iterable<String> {
    private String[] items = {"One", "Two", "Three"};

    @Override
    public Iterator<String> iterator() {
        return new Iterator<String>() {
            private int current = 0;

            @Override
            public boolean hasNext() {
                return current < items.length;
            }

            @Override
            public String next() {
                return items[current++];
            }

            @Override
            public void remove() {
                throw new UnsupportedOperationException("Remove operation is not supported.");
            }
        };
    }

    public static void main(String[] args) {
        MyIterableCollection collection = new MyIterableCollection();
        for (String item : collection) {
            System.out.println(item);
        }
    }
}
```
### When to Use Iterable:

- When you want to allow objects to be iterable in a for-each loop.

- When creating custom collection classes that need to support iteration.

---

### Comparison with Other Interfaces

- Iterator: While Iterable provides the ability to obtain an iterator, the Iterator interface itself allows for element traversal and manipulation.

- Collection: The Collection interface extends Iterable and adds more functionality, such as adding and removing elements.

## Conclusion

The Iterable interface is a fundamental building block in the Java Collection Framework, providing a mechanism to traverse elements in a collection. Implementing this interface is essential for creating custom collection classes that can be easily used in enhanced for-loops. 