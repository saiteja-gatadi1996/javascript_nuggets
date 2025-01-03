
# JavaScript Nuggets: Optional Chaining

[**YouTube Video Link**](https://www.youtube.com/watch?v=PuEGrylM1x8)

---

**optional chaining**, which offers straightforward syntax for working with deeply nested properties.  

Imagine this scenario:  
- You have an array.
- Inside the array, you have objects.
- Each object represents a person.

**Properties:**  
- A person has a `name` property.  
- A `location` property, which is an object.  
- Inside `location`, there's a `timezone` property, which again is an object.  
- Inside `timezone`, there's an `offset` property.  

However, **not all objects have this `timezone` property**!  

---

When iterating over the list, attempting to access `offset` in an object without `timezone` causes an error.  

This is where **optional chaining** comes in handy.  
If you're wondering about the structure, I got this example from the **Random User API**. Here's what happens:  
- **Random User API** provides data in a similar structure.
- I used that structure for this example.  

Instead of setting up `fetch`, let's imagine we fetched the data and want to process it. Typically, you'd iterate over the list and display something. Here, I’ll demonstrate:  

---

Using a `forEach` loop:  

```javascript
people.forEach((person) => {
  console.log(person.name); // Works fine since the `name` property exists
});
```

Now let's make it more interesting:  

```javascript
// Accessing deeply nested properties
console.log(person.location.timezone.offset);
```

For the second object, this causes an error:  
> **"Cannot read property 'offset' of undefined"**  

Why?  
- The `timezone` property doesn't exist for the second object.  
- JavaScript stops execution due to the error.  

---

**Solution Before Optional Chaining:** Using the **AND (`&&`) operator**.  

```javascript
if (true && "Hello World") {
  console.log("Hello World"); // Logs "Hello World"
}
```

If the first value is `false`:  

```javascript
if (false && "Hello People") {
  console.log("Hello People"); // Doesn't log anything, returns `false`
}
```

For our case:  

```javascript
if (person.location && person.location.timezone && person.location.timezone.offset) {
  console.log(person.location.timezone.offset);
}
```

- This checks each nested property before accessing `offset`.  
- Avoids errors but requires **verbose code**.  

---

**Introducing Optional Chaining (`?.`):**  

```javascript
console.log(person?.location?.timezone?.offset);
```

- **Behavior:** If a property doesn't exist, it returns `undefined` without throwing an error.  
- Simplifies the syntax compared to the `&&` operator approach.  

Example:  

```javascript
console.log(person?.location?.timezone?.offset || "Default Value");
```

- Adds a **default value** when a property is `undefined`.  

---

### Key Takeaways

- **Optional chaining** simplifies accessing deeply nested properties.
- Prevents errors when properties are `undefined`.
- Use the `||` operator for default values.

---
