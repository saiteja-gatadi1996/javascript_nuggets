
# JavaScript Nuggets: Callback Functions

[Watch in YouTube](https://www.youtube.com/watch?v=GWq0XETTOTk)

---

- **Callback Functions**
  - What they are.
  - Why they're important.
  - How they work.

> A **callback function** is a function that we pass in as an argument and execute it later.

Assume you're comfortable with this code:

```javascript
function makeUppercase(value) {
    console.log(value.toUpperCase());
}
makeUppercase("peter");
```

Output: `PETER`

Now, let's see how a **callback function** works:

#### Example Code:

```javascript
function handleName(name, callback) {
    const fullName = `${name} Smith`;
    callback(fullName);
}
function makeUppercase(value) {
    console.log(value.toUpperCase());
}
handleName("peter", makeUppercase);
```

Output: `PETER SMITH`

**Important Note:** Avoid invoking the callback directly in the function call.

Incorrect:

```javascript
handleName("peter", makeUppercase());
```

Correct:

```javascript
handleName("peter", makeUppercase);
```
-----

#### Example: Reverse String Callback

```javascript
function reverseString(value) {
    console.log(value.split("").reverse().join(""));
}
handleName("Peter", reverseString);
```

Output: `htimS reteP`

Callback functions make applications **flexible** and **dynamic**. You can:

1. Pass different callback functions.
2. Add custom logic.

----

#### Example: Inline Function as Callback

```javascript
handleName("susan", function(value) {
    console.log(value);
});
```
----

#### Arrow Function Example:

```javascript
handleName("Susan", (value) => console.log(value));
```

Output: `Susan Smith`

**Why Learn Callback Functions?**

- They're **everywhere** in JavaScript:
  - **Array Methods**: `map`, `filter`, `find`, `reduce`.
  - **setTimeout**.
  - **Event Listeners**.

#### Event Listener Example:

```javascript
const btn = document.querySelector(".btn");
btn.addEventListener("click", function() {
    console.log("Hello World");
});
```

Output: `Hello World` (on button click).

Callback functions enable:

- **Deferred Execution**: Decide when a function gets invoked.
- **Flexibility**: Libraries like React and Node.js extensively use them.

---

