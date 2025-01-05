
# JavaScript Nuggets - Array.from  
[Watch on Youtube](https://www.youtube.com/watch?v=zg1Bv4xubwo)  

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
- Converts an <ins>**array-like**</ins> or <ins>**iterable object**</ins> into an **array**.  
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

// [
//   Array(10) [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 ],
//   Array(10) [ 10, 11, 12, 13, 14, 15, 16, 17, 18, 19 ],
//   Array(10) [ 20, 21, 22, 23, 24, 25, 26, 27, 28, 29 ],
//   Array(10) [ 30, 31, 32, 33, 34, 35, 36, 37, 38, 39 ],
//   Array(10) [ 40, 41, 42, 43, 44, 45, 46, 47, 48, 49 ],
//   Array(10) [ 50, 51, 52, 53, 54, 55, 56, 57, 58, 59 ],
//   Array(10) [ 60, 61, 62, 63, 64, 65, 66, 67, 68, 69 ],
//   Array(10) [ 70, 71, 72, 73, 74, 75, 76, 77, 78, 79 ],
//   Array(10) [ 80, 81, 82, 83, 84, 85, 86, 87, 88, 89 ],
//   Array(10) [ 90, 91, 92, 93, 94, 95, 96, 97, 98, 99 ],
//   Array(10) [ 100, 101, 102, 103, 104, 105, 106, 107, 108, 109 ],
//   Array(10) [ 110, 111, 112, 113, 114, 115, 116, 117, 118, 119 ]
// ]
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

// Array(15) [
//   Array(8) [ 0, 1, 2, 3, 4, 5, 6, 7 ],
//   Array(8) [ 8, 9, 10, 11, 12, 13, 14, 15 ],
//   Array(8) [ 16, 17, 18, 19, 20, 21, 22, 23 ],
//   Array(8) [ 24, 25, 26, 27, 28, 29, 30, 31 ],
//   Array(8) [ 32, 33, 34, 35, 36, 37, 38, 39 ],
//   Array(8) [ 40, 41, 42, 43, 44, 45, 46, 47 ],
//   Array(8) [ 48, 49, 50, 51, 52, 53, 54, 55 ],
//   Array(8) [ 56, 57, 58, 59, 60, 61, 62, 63 ],
//   Array(8) [ 64, 65, 66, 67, 68, 69, 70, 71 ],
//   Array(8) [ 72, 73, 74, 75, 76, 77, 78, 79 ],
//   Array(8) [ 80, 81, 82, 83, 84, 85, 86, 87 ],
//   Array(8) [ 88, 89, 90, 91, 92, 93, 94, 95 ],
//   Array(8) [ 96, 97, 98, 99, 100, 101, 102, 103 ],
//   Array(8) [ 104, 105, 106, 107, 108, 109, 110, 111 ],
//   Array(8) [ 112, 113, 114, 115, 116, 117, 118, 119 ]
// ]
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
