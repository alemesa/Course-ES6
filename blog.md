## Notes of ES6.io Course

### 1. New Variables

```javascript
var // leaks outside {} curly brackets
let // scoped variables, stays inside curly brackets
const pi = 3.14;// constants
```

### 2. Arrow Functions

* Arrow functions are always anonymous functions

#### Cool functions with arrow functions

* **map()** - creates a new array with the results of calling a provided function on every element in the calling array.
```javascript
const race = '100m Dash';
const winners = ['Hunter Gath', 'Singa Song', 'Imda Bos'];
const win = winners.map((winner, i) => ({name: winner, race, place: i + 1}));
```

* **filter()** - method creates a new array with all elements that pass the test implemented by the provided function.
```javascript
const ages = [23,62,45,234,2,62,234,62,34];
const old = ages.filter(age => age >= 60);
// old = 62, 234, 62, 234, 62, 234
```

* **contains()** -  method determines whether one string may be found within another string, returning true or false as appropriate.
```javascript
// Using contains()
box.addEventListener('click', function() {
let first = 'opening';
let second = 'open';
if(this.classList.contains(first)) {
    [first, second] = [second, first];
}
this.classList.toggle(first);
});
```

* Defaults Arguments
```javascript
function calculateBill(total, tax = 0.13, tip = 0.15) {
    return total + (total * tax) + (total * tip);
}
const totalBill = calculateBill(100, undefined, 0.25);
console.log(totalBill);
```

* When not to use arrow functions

Arrow functions explicitely bind the keyword this to the block of code

### 3. Template Strings
```javascript
const name = 'Snickers';
const age = 2;
const sentence = `My dog ${name} is ${age * 7} years old.`;
```

* You can also put a template string inside another template string and run functions like .map() .filter() etc

```javascript
  const dogs = [
    { name: 'Snickers', age: 2 },
    { name: 'Hugo', age: 8 },
    { name: 'Sunny', age: 1 }
  ];

  const markup = `
    <ul class="dogs">
      ${dogs.map(dog => `
        <li>
          ${dog.name}
          is
          ${dog.age * 7}
        </li>`).join('')}
    </ul>
  `;
```

* Ternary Operator? sure...
```javascript
${song.featuring ? `(Featuring ${song.featuring})` : ''}
```

* **forEach()** - is like map() but the difference is that instead of returning a new array modify the items only
```javascript
strings.forEach((string, i) => {
    str += `${string} <span contenteditable class="hl">${values[i] || ''}</span>`;
});
```

* **reduce()** - function against an accumulator and each element in the array from left to right
```javascript
const total = [0, 1, 2, 3].reduce((sum, value) => sum + value, 1);
// total is 7
```

### 4. Additional String Methods

* **startsWith()**
* **endsWith()**
* **includes()** -> like **contains()**
* **repeat()**

self-explanatory

### 5. Destructuring

* Destructuring Objects 🔥
```javascript
const person = {
    first: 'Wes',
    last: 'Bos',
    country: 'Canada',
    city: 'Hamilton',
    twitter: '@wesbos'
  };

  const { first, last, twitter } = person;
```

* Destructuring Arrays 🔥
```javascript
const details = ['Wes Bos', 123, 'wesbos.com'];
const [name, id, website] = details;

// another example
const data = 'Basketball,Sports,90210,23,wes,bos,cool';
const [itemName, category, sku, inventory] = data.split(',');

// another example using rest
const team = ['Wes', 'Harry', 'Sarah', 'Keegan', 'Riker'];
const [captain, assistant, ...players] = team;
```

* Swapping variables
```javascript
let inRing = 'Hulk Hogan';
let onSide = 'The Rock';

[inRing, onSide] = [onSide, inRing];
```

* Destructuring 

```javascript
function convertCurrency(amount) {
    const converted = {
        USD: amount * 0.76,
        GPB: amount * 0.53,
        AUD: amount * 1.01,
        MEX: amount * 13.30
    };
    return converted;
}

const { USD, GPB, AUD, MEX } = convertCurrency(100);
```

### 6. Iterables and Looping

* for of loop

```javascript
for(const cut of cuts){
    console.log(cut);
}

//another example
const ps = document.querySelectorAll('p');
for (const paragraph of ps) {
    paragraph.addEventListener('click', function() {
        console.log(this.textContent);
    });
}
```

### 7. An Array of Array Improvements

* **Array.from()** - convert a Nodelist to array

```javascript
  function sumAll() {
    //arguments use 👀  
    const nums = Array.from(arguments);
    return nums.reduce((prev, next) => prev + next, 0);
  }

  sumAll(2, 34, 23, 234, 234, 234234, 234234, 2342);
```
* **Array.of()** - create an array with the arguments passed

```javascript
  const ages = Array.of(12,4,23,62,34);
  console.log(ages);
```
* **Array.find()** - method returns the value of the first element in the array that satisfies the provided testing function.

Let's say that I have a bunch of objects and we need to filter
```javascript
const code = 'VBgtGQcSf';   
// loops throught each post until it finds a true condition in this case post.code === code
const post = posts.find(post => post.code === code);
```
* **Array.findIndex()** - method that returns the index
```javascript
const postIndex = posts.findIndex(post => post.code === code);
```
* **Array.some()** - self-explanatory 🙄
```javascript
const ages = [32, 15, 19, 12];
// 👵👨 is there at least one adult in the group?
const adultPresent = ages.some(age => age >= 18);
console.log(adultPresent);
```
* **Array.every()** - self-explanatory 🙄
```javascript
const ages = [32, 15, 19, 12];
// 🍻 is everyone old enough to drink?
const allOldEnough = ages.every(age => age >= 19);
console.log(allOldEnough);
```

### 8. Say Hello to ...Spread and ...Rest

* **...Spread** - Takes every iterable item and apply it to the contained element

```javascript
const featured = ['Deep Dish', 'Pepperoni', 'Hawaiian'];
const specialty = ['Meatzza', 'Spicy Mama', 'Margherita'];

// add veggie in between both array
const pizzas = [...featured, 'veg', ...specialty];
// copy array 🔥
const fridayPizzas = [...pizzas];

let word = "hello";
let spreadWords = [...word];
// spreadWords h,e,l,l,o 
```

* Another way to convert NodeList to array is by spreading 
```javascript
const people = Array.from(document.querySelectorAll('.people p'));
const people = [...document.querySelectorAll('.people p')];
```

* Destructuring with ...rest
```javascript
const runner = ['Wes Bos', 123, 5.5, 5, 3, 6, 35];
const [name, id, ...runs] = runner;
console.log(name, id, runs);
```

### 10. Promises

* Some **concepts** to understand:
    * Use for JSONs usually, we're gonna use fetch()
    * Promise is something that would happen in the future but probably not inmediatly
    * JS is async which means that it doesn't wait for the previous line to run the next one

* Basic Promise 

```javascript
const postsPromise = fetch('json-url.example');

postsPromise
  .then(data => data.json()) // runs the next operation
  .then(data => { console.log(data) }) // runs the next operation
  .catch((err) => {
    console.error(err); // callback for errors
  })
```

* Building our own promises

```javascript
const promise = new Promise((resolve, reject) => {
    resolve('Wes is cool');
    reject(Error('Wes is not cool'));
});

promise.then(data => {
    console.log(data); // Wes is cool (data back)
}).catch(err => {
    console.log(err); // Wes is not cool (error message)
})
```

* Working with multiple Promises (example)
```javascript
const postsPromise = fetch('http://wesbos.com/wp-json/wp/v2/posts');
const streetCarsPromise = fetch('http://data.ratp.fr/api/datasets/1.0/search/?q=paris');

Promise
.all([postsPromise, streetCarsPromise]) //array of promises
.then(responses => {
    return Promise.all(responses.map(res => res.json()))
})
.then(responses => {
    console.log(responses);
});
```

### 11. Symbols
```javascript
// symbols are like unique identifiers
  const wes = Symbol('Wes');
  const person = Symbol('Wes');

  const classRoom = {
    [Symbol('Mark')] : { grade: 50, gender: 'male' },
    [Symbol('olivia')]: { grade: 80, gender: 'female' },
    [Symbol('olivia')]: { grade: 80, gender: 'female' },
  };

  for (const person in classRoom) {
    console.log(person); //this won't work, symbols are enumerable, you're not able to loop through them
  }

  const syms = Object.getOwnPropertySymbols(classRoom);
  const data = syms.map(sym => classRoom[sym]);
  console.log(data);
```

### 13. Javascript Tooling

* Import

```javascript
// import the apiKey const
import apiKey from 'data' // variable
import { name, language } from 'data'; // with destucturing 
import sayHello from 'data' // function
```

* Export
```javascript
// filename = data
const apiKey = "0012ASD"
export default apiKey // every module could have only one default export

export const name = "Wes";
export const language = "javascript"
export function sayHello(){
    console.log("Hello");
}
```

### 15. Classes

### 20. Async + Await Flow Control

### 21. ES7, ES8 + Beyond





