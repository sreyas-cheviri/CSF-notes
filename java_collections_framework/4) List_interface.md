
# List Interface in Java

## Overview
The `List` interface is part of the Java Collection Framework and represents an ordered collection (also known as a sequence). It allows duplicate elements and maintains the insertion order, enabling access to elements by their position (index).

## Key Characteristics
- **Ordered Collection**: Elements are stored in a specific sequence, and you can access them by their index.
- **Allows Duplicates**: You can add the same element multiple times.
- **Dynamic Size**: Unlike arrays, lists can grow and shrink in size as elements are added or removed.

## Key Methods
The `List` interface extends the `Collection` interface and includes several additional methods specifically for managing list elements:

### 1. **`void add(int index, E element)`**
- Inserts the specified element at the specified position in the list.
- Shifts the element currently at that position (if any) and any subsequent elements to the right (adds one to their indices).

**Example**:
```java
List<String> list = new ArrayList<>();
list.add("A");
list.add("B");
list.add(1, "C"); // Inserts "C" at index 1
System.out.println(list); // Outputs: [A, C, B]
```

### 2. **`E get(int index)`**
Returns the element at the specified position in the list.

**Example**:
```java
Copy code
String element = list.get(1); // Gets the element at index 1
System.out.println(element); // Outputs: C
```

### 3. **`int size()`**
Returns the number of elements in the list.

**Example**:
```java
int size = list.size(); // Gets the size of the list
System.out.println(size); // Outputs: 3
```
### 4. **`boolean remove(int index)`**

Removes the element at the specified position in the list.

**Example**:
```java
list.remove(1); // Removes the element at index 1 (C)
System.out.println(list); // Outputs: [A, B]
```
### 5. **`int indexOf(Object o)`**
Returns the index of the first occurrence of the specified element in the list, or -1 if this list does not contain the element.

**Example**:
```java
int index = list.indexOf("B"); // Finds the index of "B"
System.out.println(index); // Outputs: 1
```

### 6. **`boolean contains(Object o)`**
Returns true if this list contains the specified element.

Example:

```java
boolean contains = list.contains("A"); // Checks if "A" is in the list
System.out.println(contains); // Outputs: true
```
## Common Implementations of List Interface

1)  ### ArrayList

- Resizable array implementation of the List interface.
- Allows random access to elements due to its underlying array structure.
- Best for scenarios where you need fast access and iteration but fewer insertions/removals.

Example:

```java

List<String> arrayList = new ArrayList<>();
arrayList.add("A");
arrayList.add("B");
arrayList.add("C");
System.out.println(arrayList); 
// Outputs: [A, B, C]
```
2) ### LinkedList

- Doubly-linked list implementation of the List interface.

- Better for scenarios where you need frequent insertions and deletions at any position in the list.

- Has a higher memory overhead due to storing references for both the next and previous elements.

Example:

```java

List<String> linkedList = new LinkedList<>();
linkedList.add("A");
linkedList.add("B");
linkedList.addFirst("C"); // Adds "C" at the beginning
System.out.println(linkedList); // Outputs: [C, A, B]
```
3) ### Vector

- Synchronized (thread-safe) dynamic array implementation of the List interface.
- Similar to ArrayList, but it is synchronized, making it slower than ArrayList in single-threaded scenarios.

Example:

```java

List<String> vector = new Vector<>();
vector.add("A");
vector.add("B");
System.out.println(vector); // Outputs: [A, B]
```
# Summary of Differences
- ArrayList: Fast access, allows null values, not synchronized.
- LinkedList: Good for frequent insertions/deletions, slower access time.
- Vector: Synchronized, slower due to synchronization overhead, allows null values.

# Conclusion
The List interface is a crucial part of the Java Collection Framework, offering a flexible way to work with ordered collections. Understanding the different implementations (ArrayList, LinkedList, Vector) helps choose the right one based on performance requirements and usage patterns. 