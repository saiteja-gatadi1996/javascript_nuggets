
# JavaScript Nuggets: Promises Example

[Watch on Youtube](https://www.youtube.com/watch?v=GKVA6jYrgKc)

---

In this video, we are covering how to use promises to build a three-heading example.  

**Setup in `index.html`:**  
- Three headings with classes.
- A button to trigger the sequence.  

**Goal:**  
- Click the button to:  
  1. Turn the first heading red in 1 second.  
  2. Turn the second heading blue in 3 seconds.  
  3. Turn the third heading green in 2 seconds.  

---

We previously used **callbacks** to achieve this. Now, we'll use **promises** for cleaner, easier-to-read code.  

**Steps:**  
1. Set up an event listener for the button.  
2. Create a function `addColor` that:  
   - Accepts `time`, `selector`, and `color`.  
   - Returns a promise.  

```javascript
function addColor(time, selector, color) {
  const element = document.querySelector(selector);
  return new Promise((resolve, reject) => {
    if (element) {
      setTimeout(() => {
        element.style.color = color;
        resolve();
      }, time);
    } else {
      reject(`No such element: ${selector}`);
    }
  });
}
```

---

**Using the function:**  

```javascript
addColor(1000, '.first', 'red')
  .then(() => addColor(3000, '.second', 'blue'))
  .then(() => addColor(2000, '.third', 'green'))
  .catch((error) => console.log(error));
```

- First heading turns red in 1 second.  
- Second heading turns blue in 3 seconds.  
- Third heading turns green in 2 seconds.  

**Error Handling:**  
- If a selector is incorrect, the `catch` block logs the error.

---

**Key Benefits of Promises:**  
- Avoid callback hell by chaining `.then` statements.  
- Resolve or reject a promise to handle success and errors gracefully.

---

**Passing Data Between Promises:**  

```javascript
addColor(1000, '.first', 'red', 'Hello World')
  .then((data) => {
    console.log(data); // Logs "Hello World"
    return addColor(3000, '.second', 'blue');
  })
  .then(() => addColor(2000, '.third', 'green'))
  .catch((error) => console.log(error));
```

- Data (`"Hello World"`) is passed from one promise to the next.

---

**Why Use Promises Over Callbacks?**  
- Promises allow asynchronous code to look synchronous.  
- Cleaner and more readable code.  
- The setup for reusable functions only needs to be done once.  

**Key Takeaway:**  
Using promises, you can avoid callback hell and write maintainable code for asynchronous operations.

---

