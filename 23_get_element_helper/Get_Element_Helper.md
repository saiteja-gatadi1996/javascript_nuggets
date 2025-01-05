
# JavaScript Nuggets: Get Element Helper

[Watch on Youtube](https://www.youtube.com/watch?v=bUa9uYFaa9M)

---


**Scenario:**  
- `index.html` contains:

```html
<body>
    <h1>Get Element Helper</h1>
    <h3 class="heading">random list</h3>
    <ul>
      <li class="list-item">first item</li>
      <li class="list-item">second item</li>
    </ul>
    <script src="./app.js"></script>
  </body>
```

  - A heading with a `heading` class.
  - A list where each item has a `list-item` class.
- **Goal:** Select the heading and list items.  

---

Typically, you would use `querySelector` and `querySelectorAll`:  

```javascript
const heading = document.querySelector('.heading'); // Select heading
const listItems = document.querySelectorAll('.list-item'); // Select all list items
```

**Problem:**  
- If the selector is incorrect, you'll get `null` or an empty `NodeList`.
- Debugging becomes harder in larger applications.  

---

**Introducing the `getElement` Helper Function:**  

```javascript
const getElement = (selector) => {
  const element = document.querySelector(selector);
  if (element) {
    return element;
  }
  throw new Error(`Please double-check the selector: "${selector}"`);
};
```

**Usage Example:**  

```javascript
console.log(getElement('.heading')); // Logs the heading
console.log(getElement('.invalid-selector')); // Throws an error
```

---

**Handling Lists with `querySelectorAll`:**  
If selecting lists, an empty array is returned for invalid selectors.  

```javascript
const getElements = (selector) => {
  const elements = [...document.querySelectorAll(selector)];
  if (elements.length < 1) {
    throw new Error(`No elements found for selector: "${selector}"`);
  }
  return elements;
};
```

**Example:**  

```javascript
console.log(getElements('.list-item')); // Logs the list items
console.log(getElements('.invalid-selector')); // Throws an error
```

---

**Combining Logic into a Single Function:**  

```javascript
const getElementOrElements = (selector, isList = false) => {
  const elements = isList
    ? [...document.querySelectorAll(selector)]
    : document.querySelector(selector);
  if (isList && elements.length < 1) {
    throw new Error(`No elements found for selector: "${selector}"`);
  }
  if (!isList && !elements) {
    throw new Error(`Please double-check the selector: "${selector}"`);
  }
  return elements;
};
```

**Usage:**  

```javascript
console.log(getElementOrElements('.heading')); // Logs single element
console.log(getElementOrElements('.list-item', true)); // Logs list items
console.log(getElementOrElements('.invalid-selector', true)); // Throws an error
```

---

**Final Optimization:**  
Combine multiple checks into a single line:  

```javascript
const getElementOrElements = (selector, isList = false) => {
  const elements = isList
    ? [...document.querySelectorAll(selector)]
    : document.querySelector(selector);
  if ((isList && elements.length < 1) || (!isList && !elements)) {
    throw new Error(`Invalid selector: "${selector}"`);
  }
  return elements;
};
```

---

### Key Takeaways

- Use a helper function to simplify element selection in vanilla.js.
- Provides immediate feedback if the selector is invalid.
- Reduces debugging time in larger applications.

---
