# FETCH API

```js
// Fetch API -  Browser API for HTTP (AJAX) Requests
// Default - GET Requests, supports other methods as well
// Returns Promise

const url = 'https://www.course-api.com/react-tours-project';

// console.log(fetch(url))

// fetch(url)
//   .then((resp) => resp.json())
//   .then((data) => console.log(data))
//   .catch((err) => console.log(err))

const getTours = async () => {
  try {
    const tours = await fetch(url);
    const data = await tours.json();
    console.log(data); // Logs the fetched data
  } catch (error) {
    console.error('Error fetching tours:', error); // Handles any errors
  }
};

getTours()
  .then((data) => {
    console.log(data); // Logs the fetched data
  })
  .catch((error) => {
    console.error('Error fetching tours:', error); // Handles any errors
  });

```