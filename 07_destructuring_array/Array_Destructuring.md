
# JavaScript Nuggets - Destructuring (Array)

[Watch on Youtube](https://www.youtube.com/watch?v=qhECs40xMec)

  - **Definition**: A faster or easier way to access/unpack variables from arrays or objects.
- **Key Use Cases**:
  - Unpacking variables from arrays or objects.
  - Passing objects in function parameters (will be covered as part of REST & SPREAD operators).

### **Accessing Array Items**
- **Scenario**: Two arrays, `fruits` and `friends`.

```js
const fruits = ['orange', 'banana', 'lemon'];

const friends = ['john', 'peter', 'bob', 'anna', 'kelly'];
```

- Traditional way to access array elements:
  ```javascript
  const fruit1 = fruits[0];
  console.log(fruit1); // Outputs: "orange"
  ```
  - **Issue**: Cumbersome for accessing multiple values.

### **Using Destructuring** 
- Syntax:
  ```javascript
  const [first, second] = arrayName;
  ```
- **Example**:
  ```javascript
  const [john] = friends;
  console.log(john); // Outputs: "john"
  ```
  - Adds simplicity compared to traditional methods.
  - Allows naming variables dynamically.

### **Accessing Multiple Values** 
- Access all items:
  ```javascript
  const [john, peter, bob, anna, kelly] = friends;
  console.log(john, peter, bob, anna, kelly); // john peter bob anna kelly
  ```
- Omitting some values:
  ```javascript
  const [john, , bob] = friends;
  console.log(john, bob); // Skips the second value
  ```

### **Accessing Non-Existent Values** 
- **Scenario**: Accessing an item that doesn't exist.
  ```javascript
  const [kelly, susan] = friends;
  console.log(susan); // Outputs: undefined
  ```

### **Dynamic Variable Names** 
- Naming variables dynamically:
  ```javascript
  // I changed the first value from john to enemy
  const [enemy] = friends;
  console.log(enemy); // Outputs: "john"
  ```

### **Skipping Array Items** 
- Skip items using commas:
  ```javascript
  const [john, , bob, , kelly] = friends;
  // below logs based on the index position (ex: bob is at index 2nd, kelly at index 4th)
  console.log(john, bob, kelly); // john bob kelly
  ```

### **Swapping Variables** 
- Traditional way:
  ```javascript
  let first = "Bob";
  let second = "John";
  let temp = second;
  second = first;
  first = temp;
  console.log(first, second); // Outputs: "John", "Bob"
  ```
- **Using Array Destructuring**:
  ```javascript
  let first = "Bob";
  let second = "John";
  [first, second] = [second, first];
  console.log(first, second); // Outputs: "John", "Bob"
  ```

### **Summary** 
- **Key Takeaways**:
  - Array destructuring simplifies accessing/unpacking values.
  - Syntax:
    ```javascript
    const [var1, var2] = arrayName;
    ```
  - Skipping values:
    ```javascript
    const [val1, , val3] = arrayName;
    ```
  - Accessing non-existent values returns `undefined`.
  - Dynamic variable naming is supported.

---

