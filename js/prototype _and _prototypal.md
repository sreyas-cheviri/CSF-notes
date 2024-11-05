# [yt-video-proto](https://www.youtube.com/watch?v=wstwjQ1yqWQ)


In JavaScript, **prototypes** and **prototypal inheritance** are fundamental concepts that are important to understand how objects and inheritance work in the language.

### 1. **Prototype**

Every JavaScript object has a hidden internal property called `[[Prototype]]`. This prototype property is a reference to another object, and it is used to look up properties and methods that are not found directly on the object itself.

- When you try to access a property or method of an object, JavaScript first looks at the object itself.
- If it doesn't find the property, it looks at the object's prototype (the object referenced by `[[Prototype]]`).
- If the property is still not found, it looks at the prototype of the prototype, and so on, until it reaches the end (usually `null`).

This is called **prototype chain**.

For example:

```javascript
const car = {
  brand: "Toyota",
  drive() {
    console.log("Driving...");
  }
};

const myCar = Object.create(car); // Creates a new object with car as the prototype

console.log(myCar.brand); // "Toyota" - Inherited from the prototype
myCar.drive(); // "Driving..." - Inherited from the prototype
```

In this example:
- `myCar` does not have the `brand` or `drive` property directly, but because `myCar`'s prototype is `car`, it can access those properties.

### 2. **Prototypal Inheritance**

Prototypal inheritance is the way that JavaScript objects can inherit properties and methods from other objects through their prototype chain.

- When you create a new object, you can specify an object that it inherits from using `Object.create()`.
- If you don't specify, the object will inherit from `Object.prototype` by default, which provides basic methods like `toString()` and `hasOwnProperty()`.

For example:

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name}`);
};

const person1 = new Person("Alice");
person1.sayHello(); // "Hello, my name is Alice"
```

Here:
- `Person` is a constructor function, and its prototype (`Person.prototype`) has a method `sayHello`.
- All instances of `Person` (like `person1`) can access the `sayHello` method because it is inherited from the prototype.

### Key Concepts:

- **Prototype**: An internal object that provides properties and methods to other objects.
- **Prototypal Inheritance**: A mechanism where an object can inherit properties and methods from another object, forming a chain of prototypes.

In summary, the prototype is what allows objects to "inherit" functionality in JavaScript. It makes the language powerful and flexible because objects can share methods without directly copying them.