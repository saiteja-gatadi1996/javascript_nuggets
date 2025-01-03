# Javascript Nuggets - Async / Await

👉 [Watch on Youtube](https://youtu.be/iHrVo5fvmzE?si=VmDFb5PenaIbFp6n)

## **Overview**

### **Main Takeaway**
- **Async/Await** allows us to write asynchronous code in a synchronous fashion.
- Instead of endlessly nesting callbacks, Async/Await provides a cleaner and more readable approach.

---

## **Key Points**

### **Understanding `async` and `await`**
- `await` always waits until the promise is settled.
- To use `await`, the function must be declared as `async`.
- An `async` function **always** returns a promise.

---

## **Examples**

### **General Example**

#### **Arrow Function with `async`**
```javascript
const example = async () => {
  return "Hello there";
};

console.log(example()); // Logs: Promise {<fulfilled>: "Hello there"}
```

- The promise is immediately fulfilled because we are returning a value.

#### **Traditional Function with `async` and `await`**
```javascript
async function someFunc() {
  const result = await example();
  console.log(result); // Logs: "Hello there"
}

someFunc();
```

- **Key Point:** `await` waits for the promise to settle before proceeding.

---

### **Assigning `await` Result to a Variable**
- If the promise doesn’t return a value, no need to assign it to a variable.
- Example:

```javascript
await example();
console.log("Hello World");
```

- **Output Sequence:**
  - "Hello there"
  - "Hello World"

---

## **Real-Life Example**

### **Fetching Data Example**

#### **Dataset**
```javascript
const users = [
  { id: 1, name: "John" },
  { id: 2, name: "Susan" },
  { id: 3, name: "Anna" }
];

const articles = [
  { userId: 1, article: "Article 1" },
  { userId: 2, article: "Article 2" },
  { userId: 3, article: "Article 3" }
];
```

#### **Functions**
```javascript
function getUser(name) {
  return new Promise((resolve, reject) => {
    const user = users.find(user => user.name === name);
    if (user) {
      resolve(user);
    } else {
      reject("No such user found");
    }
  });
}

function getArticles(userId) {
  return new Promise((resolve, reject) => {
    const userArticles = articles.filter(article => article.userId === userId);
    if (userArticles.length) {
      resolve(userArticles);
    } else {
      reject("No articles found for this user");
    }
  });
}
```

#### **Chaining `.then()`**
```javascript
getUser("Susan")
  .then(user => {
    console.log(user); // Logs user object
    return getArticles(user.id);
  })
  .then(articles => {
    console.log(articles); // Logs articles array
  })
  .catch(error => {
    console.log(error);
  });
```

---

###  **Using `async/await`**

```javascript
async function getData() {
  try {
    const user = await getUser("Susan");
    console.log(user);

    const articles = await getArticles(user.id);
    console.log(articles);
  } catch (error) {
    console.log(error);
  }
}

getData();
```

- **Advantages:**
  - More readable code.
  - Avoids chaining `.then()`.

---

## **Error Handling**

### **Using `try...catch` Block**

```javascript
async function getData() {
  try {
    const user = await getUser("John");
    const articles = await getArticles(user.id);
    console.log(articles);
  } catch (error) {
    console.log(error);
  }
}
```

- **Benefits:**
  - Clean separation of success and error handling.
  - Avoids nesting callbacks or chaining multiple `.catch()`.

---

## **Final Thoughts**

### **Why Use `async/await`?**
- **Simplifies asynchronous code:**
  - No need for endless nesting or chaining `.then()`.
  - Code looks synchronous but behaves asynchronously.

---

