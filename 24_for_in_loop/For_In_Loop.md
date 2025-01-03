
# "for in" Loop

[YouTube Video Link](https://www.youtube.com/watch?v=ZNs3JEplsmQ)

---

The **`for in` loop** is useful for iterating over **object properties**. Here's an example:

#### Example: Iterating Over Object Properties

```javascript
const person = {
    name: "John",
    age: 25,
    job: "Developer"
};

for (let propertyName in person) {
    console.log(`${propertyName}: ${person[propertyName]}`);
}
```

### Explanation:

- **Key**: `propertyName` gives the key (e.g., `name`, `age`, `job`).
- **Value**: Use `person[propertyName]` to access the value.

**Output**:

```
name: John
age: 25
job: Developer
```

### Important Note:

- **Do not use `for in` on arrays**:
  - It's not recommended for arrays because it may iterate over properties rather than values.
  - Use **array methods** (e.g., `forEach`, `map`) or the **`for of` loop** for arrays.

---

**Summary**:

- The `for in` loop is ideal for objects.
- For arrays, prefer methods or `for of` loops.
