
# **JavaScript Nuggets - Rest Operator**
[Watch on Youtube](https://www.youtube.com/watch?v=f-frKsJoBQU)

---

  - **Rest Operator**: *Gathers or collects items*.
  - **Spread Operator**: *Spreads out items*.

---

### Use Cases and Key Differences**
#### **Rest Operator**: Used in 
  - **`destructuring`** 
  -  **function `declarations`**.

#### **Spread Operator**: 
  - Used when **`invoking`** functions.


> **Important Note:** Placement matters for the **Rest Operator**, and it should always be placed at the end.

---

### **Destructuring with Arrays**
- Example:
  ```javascript
  const fruits = ["apple", "orange", "lemon", "banana", "pear"];
  const [first, ...rest] = fruits;
  console.log(first); // "apple"
  console.log(rest);  // ["orange", "lemon", "banana", "pear"]
  ```
- Observations:
  - The `rest` variable collects the remaining array items.
  - The size of `rest` changes as more items are destructured:
    ```javascript
    const [first, second, ...rest] = fruits;
    console.log(rest); // ["lemon", "banana", "pear"]
    ```

---

### **Using Array Methods**
- You can apply array methods like `find` to the rest array:
  ```javascript
  const specificFruit = rest.find(fruit => fruit === "lemon");
  console.log(specificFruit); // "lemon"
  ```

---

### **Destructuring with Objects**
- Example:
  ```javascript
  const person = { name: "John", lastName: "Doe", job: "Developer" };
  const { name, ...rest } = person;
  console.log(name); // "John"
  console.log(rest); // { lastName: "Doe", job: "Developer" }
  ```
- **Key Points:**
  - The **Rest Operator** gathers remaining properties in objects.
  - Always place the **`Rest Operator`** at the end:
    ```javascript
    const { job, ...rest } = person;
    ```

---

### **Functions with Rest Operator**
- Declaring functions using the **Rest Operator**:
  ```javascript
  function getAverage(name, ...scores) {
      console.log(name); // Peter
      console.log(scores); // [ 100, 90, 80 ]
      const average = scores.reduce((total, item) => total + item, 0) / scores.length;
      return average;
  }
  const avg = getAverage("Peter", 100, 90, 80);
  console.log(avg); // 90
  ```
- **Key Notes:**
  - **Rest Operator** gathers parameters during function declaration.

---

### **Combining Rest and Spread Operators**
- Example: Passing array values as individual arguments:
  ```javascript
  const testScores = [100,90,80];
  const avg = getAverage("John", ...testScores);
  console.log(avg); // Calculates average (ex: 90)
  ```
- **Key Difference:**
  - **Rest Operator**: Used during declaration to gather items.
  - **Spread Operator**: Used during invocation to spread items.

---

### **Summary**
- Syntax is the same for both operators (`...`), but functionality differs:
  - **Rest Operator**: Gathers and collects items.
  - **Spread Operator**: Spreads out items.
- Use **Rest Operator** in destructuring and function declarations.
- Use **Spread Operator** when invoking functions.
- Placement is crucial:
  - Always place the **Rest Operator** at the end.
- Avoid name collisions when using the **Rest Operator**.

---

