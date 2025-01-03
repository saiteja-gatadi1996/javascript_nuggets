# String includes() Method  
[Watch on Youtube](https://www.youtube.com/watch?v=m7-tSUYZRXY)  

---

- **Topic:** `includes()` method in JavaScript strings.
- **Purpose:** Checks if a string contains another string.
  - Useful for search functionality.
  - Example: Filtering products based on search text.

---

### Basic Example: Using `includes()` 
#### Code Example
```javascript
const firstName = "John";
const result = firstName.includes("Jo");
console.log(result); // true

// Changing the string
console.log(firstName.includes("Peter")); // false

// Case sensitivity
console.log(firstName.includes("JO")); // false
```

- **Highlights:**
  - `includes()` is **case-sensitive**.
  - Optional parameter for **start position**:
    ```javascript
    console.log(firstName.includes("o", 1)); // true
    console.log(firstName.includes("o", 2)); // false
    ```

---

### Using `includes()` with Objects 
#### Example: Checking a Property Value
```javascript
const product = { title: "JavaScript Guide" };
console.log(product.title.includes("Guide")); // true
console.log(product.title.includes("guide")); // false
```

- **Key Points:**
  - Works on object properties.
  - **Case sensitivity applies.**

---

### Advanced Example: Filtering Products 
#### Setup
```javascript
const products = [
  { title: "JavaScript Guide" },
  { title: "React Basics" },
  { title: "Node.js Advanced" },
];
```

#### Filtering by Search Text
```javascript
const text = "ad";
const filteredProducts = products.filter((product) => 
  product.title.toLowerCase().includes(text.toLowerCase())
);

console.log(filteredProducts);
```

#### Output
```javascript
// Matching titles
[
  { title: "React Basics" },
  { title: "Node.js Advanced" }
]
```

- **Steps:**
  1. Convert titles to **lowercase** to fix case sensitivity.
  2. Use `includes()` to check if the text exists in the title.
  3. Return matching products.

---

### Conclusion 
- **`includes()` Method:**
  - Simple and powerful for checking substring existence.
  - Ideal for implementing search functionality.
- **Dynamic Filtering:** Combine `includes()` with array methods like `filter()` to build flexible solutions.  

---
