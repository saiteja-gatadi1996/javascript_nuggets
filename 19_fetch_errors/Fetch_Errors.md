
# JavaScript Nuggets: Fetch Errors

[YouTube Video Link](https://www.youtube.com/watch?v=otrSJg1yeeo)

---

- **Fetch Errors**
  - What they are.
  - Common gotchas.

Fetch is a **browser API** that allows us to perform AJAX requests without additional libraries like Axios. It returns a **promise**.

#### Example of Fetch:
```javascript
async function fetchData() {
    try {
        const response = await fetch('https://example.com/api');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
fetchData();
```

Added features:

- A button to trigger the fetch request.
- Data fetched only on button click.

#### Correct URL Output:

- **Console Output**: Array of 5 items (e.g., tours for a React project).

#### Incorrect URL Handling:

If the endpoint doesn't exist:

```javascript
const response = await fetch('https://wrong-url.com');
const data = await response.json(); // Error occurs here
```

**Why?** The `json()` method throws an error when it tries to parse invalid data.

#### Fetch Gotchas:

- **400s/500s Errors**:
  - Fetch doesn't consider these as errors.
  - It only throws errors for **network issues**.

Example:

```javascript
const response = await fetch('https://wrong-url.com');
console.log(response.status); // 404
console.log(response.statusText); // Not Found
```

- You'll still get a response object, even if it's not the desired data.

#### Network Error Simulation:

1. Block the request URL in the **Network Tab** of developer tools.
2. Fetch the URL.

**Console Output**: `TypeError: Failed to fetch`.

This error is caught in the `catch` block since the resource cannot be fetched.

#### Fixing Fetch Errors:

Handle errors manually using the `ok` property of the response:

```javascript
async function fetchData() {
    try {
        const response = await fetch('https://example.com/api');
        if (!response.ok) {
            const message = `Error: ${response.status} - ${response.statusText}`;
            throw new Error(message);
        }
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
fetchData();
```

**Final Output**:

If there's an error, the console displays:

```
Error: 404 - Not Found
```

### Summary:

- **Fetch** only cares about network errors.
- For HTTP status errors (e.g., 404, 500), handle them manually by checking `response.ok`.
- Always validate your responses to ensure your application remains robust.
