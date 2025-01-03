
# JavaScript Nuggets: Array includes()

[Watcb on Youtube](https://www.youtube.com/watch?v=HBhkKybaKeU)

---

**Array `includes()`** method.  
- **Purpose:** Checks if an item is in the array.  
- **Returns:** `true` or `false`.  
- **Use Case:** Useful in conditional statements.  

**Example:**  
```javascript
const groceries = ['milk', 'bread', 'meat'];
let randomItem = 'lemon';

const isIncluded = groceries.includes(randomItem);
console.log(isIncluded); // false (lemon is not in groceries)
```

---

If we change `randomItem` to `milk`:  

```javascript
randomItem = 'milk';
const isIncluded = groceries.includes(randomItem);
console.log(isIncluded); // true (milk is in groceries)
```

---

**Optional Second Argument:**  
You can pass an **index** as the second argument to specify where the search starts.  

**Example:**  
```javascript
const isIncludedFromIndex = groceries.includes('milk', 1);
console.log(isIncludedFromIndex); // false (search starts at index 1)
```

- By default, the search starts at index `0`.  
- If the specified index excludes the target item, `false` is returned.  

---

**Using `includes()` in Conditional Statements:**  

```javascript
const groceries = ['milk', 'bread', 'meat'];
let randomItem = 'milk';

if (groceries.includes(randomItem)) {
  console.log(`Yay! ${randomItem} is on the list.`);
} else {
  console.log(`Oops! ${randomItem} is not on the list.`);
}
```

- Since `includes()` returns `true` or `false`, it simplifies conditional logic.  
- No need to use `findIndex` or other methods.  

---

### Key Takeaways

- **`includes()` Method:**  
  - Checks if an array contains a specific item.  
  - Returns `true` or `false`.  
  - Accepts an optional **start index** as the second argument.  

- **Ideal for Conditional Statements:**  
  - Simplifies checks for array membership.  

---
