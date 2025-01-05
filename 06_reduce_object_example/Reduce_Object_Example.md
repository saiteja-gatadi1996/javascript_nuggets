
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

```js
// cart example
const cart = [
  {
    title: 'Samsung Galaxy S7',
    price: 599.99,
    amount: 1,
  },
  {
    title: 'google pixel ',
    price: 499.99,
    amount: 2,
  },
  {
    title: 'Xiaomi Redmi Note 2',
    price: 699.99,
    amount: 4,
  },
  {
    title: 'Xiaomi Redmi Note 5',
    price: 399.99,
    amount: 3,
  },
]
```

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
console.log(total) // { totalItems: 0, cartTotal: 0 }
```

```javascript
//another example
let total = cart.reduce((total, cartItem) => {
    return total;
}, {});

console.log(total) // {}
```

```javascript
//another example
let total = cart.reduce((total, cartItem) => {
    console.log(cartItem); // logs all the objects inside the original array
    return total;
}, { totalItems: 0, cartTotal: 0 });
console.log(total) // { totalItems: 0, cartTotal: 0 }
```

- <ins>**Always return the**</ins> **`total`**.  
- Set up parameters:  
  - `total` for accumulative results.  
  - `cartItem` for each object.

---

### **Updating Total Items and Cart Total**
#### Updating Logic:
```javascript
// we are destructuring the price and amount from the arrayItem (cartItem)
const { price, amount } = cartItem;

// count items
total.totalItems += amount;

// count sum
total.cartTotal += amount * price;
```


```js
// Full Logic with totalItems, cartTotal
let total = cart.reduce((total, cartItem) => {

const { price, amount } = cartItem;

// count items
total.totalItems += amount;

// count sum
total.cartTotal += amount * price;
    return total;
}, { totalItems: 0, cartTotal: 0 });

console.log(total) // { totalItems: 10, cartTotal: 5599.900000000001 }
```

#### Fixing Numbers:
- Use `.toFixed(2)` to limit decimals.  
- Convert result back to **number** with `parseFloat`.


```js
// Full Logic after applying .toFixed(2)
let {totalItems, cartTotal} = cart.reduce((total, cartItem) => {

const { price, amount } = cartItem;

// count items
total.totalItems += amount;

// count sum
total.cartTotal += amount * price;
    return total;
}, { totalItems: 0, cartTotal: 0 });

cartTotal = parseFloat(cartTotal.toFixed(2));
console.log(totalItems, cartTotal); //10, 5599.9
```

---

### **Counting Repository Languages**
**Goal**: Count languages used in repositories (e.g., CSS, HTML, JavaScript).  

#### Fetching Data:
```javascript
const url = 'https://api.github.com/users/john-smilga/repos?per_page=100';

const fetchRepos = async()=>{
  const response = await fetch(url);
  const data = await response.json();
  console.log(data) // logs the api response
}
```

#### Reduce Example:
```javascript
const languageCount = data.reduce((total, repo) => {
    const { language } = repo;
    if (language) {
        total[language] = total[language] + 1 || 1;
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

---

