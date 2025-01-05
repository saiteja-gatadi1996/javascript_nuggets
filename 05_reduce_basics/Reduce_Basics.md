
# Javascript Nuggets - Reduce Basics

👉 [Watch on Youtube](https://www.youtube.com/watch?v=3WkW9nrS2mw)

---


**Understanding Reduce**

```js
// iterates, callback function
// reduces to a single value - number, array, object
// 1st parameter ('acc') - total of all calculations
// 2nd parameter ('curr') - current iteration/value
```

```js
// Input Array
const staff = [
  { name: 'bob', age: 20, position: 'developer', salary: 100 },
  { name: 'peter', age: 25, position: 'designer', salary: 300 },
  { name: 'susy', age: 30, position: 'the boss', salary: 400 },
  { name: 'anna', age: 35, position: 'intern', salary: 10 },
];
```

-------

- Iterates over an array like `map`, `filter`, and `forEach`.
- **Key Difference:**  
  - Reduces the array to a single value.
  - The single value can be:
    - A number
    - An array
    - An object

**Why Use Reduce?**  
- Flexibility in returning various data structures.
- Two parameters in the callback function:
  - **First Parameter:** Total of all calculations (commonly named `accumulator`).
  - **Second Parameter:** Current value in the iteration.

---

**Example: Calculating Total Salary**  
- **Task:** Calculate the daily total salary from an array of staff with names, ages, and positions.

```js
const dailyTotal = staff.reduce((total, person) => {
  return total += person.salary;
}, 0);

console.log(dailyTotal)
// Output: 810
```

---


**Iteration Details**  
- **First Iteration:**
  - Total: `0` (initial value).
  - Current salary: `100`.

- **Second Iteration:**
  - Total: `100` (previous total).
  - Current salary: `300`.

- **Final Total:**  
  The sum of all salaries.

---

**Importance of Returning the Total**  
- Always **`return`** the total to avoid errors.
- Example of incorrect behavior without return:
  ```js
  // If you forget to return, undefined causes errors:
  total += person.salary; // Will fail
  ```

**Output Without Return:**  
- `undefined` causes a mismatch in calculations.

---

**Using Non-Zero Initial Values**  
- Example:
  ```js
  const expenses = 1000;
  const total = staff.reduce((total, person) => total + person.salary, expenses);
  console.log(total);  //1810
  ```
- **Result:** Adds expenses to the total.

---

## Conclusion
- **Basics of Reduce:**
  - Iterate over arrays.
  - Reduce them to a single value of any type.
- **Important Tips:**
  - Always return the total.
  - Use initial values based on requirements.

---
