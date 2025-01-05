# Javascript Nuggets - Debounce

[Watch on YouTube](https://www.youtube.com/watch?v=tYx6pXdvt1s)

**Introduction**


- **Topic**: Setting up debounce functionality in vanilla JavaScript.
- **Debounce**:
  - Programming technique to improve performance of frequently called functions.
  - Sets a threshold time to delay function execution until activity pauses.
  - **Example**: Search query - execute search only after the user stops typing.

**Use Case**

- Debounce helps avoid unnecessary executions.
- Example: User types in a search box.
  - Without debounce: Search function executes on every keystroke.
  - With debounce: Search executes after user stops typing.

**Vanilla JS Setup**

- HTML structure:
  ```html
  <button class="btn">Click Me</button>
  ```
- Basic button click functionality:
  ```javascript
  const btn = document.querySelector('.btn');
  btn.addEventListener('click', () => {
    console.log('You clicked me');
  });
  ```

**Goal**

- Add delay logic to the button click:
  - Log `"You clicked me"` **only after 2 seconds** of the last click.
  - Ignore multiple rapid clicks.

**Set Timeout Basics**

- Use `setTimeout` to introduce delay:
  ```javascript
  function debounce() {
    setTimeout(() => {
      console.log('You clicked me');
    }, 2000);
  }
  ```
- Attach `debounce` to the button click event:
  ```javascript
  btn.addEventListener('click', debounce);
  ```

**Problem**

- Current setup logs multiple messages for multiple clicks.
- **Objective**:
  - Log message **only after the last click**.

**Using Timeout IDs**

- `setTimeout` returns a unique ID for each timeout.
- Use `clearTimeout` to cancel the previous timeout:
  ```javascript
  let timeoutID;

  function debounce() {
    clearTimeout(timeoutID);
    timeoutID = setTimeout(() => {
      console.log('You clicked me');
    }, 2000);
  }

  btn.addEventListener('click', debounce);
  ```
- **Explanation**:
  - Cancels previous timeout on each click.
  - Sets a new timeout for the latest click.

**Returning a Function**

- Refactor `debounce` to return a function:
  ```javascript
  function debounce(callback, delay) {
    let timeoutID;

    return function () {
      clearTimeout(timeoutID);
      timeoutID = setTimeout(() => {
        callback();
      }, delay);
    };
  }

  const debouncedClick = debounce(() => {
    console.log('You clicked me');
  }, 2000);

  btn.addEventListener('click', debouncedClick);
  ```

**Dynamic Debounce**

- Make debounce more reusable:
  - Accept a function (`callback`) and delay time (`delay`) as arguments.
  ```javascript
  const debouncedLog = debounce(() => {
    console.log('Dynamic debounce in action!');
  }, 3000);

  btn.addEventListener('click', debouncedLog);
  ```

**Conclusion**

- **Key Takeaways**:
  - `setTimeout` and `clearTimeout` enable debounce functionality.
  - Debounce delays execution until activity pauses.
- **Applications**:
  - Search bars, API requests, scroll events, and more.
- Example behavior:
  - Click the button multiple times → Logs appear only after the final click delay.

- **Enhancements**:
  - Pass logic and delay as parameters for reusability.


```javascript
  const debouncedFunction = debounce(callback, delay);
````
