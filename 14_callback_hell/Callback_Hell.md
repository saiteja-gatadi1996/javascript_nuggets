
# JavaScript Nuggets - Callback Hell

[Watch on Youtube](https://www.youtube.com/watch?v=bx9xYPt2tdc)


- **Topic**: Callback Hell.
  - Callback functions are widely used and great for asynchronous operations.
  - However, promises and async/await make code easier to manage in some scenarios.
- **Preview**:
  - Promises will be tackled in the next video.
  - Callback hell occurs with asynchronous operations executed in sequence.

### **Scenario** 
- HTML setup:
  - Three `<h2>` elements and a button.
  - Goal:
    - Click the button.
    - After **1 second**, the first heading turns **red**.
    - After **3 seconds**, the second heading turns **blue**.
    - After **2 more seconds**, the third heading turns **green**.
  - Classes: `first`, `second`, `third`.
  - Button is wired up with an event listener for a **click**.

### **Basic Example** 
- Initial setup to test wiring:
  ```javascript
  console.log("Hello World");
  ```
- Using `setTimeout` for the first heading:
  ```javascript
  setTimeout(() => {
    first.style.color = "red";
  }, 1000); // 1 second
  ```

### **Extending the Logic** 
- Adding logic for second and third headings:
  ```javascript
  setTimeout(() => {
    first.style.color = "red";
  }, 1000); // 1 second

  setTimeout(() => {
    second.style.color = "blue";
  }, 3000); // 3 seconds

  setTimeout(() => {
    third.style.color = "green";
  }, 2000); // 2 seconds
  ```
- Issue: Actions don’t execute in sequence.

### **Requirements Change** 
- New requirement:
  - First heading turns **red** after **1 second**.
  - Second heading turns **blue** after **4 seconds**.
  - Third heading turns **green** after **6 seconds**.
- Hardcoding times is not an option.

### **Callback Hell Implementation** 
- Nesting `setTimeout` calls inside callback functions:
  ```javascript
  setTimeout(() => {
    first.style.color = "red"; // 1 second

    setTimeout(() => {
      second.style.color = "blue"; // 3 seconds

      setTimeout(() => {
        third.style.color = "green"; // 2 seconds
      }, 2000); // After second
    }, 3000); // After first
  }, 1000); // Initial delay
  ```
- Now, changes to the first timeout will affect the rest.

### **Drawbacks**
- **Harder to manage** as code grows.
- Pyramid-like structure leads to poor readability and maintainability.
- Example: Changing `green` in the last callback requires adjustments across all dependent logic.

### **Conclusion** 
- Callback hell occurs with deeply nested asynchronous code.
- Promises and `async/await` provide better solutions:
  - Improve code readability.
  - Simplify management of asynchronous operations.

---

*Stay tuned for the next video on Promises!*
