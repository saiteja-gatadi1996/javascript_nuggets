
# Javascript Nuggets - Destructuring (Object)

**YouTube Video**: [Javascript Nuggets - Destructuring (object)](https://www.youtube.com/watch?v=i4vhNKihfto)

---


- **Object Destructuring** simplifies accessing or unpacking variables from objects.
- **Problem**: Accessing nested properties in objects can involve repetitive patterns:
  - Example: `object.property.subproperty`.
- **Real-world scenario**:
  - API responses are often deeply nested objects.
  - Repeating the access pattern for nested data can become tedious.

---

```js
// Main Object
const bob = {
  first: 'bob',
  last: 'sanders',
  city: 'chicago',
  siblings: {
    sister: 'jane',
  },
};

// In our daily lives, we perform some operations like below

const firstName = bob.first; //bob
const lastName = bob.last; // sanders
const sister = bob.siblings.sister; //jane
```


----

- **Object Destructuring** reduces repetition and improves readability:
  1. Use a keyword (`const`, `let`).
  2. **Instead of `square` brackets (used in <ins>array destructuring</ins>), use `curly` braces for <ins>objects.</ins>**
  3. Example:
    ```javascript
    const { first, last, city } = bob;
    console.log(first, last, city); // Bob Sanders Chicago
    ```
  4. Missing properties return `undefined`:
    ```javascript
    const { zip } = bob; 
    console.log(zip); // undefined
    ```

---

- **Order doesn't matter in object destructuring**:
  - **`Arrays` <ins>depend on order</ins>, but `objects` <ins>do not</ins>**.
  - Example:
    ```javascript
    const { last, first } = bob;
    console.log(last, first); // Sanders Bob
    ```

- **Renaming properties** (using aliases):
  ```javascript
  const { last: surname } = bob;
  console.log(surname); // Sanders
  ```

---

- **Handling name conflicts**:
  - Avoid duplicate variable names by renaming:
    ```javascript
    const last = "some value";
    const { last: aliasLast } = bob;
    console.log(aliasLast); // Sanders
    ```

- **Destructuring nested objects**:
  - Example:
    ```javascript
    const { siblings: { sister: favoriteSibling } } = bob;
    console.log(favoriteSibling); // Jane
    ```

---

### Inside Functions:

```js
// In our daily lives, we do something like below

function printPerson(person){
  const {first, last} = person
  console.log(first, last); // bob sanders
}

printPerson(bob) // bob is our Main Object
```
----

**Using destructuring in functions**:

```javascript
function printPerson({ first, last, city, siblings: { sister } }) {
    console.log(first, last, city, sister);
}

printPerson(bob); // bob sanders chicago jane
```

  - Common in **React**:
    - Props are destructured directly in function parameters.

---

- **React and destructuring**:
  - Two approaches for accessing props:
    1. Destructure in the function body:
       ```javascript
       function Component(props) {
         const { first, last } = props;
         return <div>{first} {last}</div>;
       }
       ```
    2. Destructure directly in parameters:
       ```javascript
       function Component({ first, last }) {
         return <div>{first} {last}</div>;
       }
       ```

---

## Key Takeaways:
- Object destructuring simplifies accessing and renaming object properties.
- Nesting and aliasing are straightforward.
- Commonly used in React for props handling.

---
