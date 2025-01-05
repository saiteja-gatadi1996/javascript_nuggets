# Object.keys(), Object.values(), Object.entries()

[YouTube Video](https://www.youtube.com/watch?v=uXRwk2pALco)


**Introduction**

- Learn about three methods to convert objects into arrays:
  - `Object.keys()` - Retrieves property names as an array.
  - `Object.values()` - Retrieves values as an array.
  - `Object.entries()` - Retrieves both keys and values as an array of arrays.
- Example:
  ```javascript
  const person = { name: 'John', age: 30, status: 'active' };
  ```

**Using `Object.keys()`**

- Syntax:
  ```javascript
  const keys = Object.keys(person);
  console.log(keys); // ['name', 'age', 'status']
  ```
- **Output**:
  - Converts all keys of the object into an array.
  - The array can use regular array methods and properties.

**Using `Object.values()`**

- Syntax:
  ```javascript
  const values = Object.values(person);
  console.log(values); // ['John', 30, 'active']
  ```
- **Output**:
  - Converts all values of the object into an array.

**Using `Object.entries()`**

- Syntax:
  ```javascript
  const entries = Object.entries(person);
  console.log(entries);
  // [['name', 'John'], ['age', 30], ['status', 'active']]
  ```
- **Output**:
  - Converts keys and values into an array of arrays.

**Working with `Object.entries()`**

- Using `Array.map()` to process entries:
  ```javascript
  const result = Object.entries(person);
  const newResult = result.map(([key, value]) => key);
  console.log(newResult); // ['name', 'age', 'status']
  ```
  - **Explanation**:
    - Array destructuring is used to extract `key` and `value`.
    - Only the keys are returned.

**Using Array Destructuring**

- Example:
  ```javascript
  const result = Object.entries(person);
  result.forEach(([key, value]) => {
    console.log(`Key: ${key}, Value: ${value}`);
  });
  ```
- **Output**:
  - Logs each key and value pair to the console.

**Skipping Values in `for...of` Loops**

- Using `for...of` with destructuring:
  ```javascript
  for (const [key, value] of Object.entries(person)) {
    console.log(`Key: ${key}, Value: ${value}`);
  }
  ```
- **Alternative**:
  - Skip destructuring by directly working with the array.

**Processing Keys or Values**

- Filter keys or values using array methods:
  ```javascript
  const result = Object.entries(person);
  const filteredKeys = result.map(([key]) => key);
  console.log(filteredKeys); // ['name', 'age', 'status']
  ```
- **Use Case**:
  - Useful for filtering, transforming, or reformatting data.

**Advanced `for...of` Loop**

- Simplify with destructuring:
  ```javascript
  for (const [key, value] of Object.entries(person)) {
    console.log(key, value);
  }
  ```
- **Explanation**:
  - Directly destructure array elements within the loop.

**Conclusion**

- Methods provide an easy way to work with objects in array format.
- Use cases include data manipulation, transformation, and UI rendering in JavaScript.
- Recap:
  - `Object.keys()` for keys.
  - `Object.values()` for values.
  - `Object.entries()` for both keys and values.
