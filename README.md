# JavaScript Cheatsheet

## Index

- [Declaring Variables](#declaring-variables)
  - [Reassigning Variable Values](#reassigning-variable-values)
- [Arrays](#arrays)
  - [Accessing Values Within an Array](#accessing-values-within-an-array)
  - [Randomization](#finding-a-random-value-within-an-array)
  - [Looping Through an Array](#looping-through-an-array)
- [Objects](#objects)
  - [Accessing Object Properties](#accessing-object-properties)
- [Functions](#functions)
  - [Invoking Functions](#invoking-functions)
  - [Parameters / Arguments](#function-parameters-arguments)
  - [Returning Values](#returning-values-from-functions)
- [Iterating (for loops)](#iterating-for-loops)

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
  // will be students[0] (Joe)
  // Then it will be students[1] (Ken) on the
  // next iteration and so on
  var currentStudent = students[i];
  console.log(currentStudent);
}
```

###### See Also

- [Iterating (for loops)](#iterating-for-loops)

### Objects

We can use objects to store related variables together, using `{}` to denote an object.
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

// Arguments provided: Tom & 30
happyBirthday('Tom', 30);
```

#### Returning Values from Functions

Functions serve two main purposes: To automate tasks, and calculate values.
To calculate values with our functions, we use the `return` keyword.

```js
function add(a, b, c, d) {
  return a + b + c + d;
}

var sum = add(4, 1, 10, 7);
console.log(sum); // 21
```

### Iterating (for loops)

We can use loops to repeat steps a set number of times.
For loops have three sections: - 1. Initializes value for our counter variable - 2. Defines our exit condition (when our loop stops) - 3. Defines how we should change our counter variable after every iteration

```js
// This loop will run 5 times
// and log 0,1,2,3 and 4 in the console
for (var i = 0; i < 5; i++) {
  console.log(i);
}
```

###### See Also

- [Looping Through an Array](#looping-through-an-array)
