# JavaScript Cheatsheet

## Index

- [Declaring Variables](#declaring-variables)
  - [Reassigning Variable Values](#reassigning-variable-values)
- [Primitive Types](#primitive-types)
  - [Checking Types](#checking-types)
- [Scope](#scope)
- [Arrays](#arrays)
  - [Accessing Array Values](#accessing-values-within-an-array)
  - [Randomization](#finding-a-random-value-within-an-array)
  - [Looping Through an Array](#looping-through-an-array)
- [Objects](#objects)
  - [Accessing Properties](#accessing-object-properties)
- [Conditional Statements](#conditional-statements)
- [Functions](#functions)
  - [Invoking Functions](#invoking-functions)
  - [Parameters / Arguments](#function-parameters-arguments)
  - [Returning Values](#returning-values-from-functions)
- [Iterating (for loops)](#iterating-for-loops)
- [DOM Manipulation](#dom-manipulation)
  - [Accessing Dom Elements](#accessing-dom-elements)
  - [Changing Text and Attributes](#changing-text-and-element-attributes)
  - [Creating New Elements](#creating-new-elements)

### Declaring Variables

Variables store frequently accessed values that we can easily reference under a descriptive name.
We declare variables in JavaScript using the `var` keyword, and a single `=` to denote that we are assigning a value to a variable.

```js
// Declaring Variables
var firstName = 'Tom';
var isStudent = true;
var age = 31;
```

#### Reassigning Variable Values

We can reassign the value of a variable using the `=` operator.

```js
// Reassigning Variables
var firstName = 'Tom';
var isStudent = true;
var age = 31;

age = 32;
isStudent = false;
```

### Primitive Types

Primitive types in JavaScript include:

- Strings - Typically letters, words or sentences, wrapped in single quotes (`'`) or double quotes (`"`)
- Numbers - Includes integers and numbers with decimals
- Booleans - Either `true` or `false`
- Undefined - No set value

```js
// STRING (can be wrapped in single quotes or double quotes)
var firstName = 'Tom';

// NUMBER (includes integers and floats)
var age = 99;
var pi = 3.14;

// BOOLEAN (Either `true` or `false`)
var isStudent = true;
var isInstructor = false;

// UNDEFINED (No previous set value)
var foo;
var baz = undefined;
```

#### Checking Types

To check a type in JavaScript, we can use `typeof`

```js
var firstName = 'Tom';
console.log(typeof firstName); // string

var age = 99;
console.log(typeof age); // number

var isStudent = true;
console.log(typeof isStudent); // boolean

var foo;
console.log(typeof foo); // undefined
```

### Scope

Scope refers to the availability of specific variables in different parts of our code.
JavaScript uses Lexical scope, which means variables can only be accessed within the scope block
they were defined in, or within any child scope blocks.

Scope blocks are typically defined with `{}` and can be seen throughout our code, in things like
functions, for loops, conditional (if/else) statements etc.

If a variable is declared outside of any scope block, it is considered a global variable and can
be accessed anywhere in our code.

```js
// `isStudent` is a global variable and can be used anywhere
var isStudent = true;

function myFunction() {
  // `a` is accessible anywhere within this function
  var a = 3;

  // `isStudent` is accessible here since it is a global variable
  if (isStudent === true) {
    // `a` is accessible here since it was defined within this function
    console.log(a);
  }
}

myFunction();

// This will throw an error since `a` is not accessible outside of myFuncion
console.log(a);
```

### Arrays

Arrays are essentially just lists of related values. We use `[]` to denote a new array, and seperate the values inside our array by commas.

```js
var students = ['Joe', 'Ken', 'Brooke'];
```

#### Accessing Values Within an Array

We can access values stored in an array using their index. Indexes represent positions within an array, starting at `0`.
To access a value stored in an array, reference the array with the index wrapped in `[]`

```js
var students = ['Joe', 'Ken', 'Brooke'];

console.log(students[0]); // Joe
console.log(students[1]); // Ken
console.log(students[2]); // Brooke
```

#### Finding A Random Value within an Array

To find a random value within an array, we can use built in `Math.random()` utility, along with the arrays length.

```js
var students = ['Joe', 'Ken', 'Brooke'];

// Since our array length is 3,
// This number will be either 0,1 or 2
var randomIndex = Math.floor(Math.random() * students.length);

// Since our randomIndex will be either 0, 1, or 2,
// students[randomIndex] will be either
// students[0] (Joe), students[1] (Ken), or students[2] (Brooke)
var random = students[randomIndex];
```

#### Looping Through an Array

We can loop through an array using a for loop, looping from `0` to the array's length. Our iterator variable, `i`, can be used inside the for loop as our current array index.

```js
var students = ['Joe', 'Ken', 'Brooke'];

for (var i = 0; i < students.length; i++) {
  // The first time our for loop runs,
  // `i` will equal 0, so currentStudent
  // will be students[0] (Joe). Then, on
  // the next iteration it will be
  // students[1] (Ken) and on the final
  // interation, it will be students[2] (Brooke)
  var currentStudent = students[i];
  console.log(currentStudent);
}
```

##### See Also

- [Iterating (for loops)](#iterating-for-loops)

### Objects

We can use objects to store related values together, using `{}` to denote a new object.
Objects are collections of properties. Each property has a name and a value.

Objects can contain any primitive type, arrays, nested objects, and even functions.
Functions stored within objects are called methods.

```js
var car = {
  year: 2022,
  make: 'Tesla',
  model: 'Model 3',
  features: {
    hasNavigation: true,
    hasHeatedSeats: true,
  },
  pastOwners: ['Tom', 'Bill'],
  honk: function () {
    console.log('Beep beep!');
  },
};
```

### Accessing Object Properties

We can access object properties using dot notation.
Reference the name of the object, followed by a `.` and the property name.

```js
var car = {
  year: 2022,
  make: 'Tesla',
  model: 'Model 3',
  features: {
    hasNavigation: true,
    hasHeatedSeats: true,
  },
  pastOwners: ['Tom', 'Bill'],
  honk: function () {
    console.log('Beep beep!');
  },
};

console.log(car.make); // Tesla
console.log(car.features.hasNavigation); // true
console.log(car.pastOwners[0]); // Tom
car.honk(); // Beep beep!
```

### Conditional Statements

Using an `if` statement, we can run a block of code if a condition is met.

```js
var age = prompt('How old are you?');

if (age >= 21) {
  // This code only runs if the user's age is >= 21
  console.log('Welcome to the bar!');
}
```

If we want to run a different block of code if that condition is false, we can add an `else` statement:

```js
var age = prompt('How old are you?');

if (age >= 21) {
  // This code only runs if the user's age is >= 21
  console.log('Welcome to the bar!');
} else {
  // This code only runs if the user's age is < 21
  console.log('Please go away');
}
```

Alternatively, if we want to check if another condition is true, we can add an `else if` statement:

```js
var hour = 10;

if (hour < 12) {
  // This code only runs if the hour is less than 12
  console.log('Good morning');
} else if (hour < 17) {
  // This code will run if the hour is greater than 12,
  // but less than 17
  console.log('Good afternoon');
} else {
  // This code will run if the hour is greater than 17
  console.log('Good evening');
}
```

### Functions

We use functions to make sections of our code reusable.
Functions can be declared in one of two ways:

```js
// Method One:
function myFunction() {
  console.log('This code lives inside my function');
}

// Method Two:
var anotherFunction = function () {
  console.log('This code also lives inside my function');
};
```

#### Invoking Functions

The code within our function wont run automatically. We need to invoke the function first.
To do this, we do reference the name of our function, followed by `()`

```js
function myFunction() {
  console.log('This code lives inside my function');
}

// Invoking myFunction
myFunction();
```

#### Function Parameters / Arguments

Functions can optionally take in parameters. Parameters allow us to provide custom values that can be referenced within our function

```js
// This function takes in two parameters: firstName and age
function happyBirthday(firstName, age) {
  console.log('Happy birthday ' + firstName);
  console.log('You are ' + age + ' years old today');
}

// When calling the happyBirthday function
// we are providing two arguments: 'Tom' and 30.
// Since happyBirthday takes in two parameters (firstName and age)
// `Tom` will be used as the value of firstName
// and 30 will be used as the value of age within this function execution
happyBirthday('Tom', 30);
```

#### Returning Values from Functions

Functions serve two main purposes: To automate tasks, and calculate values.

To return a calculated value from our function, we use the `return` keyword

```js
function add(a, b, c, d) {
  return a + b + c + d;
}

var sum = add(4, 1, 10, 7);
console.log(sum); // 22
```

### Iterating (for loops)

We can use loops to repeat steps a set number of times.
For loops have three sections:

- The first section initializes a value for our counter variable
- The second section defines our exit condition (when our loop stops)
- The third section defines how we should change our counter variable after every iteration

```js
// This loop will run 5 times
// and log 0,1,2,3 and 4 in the console
for (var i = 0; i < 5; i++) {
  console.log(i);
}
```

##### See Also

- [Looping Through an Array](#looping-through-an-array)

### DOM Manipulation

DOM Manipulation refers to dynamically changing our HTML using JavaScript.

Using some built in JavaScript methods, we can access our DOM (document object model) and modify it's content and attributes

#### Accessing DOM Elements

To access an HTML Element, we can use a few methods:

- `document.getElementById(htmlElementId)` - Accesses a single element based off it's HTML id. If no element found, it returns `null`
- `document.getElementsByClassName(htmlElementClass)` - Returns an array of elements with the specified class
- `document.querySelector(query)` - Takes in a css style query and **returns the first matching element**. If no element is found, it returns `null`
- `document.querySelectorAll(query)`- Takes in a css style query and **returns an array containing all matching element**

###### index.html

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <h1 id="appTitle">Welcome to my page!</h1>
    <h2>Ways to say hello</h2>
    <section id="cardSection">
      <div class="card">Hey</div>
      <div class="card">Hi</div>
      <div class="card">Hello</div>
    </section>
    <img id="myImage" src="https://placehold.it/200/200" alt="placehodler" />

    <script src="./script.js"></script>
  </body>
</html>
```

###### script.js

```js
// Stores element with an ID of `myImage` in imageElement variable
// Alternatively, could have used querySelector like this:
//     document.querySelector('#myImage');
var imageElement = document.getElementById('myImage');

// Stores an array with all elements with a class of `card` in cards variable
// Alternatively, could have used getElementsByClassName like this:
//     document.getElementsByClassName('card');
var cards = document.querySelectorAll('.card');
```

#### Changing Text and Element Attributes

Once we have queried the DOM for our target element, we may find it useful in certain cases to change the text content or add/modify our element's HTML attributes.

We can change the text within an element by accessing the `textContent` property and we can set or modify attributes of our element using the `setAttribute()` method, providing the attribute name and the desired value.

###### index.html

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <h1 id="appTitle">Welcome to my page!</h1>
    <h2>Ways to say hello</h2>
    <section id="cardSection">
      <div class="card">Hey</div>
      <div class="card">Hi</div>
      <div class="card">Hello</div>
    </section>
    <img id="myImage" src="https://placehold.it/200/200" alt="placehodler" />

    <script src="./script.js"></script>
  </body>
</html>
```

###### script.js

```js
var firstName = prompt('What is your first name?');
var appTitleElement = document.getElementById('appTitle');

// Changing the text of the app title to include the user's first name
appTitleElement.textContent = 'Welcome to my site ' + firstName;

var imageElement = document.getElementById('myImage');

// Changing the src attribute on an img element
imageElement.setAttribute('src', './images/cancun_beach.png');

// Changing the alt attribute on an img element
imageElement.setAttribute('alt', 'A beach in Cancun');
```

#### Creating New Elements

To create a new HTML element to add to our page, we can use the built in `document.createElement()` method, passing in the name of the element tag we want to create (`div`, `section`, `p`, `h1`, etc).

Once we have created our element, we need to add it to our HTML. We do this by querying the HTML for the desired parent element, then call the `appendChild()` method of our parent and pass in the newly created element.

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <h1 id="appTitle">Welcome to my page!</h1>
    <h2>Ways to say hello</h2>
    <section id="cardSection">
      <div class="card">Hey</div>
      <div class="card">Hi</div>
      <div class="card">Hello</div>
    </section>
    <img id="myImage" src="https://placehold.it/200/200" alt="placehodler" />

    <script src="./script.js"></script>
  </body>
</html>
```

###### script.js

```js
// This creates a new div element under the variable myNewCardElement
var myNewCardElement = document.createElement('div');

// Just like when modifying an existing element
// We can set the text within an element using the `textContent` property
myNewCardElement.textContent = 'Heya';

// This sets the class of our new element to 'card'
myNewCardElement.setAttribute('class', 'card');

// Since we want our new element to live within the cardSection
// we first need to query the DOM for this element
var parentCardSection = document.querySelector('#cardSection');

// Finally, we add our new element as a child of the #cardSection element
parentCardSection.appendChild(myNewCardElement);
```
