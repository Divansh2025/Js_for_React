---

# Chapter 2: Advanced JavaScript Concepts for React  

In this chapter, we will cover some **advanced and modern JavaScript features** that are frequently used in React:  
1. Destructuring  
2. Spread and Rest Operators  
3. Default Parameters  
4. Object and Array Methods  
5. Modules and Imports  

---

## 1. Destructuring  
Destructuring allows you to unpack values from arrays or properties from objects into distinct variables.  

### **Array Destructuring**:  
```javascript
const scores = [85, 90, 78];

// Extract values into variables
const [first, second, third] = scores;
console.log(first, second, third); // Output: 85, 90, 78

// Skip values
const [topScore, , thirdScore] = scores;
console.log(topScore, thirdScore); // Output: 85, 78
```

### **Object Destructuring**:  
```javascript
const user = { name: "Alice", age: 25, role: "Admin" };

// Extract properties into variables
const { name, age } = user;
console.log(name, age); // Output: Alice, 25

// Rename variables
const { role: userRole } = user;
console.log(userRole); // Output: Admin
```

---

## 2. Spread and Rest Operators  
The `...` syntax serves two purposes:  
1. **Spread**: Expands an array/object.  
2. **Rest**: Collects the remaining elements into an array.  

### **Spread Operator**:  
```javascript
const scores = [85, 90, 78];
const newScores = [...scores, 95]; // Adds 95 to the end
console.log(newScores); // Output: [85, 90, 78, 95]

const user = { name: "Alice", age: 25 };
const updatedUser = { ...user, role: "Admin" }; // Add role
console.log(updatedUser); // Output: { name: "Alice", age: 25, role: "Admin" }
```

### **Rest Operator**:  
```javascript
const [first, ...rest] = [85, 90, 78, 95];
console.log(first); // Output: 85
console.log(rest);  // Output: [90, 78, 95]

function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}
console.log(sum(1, 2, 3)); // Output: 6
```

---

## 3. Default Parameters  
Default parameters ensure a fallback value when no argument is provided.  

### Example:  
```javascript
function greet(name = "Guest") {
  return `Hello, ${name}!`;
}
console.log(greet());        // Output: Hello, Guest!
console.log(greet("Alice")); // Output: Hello, Alice!
```

---

## 4. Object and Array Methods  
React often deals with array and object manipulations. Here are some commonly used methods:

### **Array Methods**:  
1. **map**: Transforms array elements.  
2. **filter**: Filters elements based on a condition.  
3. **reduce**: Reduces the array to a single value.  

### Example:  
```javascript
const numbers = [1, 2, 3, 4, 5];

// map: Multiply each number by 2
const doubled = numbers.map((num) => num * 2);
console.log(doubled); // Output: [2, 4, 6, 8, 10]

// filter: Get even numbers
const evens = numbers.filter((num) => num % 2 === 0);
console.log(evens); // Output: [2, 4]

// reduce: Calculate the sum
const total = numbers.reduce((sum, num) => sum + num, 0);
console.log(total); // Output: 15
```

### **Object Methods**:  
1. **Object.keys**: Gets all keys.  
2. **Object.values**: Gets all values.  
3. **Object.entries**: Gets key-value pairs.  

### Example:  
```javascript
const user = { name: "Alice", age: 25, role: "Admin" };

console.log(Object.keys(user));   // Output: ["name", "age", "role"]
console.log(Object.values(user)); // Output: ["Alice", 25, "Admin"]
console.log(Object.entries(user)); // Output: [["name", "Alice"], ["age", 25], ["role", "Admin"]]
```

---

## 5. Modules and Imports  
React uses modular code. JavaScript supports importing/exporting functions, objects, and more.  

### Example:  
**File: utils.js**  
```javascript
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
export default (a, b) => a * b; // Default export
```

**File: main.js**  
```javascript
import multiply, { add, subtract } from "./utils.js";

console.log(add(5, 3));        // Output: 8
console.log(subtract(5, 3));   // Output: 2
console.log(multiply(5, 3));   // Output: 15
```

---

 Now we'll move on to **Promises, Async/Await, and Event Handling**, which are crucial for React applications. 