
# JavaScript Nuggets: FormData API

[Watch on YouTube Video](https://www.youtube.com/watch?v=5-x4OUM-SP8)

---

The **FormData API** is a powerful interface to construct a set of **key-value pairs** representing form fields and their values.

- It's useful for handling forms with multiple inputs.
- Avoids the need to manually retrieve values for each input.

#### Typical Form Handling Without FormData:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Javascript Nuggets</title>
    <link rel="stylesheet" href="./local.css" />
    <style></style>
  </head>
  <body>
    <form class="form">
      <h4>formData API</h4>
      <!-- name -->
      <div class="form-row">
        <label class="form-label" for="name">name</label>
        <input
          type="text"
          name="name"
          id="name"
          class="form-input name-input"
        />
      </div>
      <!-- email -->
      <div class="form-row">
        <label class="form-label" for="email">email</label>
        <input
          type="email"
          name="email"
          id="email"
          class="form-input email-input"
        />
      </div>
      <!-- password -->
      <div class="form-row">
        <label class="form-label" for="password">password</label>
        <input
          type="password"
          name="password"
          id="password"
          class="form-input password-input"
        />
      </div>
      <button type="submit" class="btn btn-block">register</button>
    </form>
    <script src="./app.js"></script>
  </body>
</html>
```

```javascript
const form = document.querySelector('.form');
const nameInput = document.querySelector('.name-input');
const emailInput = document.querySelector('.email-input');
const passwordInput = document.querySelector('.password-input');

form.addEventListener('submit', (e) => {
  e.preventDefault();
  const nameValue = nameInput.value;
  const emailValue = emailInput.value;
  const passwordValue = passwordInput.value;
  // check for empty values
  if (!nameValue || !emailValue || !passwordValue) {
    console.log('please provide values');
    return;
  }
  // do something
  console.log(nameValue, emailValue, passwordValue);

  // after that clear values
  nameInput.value = '';
  emailInput.value = '';
  passwordInput.value = '';
});
```

While effective, this becomes tedious for forms with many inputs.

#### Using FormData:

```javascript
const form = document.querySelector('.form');
// also valid approach
// const formData = new FormData(form);

form.addEventListener('submit', (e) => {
  e.preventDefault();
  const formData = new FormData(e.currentTarget);
  // won't directly return values
  console.log(formData);
});
```

- Use `new FormData(event.currentTarget)` to create a FormData object.
- The result is an array of arrays: `[["key", "value"], ["key", "value"]]`.

#### Accessing Values in FormData:

```javascript

  // spread out - entries, values, keys
  const entries = [...formData.entries()];
  console.log(entries);
  const values = [...formData.values()];
  console.log(values);
  const keys = [...formData.keys()];
  console.log(keys);
```

- Use `entries()`, `values()`, or `keys()` methods to retrieve data.

#### Iterating with `for...of`:

```javascript
for (const [key, value] of formData) {
    console.log(`${key}: ${value}`);
}
```

- The `for...of` loop can destructure keys and values directly.

#### Accessing Specific Values:

Ensure inputs have a `name` attribute:

```javascript
console.log(formData.get('name')); // Retrieves value of 'name'
```

- **Important**: The `name` attribute is required for FormData to function properly.

#### Modifying FormData:

- **Add new data**:

```javascript
formData.append('testKey', 'testValue');
```

- **Remove existing data**:

```javascript
formData.delete('name');
```

- **Check for a key**:

```javascript
console.log(formData.has('name')); // true or false
```

#### Converting to a JSON Object:

Use `Object.fromEntries`:

```javascript
const dataObject = Object.fromEntries(formData.entries());
console.log(dataObject);
```

- Converts the array of arrays into a plain JavaScript object.

#### Typical Form Setup:

```javascript
const form = document.querySelector('.form');

form.addEventListener('submit', (event) => {
    event.preventDefault();
    const formData = new FormData(event.currentTarget);

    // Check for empty values
    const values = [...formData.values()];
    if (values.includes('')) {
        console.log('Empty value detected!');
        return;
    }

    // Convert to object and process
    const dataObject = Object.fromEntries(formData.entries());
    console.log(dataObject);

    // Reset form
    form.reset();
});
```

### Summary:

- **FormData** simplifies working with forms, especially those with many inputs.
- Provides methods to manipulate, retrieve, and convert form data.
- Essential for modern JavaScript applications.

---
