
# Javascript Nuggets - Reduce (Object Example)

[Watch on YouTube](https://www.youtube.com/watch?v=5BFkp8JjLEY)

---

We’ll cover more complex `reduce` method examples:  
- Counting cart totals.  
- Summing up languages from GitHub repositories.  

We’ll focus on returning an **object** from `reduce`.  

---

### **Counting Cart Totals**
**Project Example**:  
- A cart application using `useReducer` hook in React.  
- **Dynamic Functionality**:  
    - Update cart totals dynamically.  
    - Count total items in the cart.  
    - Calculate the total cost.

---

### **Static Implementation**
- Prepared an array of objects (`cart`), where each object contains:
  - `title`
  - `price` (cost of the item)
  - `amount` (number of items of the product).

- **Goal**: Use `reduce` to calculate:  
  1. **Total Items**  
  2. **Cart Total**

---

### **Setting Up Reduce**
#### Code Example:  
```javascript
let total = cart.reduce((total, cartItem) => {
    // Define what we return: an object.
    return total;
}, { totalItems: 0, cartTotal: 0 });
```

- Always return the **total**.  
- Set up parameters:  
  - `total` for accumulative results.  
  - `cartItem` for each object.

---

### **Updating Total Items and Cart Total**
#### Updating Logic:
```javascript
const { price, amount } = cartItem;
total.totalItems += amount;
total.cartTotal += amount * price;
```

#### Fixing Numbers:
- Use `.toFixed(2)` to limit decimals.  
- Convert result back to **number** with `parseFloat`.

---

### **Counting Repository Languages**
**Goal**: Count languages used in repositories (e.g., CSS, HTML, JavaScript).  

#### Fetching Data:
```javascript
const response = await fetch(url);
const data = await response.json();
```

#### Reduce Example:
```javascript
const languageCount = data.reduce((total, repo) => {
    const { language } = repo;
    if (language) {
        total[language] = (total[language] || 0) + 1;
    }
    return total;
}, {});
```

#### Example Output:
```json
{
    "JavaScript": 38,
    "CSS": 45,
    "HTML": 14
}
```

---

### **Final Notes**
1. Use `reduce` creatively to return objects for advanced functionality.  
2. Real-world applications:
   - Calculating cart totals in e-commerce.
   - Counting repository languages dynamically in GitHub projects.

Enjoy coding with `reduce`!

---

