## Notes of ES6.io Course

### 1. New Variables

```javascript
var // leaks outside {} curly brackets
let // scoped variables, stays inside curly brackets
const pi = 3.14;// constants
```

### 2. Arrow Functions

* Arrow functions are always anonymous functions

* Cool functions with arrow functions
```javascript
// Using map()
const race = '100m Dash';
const winners = ['Hunter Gath', 'Singa Song', 'Imda Bos'];
const win = winners.map((winner, i) => ({name: winner, race, place: i + 1}));

// Using filter()
const ages = [23,62,45,234,2,62,234,62,34];
const old = ages.filter(age => age >= 60);
```

* Contains()
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


### 4. Additional String Methods

### 5. Destructuring

### 6. Iterables and Looping