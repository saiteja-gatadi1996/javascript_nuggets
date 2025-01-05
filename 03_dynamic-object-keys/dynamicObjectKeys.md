# Extract the Keys from an object

👉 [Watch on Youtube](https://youtu.be/_qxCYtWm0tw?si=S5iRmUCH6ZHI7tRv)

----

```js
// dot notation
const person = {
    name: 'saiteja'
}
person.age = 28;
console.log(person.name) //saiteja
console.log(person) 
```


```js
// square bracket notation

const items = {
    'featured-items': ['item1', 'item2']
}

console.log(items.featured-items) // doesn't work

console.log(items['featured-items']) // ['item1', 'item2']

console.log(person['name']) //saiteja
```

----

```js
let appState = 'loading';
appState = 'error';

const keyName = 'computer';

const app = {
    [appState] : true;
}

app[keyName] = 'apple';

console.log(app); // {error: true, computer: 'apple'}

```

```js
const state = {
    loading: true,
    name: '',
    job: ''
}


function updateState(key, value){
    state[key] = value
}


updateState('name', 'gatadi')
console.log(state) //{loading: true, name: 'gatadi', job: ''}



updateState('job', 'developer')
updateState('loading', false)

console.log(state) //{loading: false, name: 'gatadi', job: 'developer'}
```