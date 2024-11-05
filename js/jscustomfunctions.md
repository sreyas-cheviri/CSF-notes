Here’s how you can create your own `reduce`, `filter`, and `map` functions in JavaScript.

### 1. `myReduce` Function

The `reduce` function iterates over an array and accumulates a result based on a callback function.

```javascript
Array.prototype.myReduce = function(callback, initialValue) {
    let accumulator = initialValue !== undefined ? initialValue : this[0];
    let startIndex = initialValue !== undefined ? 0 : 1;

    for (let i = startIndex; i < this.length; i++) {
        accumulator = callback(accumulator, this[i], i, this);
    }

    return accumulator;
};
```

**Usage:**

```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.myReduce((acc, curr) => acc + curr, 0);
console.log(sum); // Output: 10
```

### 2. `myFilter` Function

The `filter` function returns a new array with all elements that pass the test implemented by the callback function.

```javascript
Array.prototype.myFilter = function(callback) {
    const result = [];

    for (let i = 0; i < this.length; i++) {
        if (callback(this[i], i, this)) {
            result.push(this[i]);
        }
    }

    return result;
};
```

**Usage:**

```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.myFilter(num => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4]
```

### 3. `myMap` Function

The `map` function creates a new array populated with the results of calling a provided function on every element in the array.

```javascript
Array.prototype.myMap = function(callback) {
    const result = [];

    for (let i = 0; i < this.length; i++) {
        result.push(callback(this[i], i, this));
    }

    return result;
};
```

**Usage:**

```javascript
const numbers = [1, 2, 3, 4];
const doubled = numbers.myMap(num => num * 2);
console.log(doubled); // Output: [2, 4, 6, 8]
```

### Explanation

- **`myReduce`**: Iterates over the array, accumulating a value with each iteration, using the provided callback function.
- **`myFilter`**: Creates a new array with elements that return `true` for the given test in the callback.
- **`myMap`**: Maps each element in the array to a new value based on the callback’s return value. 

These functions work similarly to their native JavaScript counterparts and will provide you with a good understanding of how these methods are implemented under the hood.



Certainly! Let's go through each function (`reduce`, `filter`, and `map`) step-by-step to understand how they work and how we implement them manually.

---

### 1. `myReduce` Function

The `reduce` function is a powerful tool for accumulating a result from an array. It takes a callback function and an optional initial value. The callback is applied to each element in the array, progressively "reducing" the array into a single accumulated result.

Here’s how we can implement our own version of `reduce`, called `myReduce`:

```javascript
Array.prototype.myReduce = function(callback, initialValue) {
    // Step 1: Determine the initial value of the accumulator
    let accumulator = initialValue !== undefined ? initialValue : this[0];

    // Step 2: Determine where to start the loop
    let startIndex = initialValue !== undefined ? 0 : 1;

    // Step 3: Iterate over the array
    for (let i = startIndex; i < this.length; i++) {
        // Apply the callback function to update the accumulator
        accumulator = callback(accumulator, this[i], i, this);
    }

    // Step 4: Return the final accumulated result
    return accumulator;
};
```

#### Detailed Steps:
- **Step 1**: If an `initialValue` is provided, we use it as the starting value for the `accumulator`. Otherwise, we take the first element of the array (`this[0]`) as the initial accumulator.
- **Step 2**: We set `startIndex` to `0` if an `initialValue` is provided (because we start at the beginning of the array), otherwise `1` (skipping the first element because it’s already the `accumulator`).
- **Step 3**: We loop through the array from `startIndex` to the end, applying the callback function to each element. The callback takes four parameters:
  - `accumulator`: The accumulated result so far.
  - `this[i]`: The current element in the array.
  - `i`: The current index.
  - `this`: The original array.
- **Step 4**: After the loop, the `accumulator` will hold the final result, which we return.

**Example Usage**:

```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.myReduce((acc, curr) => acc + curr, 0);
console.log(sum); // Output: 10
```

In this example, `myReduce` starts with `0` as `initialValue` and then adds each number to `acc`, giving `1 + 2 + 3 + 4 = 10`.

---

### 2. `myFilter` Function

The `filter` function is used to create a new array with only the elements that pass a specified condition. The callback function is used to test each element; if it returns `true`, the element is included in the new array.

Here’s how we can implement `myFilter`:

```javascript
Array.prototype.myFilter = function(callback) {
    const result = []; // Array to hold filtered values

    for (let i = 0; i < this.length; i++) {
        // If the callback returns true, add the element to the result array
        if (callback(this[i], i, this)) {
            result.push(this[i]);
        }
    }

    return result; // Return the filtered array
};
```

#### Detailed Steps:
- **Step 1**: We initialize an empty array `result` to store elements that pass the test.
- **Step 2**: We loop over each element of the array.
  - If `callback(this[i], i, this)` returns `true`, we add `this[i]` (the current element) to `result`.
  - The callback receives:
    - `this[i]`: The current element.
    - `i`: The current index.
    - `this`: The original array.
- **Step 3**: After the loop, we return the `result` array containing only the elements that passed the test.

**Example Usage**:

```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.myFilter(num => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4]
```

Here, `myFilter` checks each element of `numbers` and includes only those where `num % 2 === 0` (even numbers), resulting in `[2, 4]`.

---

### 3. `myMap` Function

The `map` function is used to create a new array with each element transformed by the callback function. `map` applies the callback to every element and stores the results in a new array.

Here’s our custom `myMap` function:

```javascript
Array.prototype.myMap = function(callback) {
    const result = []; // Array to hold transformed values

    for (let i = 0; i < this.length; i++) {
        // Apply the callback function and push the result to the new array
        result.push(callback(this[i], i, this));
    }

    return result; // Return the new array with mapped values
};
```

#### Detailed Steps:
- **Step 1**: We initialize an empty array `result` to store the transformed values.
- **Step 2**: We loop over each element of the array, applying `callback` to each element.
  - `callback(this[i], i, this)` is called with:
    - `this[i]`: The current element.
    - `i`: The current index.
    - `this`: The original array.
  - The result of `callback` is then pushed into `result`.
- **Step 3**: After the loop, we return the `result` array containing the transformed elements.

**Example Usage**:

```javascript
const numbers = [1, 2, 3, 4];
const doubled = numbers.myMap(num => num * 2);
console.log(doubled); // Output: [2, 4, 6, 8]
```

Here, `myMap` multiplies each element of `numbers` by 2, resulting in a new array `[2, 4, 6, 8]`.

---

### Summary

- **`myReduce`**: Reduces an array to a single value by accumulating results based on a callback function.
- **`myFilter`**: Creates a new array by selecting elements that pass a condition specified in the callback.
- **`myMap`**: Transforms each element in an array based on a callback function, returning a new array with the transformed elements.

These custom implementations mimic the behavior of JavaScript’s built-in `reduce`, `filter`, and `map` methods, providing a good understanding of how each method works internally.