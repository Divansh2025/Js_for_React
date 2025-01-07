---

# Chapter 4: **ES6 Classes, Prototypes, and Closures**

In this chapter, we will explore **ES6 Classes**, **Prototypes**, and **Closures**, which are foundational for understanding React concepts like components, state management, and lifecycle methods.

---

## 1. **ES6 Classes**

### What are ES6 Classes?

Classes in JavaScript (introduced in ES6) are **syntactic sugar** over the prototype-based inheritance model. They make it easier to define object blueprints and work with object-oriented programming principles like **inheritance**, **encapsulation**, and **polymorphism**.

### Defining a Class

#### Example 1: Basic Class Definition  
```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hi, my name is ${this.name}, and I am ${this.age} years old.`);
  }
}

// Creating an instance
const person1 = new Person("Alice", 25);
person1.greet(); // Output: Hi, my name is Alice, and I am 25 years old.
```

---

### Class Methods and Properties

1. **Constructor**: A special method for initializing objects.  
2. **Methods**: Functions defined inside a class.  
3. **Static Methods**: Methods that belong to the class itself, not instances.  

#### Example 2: Static Method
```javascript
class Calculator {
  static add(a, b) {
    return a + b;
  }
}

console.log(Calculator.add(5, 10)); // Output: 15
```

---

### Inheritance with Classes

Inheritance allows a class to derive properties and methods from another class using the `extends` keyword.

#### Example 3: Class Inheritance  
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const dog = new Dog("Buddy");
dog.speak(); // Output: Buddy barks.
```

---

### Getters and Setters  

Getters and setters allow you to control how object properties are accessed or modified.

#### Example 4: Getters and Setters  
```javascript
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  get area() {
    return this.width * this.height;
  }

  set width(value) {
    if (value <= 0) throw new Error("Width must be positive.");
    this._width = value;
  }

  get width() {
    return this._width;
  }
}

const rect = new Rectangle(5, 10);
console.log(rect.area); // Output: 50
rect.width = 20;
console.log(rect.area); // Output: 200
```

---

## 2. **Prototypes**

### What are Prototypes?

In JavaScript, every object has an internal property called `[[Prototype]]`, which links to another object. This enables **prototype chaining**, where properties and methods of one object can be accessed by others.

#### Example 1: Prototype Chain  
```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function () {
  console.log(`Hello, my name is ${this.name}.`);
};

const person1 = new Person("Alice");
person1.greet(); // Output: Hello, my name is Alice.
```

---

### Prototype Inheritance

Objects can inherit methods and properties from other objects via prototypes.

#### Example 2: Inheriting Methods Using Prototypes  
```javascript
function Animal(name) {
  this.name = name;
}

Animal.prototype.speak = function () {
  console.log(`${this.name} makes a sound.`);
};

function Dog(name) {
  Animal.call(this, name); // Call parent constructor
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.speak = function () {
  console.log(`${this.name} barks.`);
};

const dog = new Dog("Buddy");
dog.speak(); // Output: Buddy barks.
```

---

## 3. **Closures**

### What is a Closure?

A **closure** is a function that "remembers" its outer variables, even after the outer function has executed. Closures are critical for understanding concepts like **state**, **encapsulation**, and **currying** in React.

---

### Example 1: Simple Closure  
```javascript
function outer() {
  let count = 0; // Enclosed variable
  return function inner() {
    count++;
    console.log(count);
  };
}

const counter = outer();
counter(); // Output: 1
counter(); // Output: 2
```

---

### Example 2: Closure for Encapsulation

Closures are often used to **encapsulate private variables**.

```javascript
function Counter() {
  let count = 0;

  return {
    increment() {
      count++;
      console.log(count);
    },
    decrement() {
      count--;
      console.log(count);
    },
  };
}

const counter = Counter();
counter.increment(); // Output: 1
counter.increment(); // Output: 2
counter.decrement(); // Output: 1
```

---

### Example 3: Real-World Use Case: Event Listeners  

```javascript
function createButton(label) {
  let clickCount = 0;

  const button = document.createElement("button");
  button.innerText = label;

  button.addEventListener("click", () => {
    clickCount++;
    console.log(`Button clicked ${clickCount} times.`);
  });

  document.body.appendChild(button);
}

createButton("Click Me!");
// Clicking the button will increment and log the count
```

---

## Combining ES6 Classes, Prototypes, and Closures

#### Example: Counter Class with Closures and Prototypes  

```javascript
class Counter {
  constructor() {
    this.count = 0;
  }

  increment() {
    this.count++;
    console.log(`Count: ${this.count}`);
  }

  reset() {
    this.count = 0;
    console.log("Counter reset.");
  }
}

Counter.prototype.decrement = function () {
  this.count--;
  console.log(`Count: ${this.count}`);
};

const counter = new Counter();
counter.increment(); // Output: Count: 1
counter.increment(); // Output: Count: 2
counter.decrement(); // Output: Count: 1
counter.reset();     // Output: Counter reset.
```

---

### Key Takeaways:
1. **ES6 Classes**: Use for creating object blueprints and managing inheritance in an easy-to-read syntax.
2. **Prototypes**: Enable property and method sharing between objects for memory efficiency.
3. **Closures**: Critical for encapsulating state and creating reusable, self-contained logic.

 Now we’ll move on to **Understanding Modules, Imports/Exports, and Advanced Array Methods**, which are essential for React development.