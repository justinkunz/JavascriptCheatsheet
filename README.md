# JavaScript Cheatsheet

Use this guide as a reference when you get stuck or need a refresher on how to do something. While coding examples are included, you will learn better if you retype them and avoid copying/pasting.

###### Related Guides

- [Git Guide](https://github.com/justinkunz/GitCheatsheet)

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
- [Logical Comparison Operators](#logical-comparison-operators)
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
- [Event Listeners](#event-listeners)
  - [Click Events](#click-events)
  - [Keyboard Events](#keyboard-events)
- [Browser Interactive Popups](#browser-interactive-popups)
  - [Alerts](#alerts)
  - [Prompts](#prompts)
  - [Confirms](#confirms)
- [Timeouts and Intervals](#timeouts-and-intervals)
  - [Timeouts](#timeouts)
  - [Intervals](#intervals)
  - [Clearing Intervals](#clearing-intervals)
- [Browser Storage](#browser-storage)
  - [Local Storage](#local-storage)
  - [Session Storage](#session-storage)

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

### Logical Comparison Operators

We use logical comparison operators to compare the equality of two values.

- `===` - Equal in both type & value
- `==` - Equal in value
- `!==` - Not equal in both type and value
- `!=` - Not equal in value
- `>` - Greater than
- `>=` - Greater than or equal to
- `<` - Less than
- `<=` - Less than or equal to

```js
var a = 5;
var b = '5';
var c = 10;

console.log(a === b); // False
console.log(a == b); // True
console.log(c > a); // True
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

### Event Listeners

We can use event listeners to get our code to react to user driven events, like button clicks or keyboard events.

#### Click Events

To add a click event listener to an HTML element, target the element and call the `addEventListener` method, passing in `click` as the first argument and the callback function we want to execute when our click occurs as the second argument.

###### index.html

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <form>
      <input placeholder="Email" type="email" id="emailAddress" />
      <input placeholder="Password" type="password" />
      <button id="btn">Sign Up</button>
    </form>
    <script src="./script.js"></script>
  </body>
</html>
```

###### script.js

```js
var btnElement = document.getElementById('btn');

// addEventListener takes in two arguements:
// The type of event to listen for (clicks in our case)
// And the function to execute when the event occurs
btnElement.addEventListener('click', function (event) {
  // Submit Buttons or buttons within forms can have some unexpected default behavior
  // To override this default behavior, we can use the `preventDefault` method on the
  // event object JavaScript provides us
  event.preventDefault();
  console.log("I've been clicked!");
});
```

Alternatively, we can add an `onclick` attribute to the element within our HTML

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <form>
      <input placeholder="Email" type="email" id="emailAddress" />
      <input placeholder="Password" type="password" />
      <button id="btn" onclick="myFunction()">Sign Up</button>
    </form>
    <script src="./script.js"></script>
  </body>
</html>
```

#### Keyboard Events

To listen for keyboard events within an HTML element, target the element and call the `addEventListener`, passing in either `keyup`, `keypress`, or `keydown` (depending on exactly what event we're wanting to listen for) as the first argument, and the callback function we want to execute when the event occurs as the second argument.

###### index.html

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <form>
      <input placeholder="Email" type="email" id="emailAddress" />
      <input placeholder="Password" type="password" />
      <button id="btn">Sign Up</button>
    </form>
    <script src="./script.js"></script>
  </body>
</html>
```

###### script.js

```js
var emailInput = document.querySelector('#emailAddress');

// addEventListener takes in two arguements:
// The type of event to listen for (keydown events in our case)
// And the function to execute when the event occurs
emailInput.addEventListener('keydown', function (event) {
  console.log('The following key has been typed:', event.key);
});
```

### Browser Interactive Popups

We can use browser popups to deliver messages and ask questions with users visiting our site.

#### Alerts

The `alert()` function is used to deliver messages to users. Users must click `ok` to dismiss the message.

```js
alert('Thank you for visiting my site');
```

#### Prompts

The `prompt()` function is used to get input from a user. Along with the `prompt` message, the user will be given an input field to type their response. Whatever input is entered in here will be returned from the `prompt` function.

```js
// Whatever the user types in the prompt field will be stored
// in the `firstName` variable
var firstName = prompt('What is your first name?');
```

#### Confirms

The `confirm()` function is used to ask a yes or no question to users. When presented with a `confirm` message, a user can select from two options: `ok` or `cancel`. If they select `ok`, the `confirm` function returns true. If they select `cancel`, the `confirm` function returns false.

```js
// The user will be asked "Do you like pizza?"
// If they click "ok", `likesPizza` is true
// If they click "cancel", `likesPizza` is false
var likesPizza = confirm('Do you like pizza?');

if (likesPizza === true) {
  alert('Yay! I also like Pizza!');
} else {
  alert('Boo!');
}
```

### Timeouts and Intervals

There may be times where we want to delay execution of some code. We can accomplish this using timeouts and intervals in JavaScript.

#### Timeouts

Timeouts in JavaScript delay the execution of our code by a specified amount of time. To add a timeout, we can use the built in `setTimeout()` function.

`setTimeout()` takes in two arguments: the function to execute once time has elapsed and the amount of time to wait (in milliseconds)

```js
setTimeout(function () {
  console.log('This will log to the console once after 1 second has passed');
}, 1000);
```

#### Intervals

Intervals work similiarly to timeouts, but instead of executing our supplied code once, our code runs on a regular interval we specify. To add an interval, we can use the built in `setInterval()` function.

Like `setTimeout()`, `setInterval()` takes in two arguments: a function to execute, and the frequency in which to execute it (in milliseconds)

```js
setInterval(function () {
  console.log('This will log to console every second');
}, 1000);
```

#### Clearing Intervals

Many times when working with intervals, we'll want a way to eventually stop them from executing further. We can accomplish this using the built in `clearInterval()` function.

To do this, first declare a new variable set equal to your interval. Then, to later clear the interval, call `clearInterval()` passing in the interval reference.

```js
var timeRemaining = 5;

// This will countdown from 5 to 0
// Once `timeRemaining` is equal to 0, the interval is cleared
// and the callback will not be executed again
var countdownInterval = setInterval(function () {
  console.log('Time remaining:', timeRemaining);
  timeRemaining--;

  if (timeRemaining === 0) {
    clearInterval(countdownInterval);
  }
}, 1000);
```

### Browser Storage

Many times, we will want our applications to remember some information about a user's last visit to our site. To accomplish this, we can utilize `localStorage` and `sessionStorage`.

Keep in mind, browser storage is domain specific, so your site does not have access to items stored by other sites.

#### Local Storage

Local storage allows us to add items to and retrieve items from storage managed by the browser.

To add an item to local storage, we use the `setItem()` method on the `localStorage` object. The `setItem()` method takes in two arguments: A name for the item we are setting, and a value.

To retrieve an item from local storage, we use the `getItem()` method on the `localStorage` object. The `getItem()` method takes in the name of the item to retrieve, and returns the stored value.

###### index.html

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <form>
      <input placeholder="First Name" id="firstName" />
      <input placeholder="Last Name" id="lastName" />
      <button id="btn">Sign Up</button>
    </form>
    <script src="./script.js"></script>
  </body>
</html>
```

###### script.js

```js
var firstNameInput = document.getElementById('firstName');
var lastNameInput = document.getElementById('lastName');

function recordValues() {
  // Add a record with the name "firstName" to our local storage
  // Set the value to whatever is in the firstNameInput text field
  localStorage.setItem('firstName', firstNameInput.value);
  // Add a record with the name "lastName" to our local storage
  // Set the value to whatever is in the lastNameInput text field
  localStorage.setItem('lastName', lastNameInput.value);
}

// Run the recordValues function whenever the button is clicked
document.getElementById('btn').addEventListener('click', recordValues);

function retrieveStoredValues() {
  // Get the value stored in local storage under the key `firstName`
  // and store it in the `storedFirstNameValue` variable
  var storedFirstNameValue = localStorage.getItem('firstName');
  // Update the firstNameInput's value to match what was stored in local storage
  firstNameInput.value = storedFirstNameValue;

  // Get the value stored in local storage under the key `lastName`
  // and store it in the `storedLastNameValue` variable
  var storedLastNameValue = localStorage.getItem('lastName');
  // Update the lastNameInput's value to match what was stored in local storage
  lastNameInput.value = storedLastNameValue;
}

// When the page first loads,
// Pull the stored values out of localStorage and set them to the corresponding text fields
retrieveStoredValues();
```

Local Storage is fantastic at storing strings...It's not good, however, at storing objects or arrays.

So if we want to store an object or an array inside local storage, we will first need to convert it to a string. We can do this using `JSON.stringify()`, and passing in the object or array we need to convert.

Since our value will be stored as string, we will need to convert it back to an object before we can use it again in our code. We can do this using `JSON.parse()` and passing in the stringified object/array.

###### index.html

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <form>
      <input placeholder="First Name" id="firstName" />
      <input placeholder="Last Name" id="lastName" />
      <button id="btn">Sign Up</button>
    </form>
    <script src="./script.js"></script>
  </body>
</html>
```

###### script.js

```js
var firstNameInput = document.getElementById('firstName');
var lastNameInput = document.getElementById('lastName');

function recordValues() {
  var usersName = {
    firstName: firstNameInput.value,
    lastName: lastNameInput.value,
  };

  // Before we can store this in local storage, we will need to first
  // stringify the object using JSON.stringify()
  localStorage.setItem('name', JSON.stringify(usersName));
}

// Run the recordValues function whenever the button is clicked
document.getElementById('btn').addEventListener('click', recordValues);

function retrieveStoredValues() {
  // After retrieving the item from local storage,
  // we will need to parse the object string back into a normal object using JSON.parse();
  var storedFullName = JSON.parse(localStorage.getItem('name'));

  // Update the HTML Input values to match what was stored in localStorage
  firstNameInput.value = storedFullName.firstName;
  lastNameInput.value = storedFullName.lastName;
}

// When the page first loads,
// Pull the stored values out of localStorage and set them to the corresponding text fields
retrieveStoredValues();
```

#### Session Storage

Like Local storage, Session storage allows us to add items to and retrieve items from storage managed by the browser.

**While local storage remembers data from each visit, sessionStorage is cleared whenever the page session ends. (when the tab is closed)**

To add an item to local storage, we use the `setItem()` method on the `sessionStorage` object. The `setItem()` method takes in two arguments: A name for the item we are setting, and a value.

To retrieve an item from local storage, we use the `getItem()` method on the `sessionStorage` object. The `getItem()` method takes in the name of the item to retrieve, and returns the stored value.

###### index.html

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <form>
      <input placeholder="First Name" id="firstName" />
      <input placeholder="Last Name" id="lastName" />
      <button id="btn">Sign Up</button>
    </form>
    <script src="./script.js"></script>
  </body>
</html>
```

###### script.js

```js
var firstNameInput = document.getElementById('firstName');
var lastNameInput = document.getElementById('lastName');

function recordValues() {
  // Add a record with the name "firstName" to our session storage
  // Set the value to whatever is in the firstNameInput text field
  sessionStorage.setItem('firstName', firstNameInput.value);
  // Add a record with the name "lastName" to our session storage
  // Set the value to whatever is in the lastNameInput text field
  sessionStorage.setItem('lastName', lastNameInput.value);
}

// Run the recordValues function whenever the button is clicked
document.getElementById('btn').addEventListener('click', recordValues);

function retrieveStoredValues() {
  // Get the value stored in session storage under the key `firstName`
  // and store it in the `storedFirstNameValue` variable
  var storedFirstNameValue = sessionStorage.getItem('firstName');
  // Update the firstNameInput's value to match what was stored in local storage
  firstNameInput.value = storedFirstNameValue;

  // Get the value stored in session storage under the key `lastName`
  // and store it in the `storedLastNameValue` variable
  var storedLastNameValue = sessionStorage.getItem('lastName');
  // Update the lastNameInput's value to match what was stored in session storage
  lastNameInput.value = storedLastNameValue;
}

// When the page first loads,
// Pull the stored values out of localStorage and set them to the corresponding text fields
retrieveStoredValues();
```

Like Local Storage, Session Storage is fantastic at storing strings...It's not good, however, at storing objects or arrays.

So if we want to store an object or an array inside session storage, we will first need to convert it to a string. We can do this using `JSON.stringify()`, and passing in the object or array we need to convert.

Since our value will be stored as string, we will need to convert it back to an object before we can use it again in our code. We can do this using `JSON.parse()` and passing in the stringified object/array.

###### index.html

```html
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <form>
      <input placeholder="First Name" id="firstName" />
      <input placeholder="Last Name" id="lastName" />
      <button id="btn">Sign Up</button>
    </form>
    <script src="./script.js"></script>
  </body>
</html>
```

###### script.js

```js
var firstNameInput = document.getElementById('firstName');
var lastNameInput = document.getElementById('lastName');

function recordValues() {
  var usersName = {
    firstName: firstNameInput.value,
    lastName: lastNameInput.value,
  };

  // Before we can store this in session storage, we will need to first
  // stringify the object using JSON.stringify()
  sessionStorage.setItem('name', JSON.stringify(usersName));
}

// Run the recordValues function whenever the button is clicked
document.getElementById('btn').addEventListener('click', recordValues);

function retrieveStoredValues() {
  // After retrieving the item from session storage,
  // we will need to parse the object string back into a normal object using JSON.parse();
  var storedFullName = JSON.parse(sessionStorage.getItem('name'));

  // Update the HTML Input values to match what was stored in localStorage
  firstNameInput.value = storedFullName.firstName;
  lastNameInput.value = storedFullName.lastName;
}

// When the page first loads,
// Pull the stored values out of localStorage and set them to the corresponding text fields
retrieveStoredValues();
```
