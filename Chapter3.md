---

# Chapter 3: Promises, Async/Await, and Event Handling

In this chapter, we will go **deeper into Promises, Async/Await, and Event Handling** with detailed examples and outputs to ensure complete understanding.

---

## 1. **Promises**

### What are Promises?

A Promise is a JavaScript object that represents the **future completion or failure of an asynchronous task**. It allows you to attach **callbacks** for handling success (`.then`) or failure (`.catch`).

#### **Promise Lifecycle**:
1. **Pending**: Initial state, neither fulfilled nor rejected.  
2. **Fulfilled**: Operation completed successfully, and the result is available.  
3. **Rejected**: Operation failed, and an error is available.

### Creating and Using Promises

#### Example 1: Basic Promise  
```javascript
const myPromise = new Promise((resolve, reject) => {
  let success = true; // Simulate success or failure
  if (success) {
    resolve("Promise fulfilled!");
  } else {
    reject("Promise rejected!");
  }
});

myPromise
  .then((message) => console.log(message)) // Output: Promise fulfilled!
  .catch((error) => console.error(error));
```

#### Example 2: Simulating Asynchronous Behavior
```javascript
const fetchData = () => {
  return new Promise((resolve, reject) => {
    console.log("Fetching data...");
    setTimeout(() => {
      const success = true; // Simulating success
      if (success) {
        resolve("Data fetched successfully!");
      } else {
        reject("Error fetching data.");
      }
    }, 2000);
  });
};

fetchData()
  .then((data) => console.log(data)) // Output (after 2 seconds): Data fetched successfully!
  .catch((error) => console.error(error));
```

---

### Chaining Promises

#### Example 3: Chaining Multiple Promises
Promises can be chained for executing tasks sequentially.  

```javascript
const fetchUser = () => {
  return new Promise((resolve) => {
    setTimeout(() => resolve({ id: 1, name: "Alice" }), 1000);
  });
};

const fetchPosts = (userId) => {
  return new Promise((resolve) => {
    setTimeout(() => resolve(["Post 1", "Post 2"]), 1000);
  });
};

// Chaining
fetchUser()
  .then((user) => {
    console.log("User:", user); // Output: User: { id: 1, name: "Alice" }
    return fetchPosts(user.id);
  })
  .then((posts) => console.log("Posts:", posts)) // Output: Posts: ["Post 1", "Post 2"]
  .catch((error) => console.error(error));
```

---

### Error Handling in Promises

#### Example 4: Using `.catch`  
```javascript
const fetchData = () => {
  return new Promise((resolve, reject) => {
    const success = false;
    setTimeout(() => {
      success ? resolve("Data fetched!") : reject("Fetch failed!");
    }, 2000);
  });
};

fetchData()
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error)); // Output (after 2 seconds): Error: Fetch failed!
```

#### Example 5: Using `.finally`  
The `.finally` block executes regardless of whether the promise is fulfilled or rejected.  

```javascript
fetchData()
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error))
  .finally(() => console.log("Operation completed.")); // Output: Operation completed.
```

---

## 2. **Async/Await**

### Why Use Async/Await?  
Async/Await makes asynchronous code look like synchronous code, improving readability and reducing callback complexity.

#### Example 1: Basic Async/Await  
```javascript
const fetchData = async () => {
  return "Data fetched!";
};

const getData = async () => {
  const data = await fetchData(); // Wait for fetchData to resolve
  console.log(data); // Output: Data fetched!
};

getData();
```

#### Example 2: Error Handling with Try/Catch  
```javascript
const fetchData = async () => {
  throw new Error("Fetch failed!");
};

const getData = async () => {
  try {
    const data = await fetchData();
    console.log(data);
  } catch (error) {
    console.error("Error:", error.message); // Output: Error: Fetch failed!
  }
};

getData();
```

---

### Combining Async/Await with APIs  

#### Example 3: Fetching Data from an API  
```javascript
const fetchPosts = async () => {
  const response = await fetch("https://jsonplaceholder.typicode.com/posts");
  const posts = await response.json();
  console.log(posts);
};

fetchPosts(); // Output: Array of posts from the API
```

---

## 3. **Event Handling in JavaScript**

### What are Events?  
Events are actions triggered by the user or the browser, such as clicks, key presses, or page loads.

### Adding Event Listeners  

#### Example 1: Basic Event Listener  
```html
<button id="myButton">Click Me!</button>
<script>
  const button = document.getElementById("myButton");
  button.addEventListener("click", () => {
    console.log("Button clicked!"); // Output: Button clicked!
  });
</script>
```

---

### Event Object  
The `event` object contains information about the event.

#### Example 2: Using the Event Object  
```html
<button id="myButton">Click Me!</button>
<script>
  const button = document.getElementById("myButton");
  button.addEventListener("click", (event) => {
    console.log("Button ID:", event.target.id); // Output: Button ID: myButton
  });
</script>
```

---

### Types of Events  

#### Mouse Events:  
1. `click`: When an element is clicked.  
2. `dblclick`: When an element is double-clicked.  
3. `mouseover`: When the mouse hovers over an element.  

#### Example 3: Mouse Events  
```html
<div id="box" style="width: 100px; height: 100px; background: lightblue;"></div>
<script>
  const box = document.getElementById("box");

  box.addEventListener("mouseover", () => {
    box.style.backgroundColor = "lightgreen";
    console.log("Mouse is over the box!");
  });

  box.addEventListener("mouseout", () => {
    box.style.backgroundColor = "lightblue";
    console.log("Mouse left the box!");
  });
</script>
```

---

### Combining Events and Promises  

#### Example 4: Fetching Data on Button Click  
```html
<button id="fetchButton">Fetch Data</button>
<script>
  const fetchButton = document.getElementById("fetchButton");

  const fetchData = async () => {
    console.log("Fetching data...");
    const response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
    const data = await response.json();
    console.log("Fetched Data:", data); // Output: Fetched Data: { id: 1, ... }
  };

  fetchButton.addEventListener("click", fetchData);
</script>
```

---

### **Key Takeaways**:  
1. **Promises**: Essential for handling async operations like API calls.  
2. **Async/Await**: Simplifies async operations and error handling.  
3. **Event Handling**: Connects user interactions to JavaScript logic.  

 Now we’ll move on to **ES6 Classes, Prototypes, and Closures**, foundational for understanding React components, state, and lifecycle. 