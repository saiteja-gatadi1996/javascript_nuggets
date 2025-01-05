
# JavaScript Nuggets - `new Set()`

[Watch on Youtube](https://www.youtube.com/watch?v=H4NnCItCZWE)

- **Topic**: The `Set` object.
  - Stores only **unique values**.
  - Values can be of **any type**.
- **Setup**:
  ```javascript
  const unique = new Set();
  console.log(unique); // Logs an empty Set object
  ```
- Initial size of the Set is `0`.

### **Set Methods** 
- **Available Methods**:
  1. `add()` - Adds values to the set.
  2. `delete()` - Removes specific values.
  3. `clear()` - Clears the entire set.
  4. `has()` - Checks if a value exists in the set.

#### Using `add()`:
```javascript
unique.add("first");
unique.add("second");
unique.add("third");
unique.add("first"); // Duplicate value ignored
console.log(unique); // Set { "first", "second", "third" }
```

#### Using Variables with `add()`:
```javascript
const random = "third";
unique.add(random);
console.log(unique); // Value remains unchanged
```

### **Deleting Items from the Set** 
- Example:
  ```javascript
  const result = unique.delete("third");
  console.log(result); // true if value existed and was deleted
  ```
- Attempting to delete a non-existent value:
  ```javascript
  console.log(unique.delete("fifth")); // false
  ```

### **Checking for Values** 
- Using `has()`:
  ```javascript
  const isValueFound = unique.has("first");
  console.log(isValueFound); // true
  ```

### **Iterators** 
- Iterators like `entries()`, `keys()`, and `values()` are available.
- Example usage with `forEach` is not covered here.

### **Use Case: Getting Unique Items from an Array** 
- Scenario: Extracting unique companies from an array of objects.
- Example setup:
  ```javascript
  const products = [
    { title: "Product 1", company: "Apple" },
    { title: "Product 2", company: "Google" },
    { title: "Product 3", company: "Apple" },
    ];
  ```

#### Step 1: Map the Array
```javascript
const companies = products.map((item) => item.company);
console.log(companies); // ["Apple", "Google", "Apple"]
```

#### Step 2: Use `Set`
```javascript
const uniqueCompanies = new Set(companies);
console.log(uniqueCompanies); // Set { "Apple", "Google" }
```

#### Step 3: Convert Set to Array
```javascript
const finalCompanies = [...uniqueCompanies];
console.log(finalCompanies); // ["Apple", "Google"]
```

#### Adding an "All" Option
```javascript
const finalCompaniesWithAll = ["All", ...uniqueCompanies];
console.log(finalCompaniesWithAll); // ["All", "Apple", "Google"]
```

### **One-Liner Example** 
- Combine all steps into a single line:
```javascript
const result = ["All", ...new Set(products.map((item) => item.company))];
console.log(result); // ["All", "Apple", "Google"]
```

---
