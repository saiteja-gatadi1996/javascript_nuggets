# JavaScript Nuggets - Promises  
**YouTube Video:** [Javascript Nuggets - Promises](https://www.youtube.com/watch?v=IBjmTlShf6U)  

---


- **Topic:** Promises in JavaScript.  
- **Purpose:** Avoid "callback hell" and write asynchronous code in a synchronous fashion.  
  - Promises work well with `async/await`, which provides cleaner syntax (to be covered in future videos).
- Focus: Learning **concepts of promises** and **consuming them** effectively.  

---

### Basics of Promises
- **Definition:** A promise is an object that represents a value that you hope to receive in the future.  
- **Analogy:**
  - Ordering at a fast food restaurant.
    - Payment = Promise.
    - Receipt = Pending promise.
    - Delivery = Fulfilled promise.
    - No ice cream = Rejected promise.  
- **Common Example:** HTTP requests.  
  - Asynchronous operation: Server response delivers data or error.

---

### Creating a Promise
```javascript
const promise = new Promise((resolve, reject) => {
  // Initial state: Pending
  console.log(promise); // { state: 'pending', result: undefined }
});
```

- **States of a Promise:**  
  1. **Pending:** Initial state.  
  2. **Fulfilled:** Operation completed successfully.  
  3. **Rejected:** Operation failed.  
- **One-Way Transition:** Promises cannot revert to a previous state.  

---

### Resolving and Rejecting Promises
#### Resolving a Promise
```javascript
resolve("Hello World");
console.log(promise); // { state: 'fulfilled', result: 'Hello World' }
```

- **Passing Data:**
  - Pass data into `resolve()` to return it when the promise is fulfilled.
  
#### Rejecting a Promise
```javascript
reject("There was an error");
console.log(promise); // { state: 'rejected', result: 'There was an error' }
```

---

### Accessing Promise Results
- Use `.then()` to access fulfilled values.  
- Use `.catch()` to handle rejections.  

#### Example
```javascript
promise.then((data) => {
  console.log(data); // Logs "Hello World"
});

promise.catch((error) => {
  console.error(error); // Logs "There was an error"
});
```

---

### Conditional Promise Example 
#### Logic
- Generate a random number.
- Compare it to a predefined value.
- Resolve or reject based on the comparison.

#### Code Example
```javascript
const value = 2;
const promise = new Promise((resolve, reject) => {
  const random = Math.floor(Math.random() * 3);
  if (random === value) {
    resolve("You guessed correctly");
  } else {
    reject("Wrong number");
  }
});

promise
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

#### Console Output
- Random number and result logged.
- Example:
  - `Random: 1, Error: Wrong number`
  - `Random: 2, Success: You guessed correctly`

---

### Conclusion 
- Promises simplify asynchronous code compared to callbacks.  
- Upcoming videos: Practical examples demonstrating the advantages of promises.  
