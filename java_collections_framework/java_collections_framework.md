# JAVA collections framework notes

![JCF-flowchart](https://miro.medium.com/v2/resize:fit:828/format:webp/1*qgcrVwo8qzF4muOQ-kKB8A.jpeg)



## Java Collection Framework - Interfaces and Relationships

## Core Interfaces and Their Relationships

### 1. Iterable Interface
- The root interface for all collections.
- Allows iteration over elements.

### 2. Collection Interface
- **Extends**: `Iterable<T>`
- The base interface for most collection types.

### 3. List Interface
- **Extends**: `Collection<E>`
- Represents an ordered collection (sequence).
- Allows duplicate elements.
- **Key Implementations**:
  - `ArrayList`
  - `LinkedList`
  - `Vector`
  - `Stack`

### 4. Set Interface
- **Extends**: `Collection<E>`
- Represents a collection that does not allow duplicate elements.
- **Key Implementations**:
  - `HashSet`
  - `LinkedHashSet`
  - `TreeSet`

### 5. Map Interface
- **Does Not Extend Collection**
- Represents a collection of key-value pairs.
- Keys must be unique.
- **Key Implementations**:
  - `HashMap`
  - `LinkedHashMap`
  - `TreeMap`

### 6. Queue Interface
- **Extends**: `Collection<E>`
- Represents a collection designed for holding elements prior to processing.
- Typically follows FIFO (first-in-first-out) order.
- **Key Implementations**:
  - `LinkedList` *this is also Implementation of List*
  - `PriorityQueue`

## Summary of Relationships

- **Iterable** → **Collection** → **List**
- **Iterable** → **Collection** → **Set**
- **Iterable** → **Collection** → **Queue**
- **Map** (does not extend `Collection` but is part of the framework)



