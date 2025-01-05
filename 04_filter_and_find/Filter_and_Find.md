
# Filter and Find

👉 **[Watch on Youtube](https://www.youtube.com/watch?v=KeYxsev737s)**

---

## Filter 
  - Returns a new array.  
  - The size of the new array depends on conditions.  
  - Example:  
    ```js
    // 10 items → Condition matches 5 → New array has 5 items.
    // No matches → Empty array.
    ```

**Key Notes:**  
- Filter manipulates the size of the new array.  
- With `map`, the size of the new array is always the same.

---

```js
// Original Array
const people = [
  { name: 'bob', age: 20, position: 'developer' },
  { name: 'peter', age: 25, position: 'designer' },
  { name: 'susy', age: 30, position: 'the boss' },
  { name: 'anna', age: 35, position: 'intern' },
];
```

---

**Filtering Young People**  
```js
const youngPeople = people.filter((person) => {
  if(person.age<=25){
    return person
  }
});

// Output: We are filtering with people who are less than or equal to 25 age group
[
  { name: 'bob', age: 20, position: 'developer' },
  { name: 'peter', age: 25, position: 'designer' }
]
```  
- **Callback Function Logic:**  
  - If `true` → Return the item.  
  - If `false` → Skip the item.

---

**Filtering with Shortcuts**  
- Instead of using an `if` block, directly return the condition:  
```js
const youngPeople = people.filter(person => person.age < 30);

// Output:
[
  { name: 'bob', age: 20, position: 'developer' },
  { name: 'peter', age: 25, position: 'designer' }
]
```

---

**Using Arrow Functions and Implicit Returns**  
- Simplify the filter process:  
```js
// filtering out the developer from original array
const developers = people.filter(person => person.position === 'developer');

//Output:
[ { name: 'bob', age: 20, position: 'developer' } ]

```  
**Notes:**  
- Arrow functions can use **implicit `return`** for cleaner code.  
- Parameter names are anything (e.g., `banana` instead of `person`).

---

**Filtering Non-Objects**  
- For arrays of strings, you don’t check object properties:  
```js
const items = ['apple', 'orange', 'banana'];
const filtered = items.filter(item => item === 'orange');

// Output: 
[ 'orange' ]
```

---

**Handling No Matches**  
- If no items match the condition:  
```js
const seniorDevs = people.filter(person => person.position === 'senior');
```  
- Output: `[]` (empty array).

---

## **Find Method**  
- Works similarly to filter **but returns a single instance**.  
- <ins>**First match is returned**</ins>; if no match, returns `undefined`.

---

**Example: Finding a Specific Person**  
```js
const peter = people.find(person => person.name === 'peter');

// Output
{ name: 'peter', age: 25, position: 'designer' }
```  

---

**Find with Strings**  
```js
const fruits = ['orange', 'pear', 'lemon'];
const lemon = fruits.find(fruit => fruit === 'lemon');

//Output: 'lemon'
```

---

**No Matches with Find**  
- If no match is found:  
```js
const oldPerson = people.find(person => person.age > 35);
```  
- Result: `undefined`.

---

**Handling Multiple Matches**  
- ***Find always returns the first match:***  
```js
const randomPerson = people.find(person => person.age < 35);

// Output: 
{ name: 'bob', age: 20, position: 'developer' }
```  
---

**Differences Between Find and Filter**  
- `Find`: Directly access properties of the single instance:  
```js
const peter = people.find(person => person.name === 'peter');
const peterPosition = peter.position;

//Output: 'designer;
```  
- `Filter`: Results are always arrays, even with one match:  
```js
const anna = people.filter(person => person.name === 'anna');

const annaPosition = anna[0].position;
```  
---

**Summary:**  
- Use `find` for single instances.  
- Use `filter` for arrays.

---

## Conclusion  
- Both `filter` and `find` are powerful array methods in JavaScript.  
- Choose based on your specific requirements and expected outputs.
