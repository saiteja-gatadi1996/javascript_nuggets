
# JavaScript Nuggets - Timestamps

**YouTube Video**: [JavaScript Nuggets - Timestamps](https://www.youtube.com/watch?v=-Sbd08tTbAA)

- **Topic**: Timestamps.
  - Utilized while working on a Node project.
  - Realized its utility and decided to share it.
- **Setup**:
  - Using an extension called `qoca.js` to display logs in the document.

### **Working with Date Objects** 
- Running `new Date()` provides a lot of information:
  ```javascript
  const currentDate = new Date();
  console.log(currentDate);
  ```
- **Unix Time**:
  - Measures time elapsed since midnight, January 1st, 1970 (in milliseconds).
  - Example: `Date.now()`.
  ```javascript
  const unixTime = Date.now();
  console.log(unixTime);
  ```

### **Getting Timestamps** 
- Three ways to get timestamps:
  1. `Date.now()`.
  2. `new Date().getTime()`.
  3. `new Date().valueOf()`.
- Timestamps are in milliseconds, and values increase over time.

### **Using Timestamps with SetTimeout** 
- Example showing timestamps increasing with a delay:
  ```javascript
  setTimeout(() => {
    console.log(Date.now());
  }, 1000); // 1 second delay
  ```
- Demonstrates absolute values useful for calculations.

### **Use Case 1: Generating Unique IDs** 
- Using `Date.now()` as a simple unique ID generator:
  ```javascript
  const people = [];
  people.push({ id: Date.now(), name: "Peter" });
  setTimeout(() => {
    people.push({ id: Date.now(), name: "John" });
    console.log(people);
  }, 1000);
  ```

### **Use Case 2: Creating Dates with Timestamps** 
- Using timestamps to create specific dates:
  ```javascript
  const timestamp = Date.now();
  const specificDate = new Date(timestamp);
  console.log(specificDate);
  ```
- Example for creating an expiration date:
  ```javascript
  const now = Date.now();
  const expirationDate = new Date(now + 86400000); // Adds 1 day in milliseconds
  console.log(expirationDate);
  ```

### **Use Case 3: Finding Difference Between Dates** 
- Calculating the difference between two dates:
  ```javascript
  const firstDate = new Date("2021-09-27");
  const secondDate = new Date("2021-09-28");
  const diffInMilliseconds = secondDate.getTime() - firstDate.getTime();
  const diffInMinutes = diffInMilliseconds / (1000 * 60); // Convert to minutes
  console.log(diffInMinutes);
  ```

### **Summary** 
- Timestamps are highly useful for:
  - Calculating differences between dates.
  - Setting expiration dates (e.g., cookies).
  - Generating unique IDs.

---

*Hope you found this video helpful. See you in the next one!*
