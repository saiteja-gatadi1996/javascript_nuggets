
# JavaScript Nuggets - Array.from  
**YouTube Video:** [Javascript Nuggets - Array.from](https://www.youtube.com/watch?v=zg1Bv4xubwo)  

---


- **Topic**: Understanding `Array.from`.  
  - Start with basic examples.  
  - End with **pagination setup** using `Array.from`.  

---

### Key Concept: Array.from 
- **Important Note**:  
  - `Array.from` is **not on the prototype** like `filter` or `map`.  
  - Usage: `Array.from` is invoked directly.  

#### Definition  
- Converts an **array-like** or **iterable object** into an **array**.  
- Examples of array-like objects:  
  - Strings, NodeLists, Sets, etc.  

---

### Example 1: Converting a String to an Array 
```javascript
const str = "Udemy";
const result = Array.from(str);
console.log(result); // ['U', 'd', 'e', 'm', 'y']
```

- **Output**: Each letter in the string becomes an individual item in the array.  

---

### Example 2: Handling NodeLists 
#### Problem:  
- Selecting all `<h2>` elements with a specific class results in a **NodeList**.  
- NodeLists are **array-like** but don't support all array methods (e.g., `filter`).  

#### Solution: Convert NodeList to an Array  
```javascript
const headings = document.querySelectorAll(".text");
const headingArray = Array.from(headings);
const filteredHeading = headingArray.find(
  (item) => item.textContent === "Person"
);
console.log(filteredHeading);
```

- **Steps**:  
  1. Use `document.querySelectorAll()` to select elements.  
  2. Convert NodeList to Array using `Array.from`.  
  3. Apply array methods like `find`.  

---

### Example 3: Pagination Setup  
- **Use Case**: Create pagination for **GitHub followers** or similar lists.  

#### Steps:  
1. **Generate an Array**  
```javascript
const items = Array.from({ length: 120 }, (_, index) => index);
console.log(items); // [0, 1, 2, ..., 119]
```

2. **Define Items Per Page**  
```javascript
const itemsPerPage = 10;
const totalPages = Math.ceil(items.length / itemsPerPage);
console.log(totalPages); // 12
```

3. **Slice Items for Each Page**  
```javascript
const paginatedItems = Array.from({ length: totalPages }, (_, index) => {
  const start = index * itemsPerPage;
  return items.slice(start, start + itemsPerPage);
});
console.log(paginatedItems);
```

#### Output:  
- An array of arrays, each containing items for a specific page.  

---

### Advanced Example: Adjusting Items Per Page   
- Change `itemsPerPage` dynamically:  
```javascript
const itemsPerPage = 8;
const updatedPages = Array.from({ length: Math.ceil(items.length / itemsPerPage) }, (_, index) => {
  const start = index * itemsPerPage;
  return items.slice(start, start + itemsPerPage);
});
console.log(updatedPages);
```

---

### Conclusion
- **`Array.from`** is versatile for:  
  - Converting array-like objects.  
  - Generating arrays dynamically.  
  - Implementing features like **pagination**.  
- **Upcoming Project**:  
  - Build a **pagination project** using `Array.from`.  
  - Features:  
    - GitHub followers display.  
    - Dynamic buttons for navigation.  
    - Prev/Next and specific page buttons.  
