# ES6 - Compact

This is a collection of exercises and features of **ECMAScript6 (ES6)**. 
I used this compact to understand new features and improve my abilities with **Javascript** as well as ES6. Maybe can be helpful for you too.
If you need help with solutions, contact me or search on [MDN Documentation](https://developer.mozilla.org/en-US/) or at the programmers' best friend [Stack Overflow](https://stackoverflow.com/).

## Getting Started

This compact is organized as follows:

* Feature Explanation
* Exercises (external links)
* Solutions

## Built With

* [Marijn Haverbeke ES6 Exercises](http://marijnhaverbeke.nl/talks/es6_falsyvalues2015/exercises/)
* [ES6 Katas](http://es6katas.org/)
* [ES6 Features](http://es6-features.org/)
* [Udacity ES6 Course](https://br.udacity.com/course/es6-javascript-improved--ud356)
* [ES6 Summary](https://github.com/zsolt-nagy/es6-summary)

## Summary

* [Variables and Scope](#variable-and-scope)
* [Template Literals](#template-literals)
* [Destructuring](#destructuring)
* [Iteration (For...of) Loops](#iteration-(for...of)-loops)
* [Spread Operator](#spread-operator)
* [Arrow Functions](#arrow-functions)
* [Default Parameters](#default-parameters)
* [Class and Subclass](#class-and-subclass)

# Variable and Scope

* **Let** - Restricts the scope of the variable to the current block
* **Const** - Works as *Let*, but value cannot be modified.
```javascript
let x = 5
x = 7
const PI = 3.141593
```

### Exercise 1: [**Translate from ES5 to ES6**](http://marijnhaverbeke.nl/talks/es6_falsyvalues2015/exercises/#Closing_over_scope) - [Solution Here](#solution-1)

### Exercise 2: [**Fix the Bug**](http://marijnhaverbeke.nl/talks/es6_falsyvalues2015/exercises/#Hoist_the_class) - [Solution Here](#solution-2)

### Exercise 3: **Translate Code (Udacity)** - [Solution Here](#solution-3)
```javascript
var CHARACTER_LIMIT = 255;
var posts = [
	"#DeepLearning transforms everything from self-driving cars to language translations. AND it's our new Nanodegree!",
	"Within your first week of the VR Developer Nanodegree Program, you'll make your own virtual reality app",
	"I just finished @udacity's Front-End Web Developer Nanodegree. Check it out!"
];

// prints posts to the console
function displayPosts() {
	for (var i = 0; i < posts.length; i++) {
		console.log(posts[i].slice(0, CHARACTER_LIMIT));
	}
}
displayPosts();
```

### Solution 1:
```javascript
const callbacks = []
for (let i = 0; i < 10; i++) {
  callbacks.push(function() { console.log(i) })
}
callbacks[2]()
// 2
```

### Solution 2:
```javascript
class Something {}
let s = new Something()
```

### Solution 3:
```javascript
const CHARACTER_LIMIT = 255;
const posts = [
	"#DeepLearning transforms everything from self-driving cars to language translations. AND it's our new Nanodegree!",
	"Within your first week of the VR Developer Nanodegree Program, you'll make your own virtual reality app",
	"I just finished @udacity's Front-End Web Developer Nanodegree. Check it out!"
];

// prints posts to the console
function displayPosts() {
	for (let i = 0; i < posts.length; i++) {
		console.log(posts[i].slice(0, CHARACTER_LIMIT));
	}
}
displayPosts();
``` 

# Template Literals
A template string, is wrapped in ` (backticks) instead of **'** or **"**. By default, behaves like a normal string just surrounded by backticks, however, can evaluate variables, which are wrapped in **"${" and "}"** and any expression, wrapped inside **"${...}"**.
```javascript
var customer = { name: "Foo" }
var card = { amount: 7, product: "Bar", unitprice: 42 }
var message = `Hello ${customer.name},
want to buy ${card.amount} ${card.product} for
a total of ${card.amount * card.unitprice} bucks?`
```

### Exercise 4: [**Code using es6**](http://marijnhaverbeke.nl/talks/es6_falsyvalues2015/exercises/#The_tooling_team) - [Solution Here](#solution-4)

```javascript
// Produce the following message:
//There are 4 people on the tooling team.
//Their names are Jennie, Ronald, Martin, Anneli.
//2 of them have a senior role.
const teamName = "tooling"
const people = [{name: "Jennie", role: "senior"},
                {name: "Ronald", role: "junior"},
                {name: "Martin", role: "senior"},
                {name: "Anneli", role: "junior"}]

let message = YOUR_CODE_HERE

console.log(message)
```
### Exercise 5: **Translate from es5 to es6 (Udacity)** - [Solution Here](#solution-5)
```javascript
const cheetah = {
    name: 'Cheetah',
    scientificName: 'Acinonyx jubatus',
    lifespan: '10-12 years',
    speed: '68-75 mph',
    diet: 'carnivore',
    summary: 'Fastest mammal on land, the cheetah can reach speeds of 60 or perhaps even 70 miles (97 or 113 kilometers) an hour over short distances. It usually chases its prey at only about half that speed, however. After a chase, a cheetah needs half an hour to catch its breath before it can eat.',
    fact: 'Cheetahs have “tear marks” that run from the inside corners of their eyes down to the outside edges of their mouth.'
};

// creates an animal trading card
function createAnimalTradingCardHTML(animal) {
    const cardHTML = '<div class="card">' +
        '<h3 class="name">' + animal.name + '</h3>' +
        '<img src="' + animal.name + '.jpg" alt="' + animal.name +'" class="picture">' +
        '<div class="description">' +
            '<p class="fact">' + animal.fact + '</p>' +
            '<ul class="details">' +
                '<li><span class="bold">Scientific Name</span>: ' + animal.scientificName + '</li>' +
                '<li><span class="bold">Average Lifespan</span>: ' + animal.lifespan + '</li>' +
                '<li><span class="bold">Average Speed</span>: ' + animal.speed + '</li>' +
                '<li><span class="bold">Diet</span>: ' + animal.diet + '</li>' +
            '</ul>' +
            '<p class="brief">' + animal.summary + '</p>' +
        '</div>' +
    '</div>';

    return cardHTML;
}

console.log(createAnimalTradingCardHTML(cheetah));
```

### Solution 4:
```javascript
const teamName = "tooling"
const people = [{name: "Jennie", role: "senior"},
                {name: "Ronald", role: "junior"},
                {name: "Martin", role: "senior"},
                {name: "Anneli", role: "junior"}]

let message = 
`There are ${people.length} people on the tooling team.
Their names are ${people.map(person => person.name)}.
${people.filter(person => person.role == "senior").length} of them have a senior role.`

console.log(message)
```

### Solution 5:
```javascript
const cheetah = {
    name: 'Cheetah',
    scientificName: 'Acinonyx jubatus',
    lifespan: '10-12 years',
    speed: '68-75 mph',
    diet: 'carnivore',
    summary: 'Fastest mammal on land, the cheetah can reach speeds of 60 or perhaps even 70 miles (97 or 113 kilometers) an hour over short distances. It usually chases its prey at only about half that speed, however. After a chase, a cheetah needs half an hour to catch its breath before it can eat.',
    fact: 'Cheetahs have “tear marks” that run from the inside corners of their eyes down to the outside edges of their mouth.'
};

// creates an animal trading card
function createAnimalTradingCardHTML(animal) {
    const cardHTML = `<div class="card">
        <h3 class="name">'${animal.name}'</h3>
        <img src="${animal.name}.jpg" alt="${animal.name}" class="picture">
        <div class="description">
            <p class="fact">${animal.fact}</p>
            <ul class="details">
                <li><span class="bold">Scientific Name</span>:${animal.scientificName}</li>
                <li><span class="bold">Average Lifespan</span>:${animal.lifespan}</li>
                <li><span class="bold">Average Speed</span>:${animal.speed}</li>
                <li><span class="bold">Diet</span>:${animal.diet}</li>
            </ul>
            <p class="brief">${animal.summary}</p>
        </div>
    </div>`;

    return cardHTML;
}

console.log(createAnimalTradingCardHTML(cheetah));
```

# Destructuring
Intuitive and flexible destructuring of Arrays into individual variables and Objects during assignment and function calls.
```javascript
var list = [ 1, 2, 3 ]
var [ a, , b ] = list
[ b, a ] = [ a, b ]
```

```javascript
var obj = { a: 1 }
var list = [ 1 ]
var { a, b = 2 } = obj
var [ x, y = 2 ] = list
``` 

### Exercise 6 - [**Fix the code**](http://marijnhaverbeke.nl/talks/es6_falsyvalues2015/exercises/#Avoiding_disaster) -  [Solution Here](#solution-6)
```javascript
/*
* It would be nice to be able to call our `lastIndexOf` function without providing the third argument, and have it default to starting at the end of the array.
*/
function lastIndexOf(arr, elt, start) {
  for (let i = start - 1; i >= 0; i--)
    if (arr[i] === elt) return i
  return -1
}

console.log(lastIndexOf([1, 2, 1, 2], 2))
```

### Exercise 7 - **Retrieve Colors (Udacity)** - [Solution Here](#solution-7)
```javascript
/*
 * Use destructuring to initialize the variables `one`, `two`, and `three`
 * with the colors from the `things` array.
 */
const things = ['red', 'basketball', 'paperclip', 'green', 'computer', 'earth', 'udacity', 'blue', 'dogs'];
const one = things;
const two = '';
const three = '';

const colors = `List of Colors
1. ${one}
2. ${two}
3. ${three}`;

console.log(colors);
```

### Solution 6:
```javascript
function lastIndexOf(arr, elt, start=arr.length) {
  console.log(start)
  for (let i = start - 1; i >= 0; i--)
    if (arr[i] === elt) return i
  return -1
}
console.log(lastIndexOf([1, 2, 1, 2], 2))
```

### Solution 7:
```javascript
const things = ['red', 'basketball', 'paperclip', 'green', 'computer', 'earth', 'udacity', 'blue', 'dogs'];
const [one,,, two,,,, three] = things;

const colors = `List of Colors
1. ${one}
2. ${two}
3. ${three}`;

console.log(colors);
```
# Iteration (For...of) Loops
The **for...of loop** is used to loop over any type of data that is iterable.

You write a **for...of** loop almost exactly like you would write a **for...in** loop, except you swap out **in** with **of** and you can drop the index.
```javascript
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
for (const digit of digits) {
  if (digit % 2 === 0) {
    continue;
  }
  console.log(digit);
}
```

**Properties of iterable objects**
* Iterable object: has a [Symbol.iterator] method returning an iterator object
* Iterator object: have a next() method returning { done: <Boolean>, value: <NextValue> } of the iteration
* when done is truthy, the iteration ends
* when done is falsy, value is the upcoming element of the iteration

### Exercise 8 - **Loop through each day in the array (Udacity)** - [Solution Here](#solution-8):
```javascript
/*
* Write a for...of loop that:
*
* loops through each day in the days array
* capitalizes the first letter of the day
* and prints the day out to the console
*/
const days = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday'];

// your code goes here
```

### Solution 8:
```javascript
const days = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday'];
for( day of days ){
    console.log(day.slice(0,1).toUpperCase() + (day.slice(1)));
}
```

# Spread Operator
Spreading of elements of an iterable collection (like an array or even a string) into both literal elements and individual function parameters.
```javascript
var params = [ "hello", true, 7 ]
var other = [ 1, 2, ...params ] // [ 1, 2, "hello", true, 7 ]

function f (x, y, ...a) {
    return (x + y) * a.length
}
f(1, 2, ...params) === 9

var str = "foo"
var chars = [ ...str ] // [ "f", "o", "o" ]
```

```javascript
function sum(...nums) {
  let total = 0;  
  for(const num of nums) {
    total += num;
  }
  return total;
}
```

### Exercise 9 - **Combine arrays (Udacity)** - [Solution Here](#solution-9):
```javascript
/*
 * Instructions: Use the spread operator to combine the `fruits` and `vegetables` arrays into the `produce` array.
 */
const fruits = ["apples", "bananas", "pears"];
const vegetables = ["corn", "potatoes", "carrots"];

const produce = [];
console.log(produce);
```

### Exercise 10 -[**Simplify functions**](http://marijnhaverbeke.nl/talks/es6_falsyvalues2015/exercises/#Spread_out) - [Solution Here](#solution-10):
```javascript
/*
The first one, replace, replaces part of an array with elements from another array.

The second one, copyReplace, does the same, but creates a new array rather than modifying its argument.

The third one is used to record a birdwatcher's sightings. It takes first a timestamp (say, a Date), and then any number of strings naming birds. It then stores these in the birdsSeen array.
*/
function replace(array, from, to, elements) {
  array.splice.apply(array, [from, to - from].concat(elements))
}

let testArray = [1, 2, 100, 100, 6]
replace(testArray, 2, 4, [3, 4, 5])
console.log(testArray)

function copyReplace(array, from, to, elements) {
  return array.slice(0, from).concat(elements).concat(array.slice(to))
}

console.log(copyReplace([1, 2, 100, 200, 6], 2, 4, [3, 4, 5]))

let birdsSeen = []
function recordBirds(time) {
  birdsSeen.push({time, birds: Array.prototype.slice.call(arguments, 1)})
}

recordBirds(new Date, "sparrow", "robin", "pterodactyl")
console.log(birdsSeen)
```

### Solution 9:
```javascript
const fruits = ["apples", "bananas", "pears"];
const vegetables = ["corn", "potatoes", "carrots"];

const produce = [...fruits, ...vegetables];
console.log(produce);
```

### Solution 10:
```javascript
function replace(array, from, to, elements) {
  array.splice(from, to-from, ...elements)
}

let testArray = [1, 2, 100, 100, 6]
replace(testArray, 2, 4, [3, 4, 5])
console.log(testArray)

function copyReplace(array, from, to, elements) {
  return array.slice(0, from).concat(...elements).concat(array.slice(to))
}

console.log(copyReplace([1, 2, 100, 200, 6], 2, 4, [3, 4, 5]))

let birdsSeen = []
function recordBirds(time, ...birds) {
  birdsSeen.push({time, birds: birds})
}

recordBirds(new Date, "sparrow", "robin", "pterodactyl")
console.log(birdsSeen)
```

# Arrow Functions
There are only a few steps for converting the existing "normal" function into an arrow function.

* Remove the *function* keyword
* Remove the parentheses
* Remove the opening and closing curly braces
* Remove the *return* keyword
* Remove the semicolon
* Add an arrow ( *=>* ) between the parameter list and the function body
```javascript
// ES5
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(function(name) { 
  return name.toUpperCase();
});

// ES6
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(
  name => name.toUpperCase()
);
```

### Exercise 11 - **Convert the function to Arrow function (Udacity)** - [Solution Here](#solution-11)
```javascript
const squares = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10].map(function(square) {
	return square * square;
});
console.log(...squares);
```
### Exercise 12 - [**Fix the code**](http://marijnhaverbeke.nl/talks/es6_falsyvalues2015/exercises/#Accounting) - [Solution Here](#solution-12)
```javascript
// Write an expression using higher-order array methods (say, filter and reduce) to compute the total value of the machines in the inventory array.
const inventory = [
  {type:   "machine", value: 5000},
  {type:   "machine", value:  650},
  {type:      "duck", value:   10},
  {type: "furniture", value: 1200},
  {type:   "machine", value:   77}
]

let totalMachineValue = // YOUR_CODE_HERE
console.log(totalMachineValue)
```

### Solution 11
```javascript
const squares = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10].map(square => square * square);
console.log(...squares);
```

### Solution 12
```javascript
const inventory = [
  {type:   "machine", value: 5000},
  {type:   "machine", value:  650},
  {type:      "duck", value:   10},
  {type: "furniture", value: 1200},
  {type:   "machine", value:   77}
]

let totalMachineValue = inventory.map(item => item.value).reduce((total, value) => total + value)
console.log(totalMachineValue)
```

# Default Parameters
To create a default parameter, you add an equal sign ( = ) and then whatever you want the parameter to default to if an argument is not provided.

```javascript
function f (x, y = 7, z = 42) {
    return x + y + z
}
f(1) === 50
```
The following codes show examples of function calls without any arguments.

```javascript
function createGrid([width = 5, height = 5] = []) {
  return `Generates a ${width} x ${height} grid`;
}
```

```javascript
function createSundae({scoops = 1, toppings = ['Hot Fudge']} = {}) {
  const scoopText = scoops === 1 ? 'scoop' : 'scoops';
  return `Your sundae has ${scoops} ${scoopText} with ${toppings.join(' and ')} toppings.`;
}
```

### Exercise 13 - **Create Function (Udacity)** - [Solution Here](#solution-13)
```javascript
/*Create a buildHouse() function that accepts an object as a default parameter. The object should set the following properties to these default values:

floors = 1
color = 'red'
walls = 'brick'
The function should return the following if no arguments or any empty object is passed to the function.

Your house has 1 floor(s) with red brick walls.

// your code goes here

//tests
console.log(buildHouse()); // Your house has 1 floor(s) with red brick walls.
console.log(buildHouse({})); // Your house has 1 floor(s) with red brick walls.
console.log(buildHouse({floors: 3, color: 'yellow'})); // Your house has 3 floor(s) with yellow brick walls.
*/
```

### Solution 13
```javascript
function buildHouse({floors = 1, color = 'red', walls='brick'} = {}){
    return(`Your house has ${floors} floor(s) with ${color} ${walls} walls.`);
};

console.log(buildHouse()); // Your house has 1 floor(s) with red brick walls.
console.log(buildHouse({})); // Your house has 1 floor(s) with red brick walls.
console.log(buildHouse({floors: 3, color: 'yellow'})); // Your house has 3 floor(s) with yellow brick walls.
```

# Class and Subclass
Benefits of classes:
* **Less setup:** There's a lot less code that you need to write to create a function
* **Clearly defined constructor function** Inside the class definition, you can clearly specify the constructor function.
* **Everything's contained** All code that's needed for the class is contained in the class declaration. Instead of having the constructor function in one place, then adding methods to the prototype one-by-one, you can do everything all at once!

```javascript
class Dessert {
  constructor(calories = 250) {
    this.calories = calories;
  }
}

class IceCream extends Dessert {
  constructor(flavor, calories, toppings = []) {
    super(calories);
    this.flavor = flavor;
    this.toppings = toppings;
  }
  addTopping(topping) {
    this.toppings.push(topping);
  }
}
```
### Exercise 14 - **Translate from ES5 to ES6 (Udacity)** - [Solution Here](#solution-14)
```javascript
function Plane(numEngines) {
  this.numEngines = numEngines;
  this.enginesActive = false;
}

// methods "inherited" by all instances
Plane.prototype.startEngines = function () {
  console.log('starting engines...');
  this.enginesActive = true;
};
```

### Exercise 15 - **Create Subclass (Udacity)** - [Solution Here](#solution-15)
```javascript
// Create a Bicycle subclass that extends the Vehicle class. The Bicycle subclass should override Vehicle's constructor function by changing the default values for // wheels from 4 to 2 and horn from 'beep beep' to 'honk honk'.

class Vehicle {
	constructor(color = 'blue', wheels = 4, horn = 'beep beep') {
		this.color = color;
		this.wheels = wheels;
		this.horn = horn;
	}

	honkHorn() {
		console.log(this.horn);
	}
}

// your code goes here

/* tests
const myVehicle = new Vehicle();
myVehicle.honkHorn(); // beep beep
const myBike = new Bicycle();
myBike.honkHorn(); // honk honk
*/
```

### Solution 14:
```javascript
class Plane {
  constructor(numEngines) {
    this.numEngines = numEngines;
    this.enginesActive = false;
  }

  startEngines() {
    console.log('starting engines…');
    this.enginesActive = true;
  }
}
```

### Solution 15:
```javascript
class Vehicle {
	constructor(color = 'blue', wheels = 4, horn = 'beep beep') {
		this.color = color;
		this.wheels = wheels;
		this.horn = horn;
	}

	honkHorn() {
		console.log(this.horn);
	}
}

class Bicycle extends Vehicle{
    constructor(color, wheels = 2, horn = 'honk honk'){
        super(undefined, wheels, horn);
    }
}


const myVehicle = new Vehicle();
myVehicle.honkHorn(); // beep beep
const myBike = new Bicycle();
myBike.honkHorn(); // honk honk
```

# Symbols
* **Symbol()** creates a unique symbol
* Objects can have string or symbol keys
* Node.js does not print Symbol keys
* **JSON.stringify** excludes Symbol keys
* **Object.assign** copies Symbol keys over to **target**

```javascript
// ES5
const bowl = {
  'apple': { color: 'red', weight: 136.078 },
  'banana': { color: 'yellow', weight: 183.151 },
  'orange': { color: 'orange', weight: 170.097 },
  'banana': { color: 'yellow', weight: 176.845 }
};
console.log(bowl); // Object {apple: Object, banana: Object, orange: Object}

```

```javascript
// ES6
const bowl = {
  [Symbol('apple')]: { color: 'red', weight: 136.078 },
  [Symbol('banana')]: { color: 'yellow', weight: 183.15 },
  [Symbol('orange')]: { color: 'orange', weight: 170.097 },
  [Symbol('banana')]: { color: 'yellow', weight: 176.845 }
};
console.log(bowl); // Object {Symbol(apple): Object, Symbol(banana): Object, Symbol(orange): Object, Symbol(banana): Object}
```