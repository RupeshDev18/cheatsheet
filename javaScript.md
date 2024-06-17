# JavaScript cheatsheet

A JavaScript cheat sheet with the most important concepts, functions, methods, and more. A complete quick reference for beginners.

## Variables

```javascript
// ES5
var x = 5;

// ES6+
let y = 10;
const z = 15;
```

## Data Types

```javascript
// Number
let num = 123;

// String
let str = "Hello, World!";

// Boolean
let isTrue = true;

// Null
let empty = null;

// Undefined
let notDefined;

// Object
let obj = { key: "value" };

// Array
let arr = [1, 2, 3];
```

## Operators

```javascript
// Arithmetic Operators
let sum = 5 + 3; // Addition
let difference = 5 - 3; // Subtraction
let product = 5 * 3; // Multiplication
let quotient = 5 / 3; // Division
let remainder = 5 % 3; // Modulus

// Assignment Operators
let x = 5;
x += 3; // x = x + 3
x -= 3; // x = x - 3
x *= 3; // x = x * 3
x /= 3; // x = x / 3
x %= 3; // x = x % 3

// Comparison Operators
let isEqual = 5 == "5"; // true
let isStrictEqual = 5 === "5"; // false
let isNotEqual = 5 != "5"; // false
let isStrictNotEqual = 5 !== "5"; // true
let isGreater = 5 > 3; // true
let isLess = 5 < 3; // false
let isGreaterOrEqual = 5 >= 3; // true
let isLessOrEqual = 5 <= 3; // false

// Logical Operators
let and = true && false; // false
let or = true || false; // true
let not = !true; // false

// Bitwise Operators
let bitwiseAnd = 5 & 3; // 1
let bitwiseOr = 5 | 3; // 7
let bitwiseXor = 5 ^ 3; // 6
let bitwiseNot = ~5; // -6
let bitwiseLeftShift = 5 << 1; // 10
let bitwiseRightShift = 5 >> 1; // 2
let bitwiseUnsignedRightShift = 5 >>> 1; // 2
```

## Control Flow

```javascript
// If-Else
if (condition) {
  // code
} else if (anotherCondition) {
  // code
} else {
  // code
}

// Switch
switch (expression) {
  case value1:
    // code
    break;
  case value2:
    // code
    break;
  default:
    // code
    break;
}

// For Loop
for (let i = 0; i < 10; i++) {
  // code
}

// While Loop
let i = 0;
while (i < 10) {
  // code
  i++;
}

// Do-While Loop
let j = 0;
do {
  // code
  j++;
} while (j < 10);
```

## Functions

```javascript
// Function Declaration
function myFunction(param1, param2) {
  // code
}

// Function Expression
const myFunction = function (param1, param2) {
  // code
};

// Arrow Function
const myFunction = (param1, param2) => {
  // code
};

// Arrow Function (concise)
const myFunction = (param1, param2) => param1 + param2;
```

## Objects

```javascript
// Object Literal
let person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  fullName: function () {
    return this.firstName + " " + this.lastName;
  },
};

// Accessing Properties
let name = person.firstName; // "John"
let age = person["age"]; // 30

// Adding/Modifying Properties
person.job = "Developer";
person["city"] = "New York";

// Deleting Properties
delete person.age;
```

## Arrays

```javascript
// Array Declaration
let fruits = ["Apple", "Banana", "Cherry"];

// Accessing Elements
let firstFruit = fruits[0]; // "Apple"

// Adding Elements
fruits.push("Orange"); // Adds to the end
fruits.unshift("Mango"); // Adds to the beginning

// Removing Elements
let lastFruit = fruits.pop(); // Removes from the end
let firstFruit = fruits.shift(); // Removes from the beginning

// Iterating Over Arrays
fruits.forEach((fruit, index) => {
  console.log(fruit);
});

// Mapping Arrays
let upperFruits = fruits.map((fruit) => fruit.toUpperCase());

// Filtering Arrays
let filteredFruits = fruits.filter((fruit) => fruit.startsWith("A"));

// Reducing Arrays
let fruitString = fruits.reduce((acc, fruit) => acc + " " + fruit, "");
```

## Promises and Async/Await

```javascript
// Creating a Promise
let myPromise = new Promise((resolve, reject) => {
  let success = true;
  if (success) {
    resolve("Promise resolved!");
  } else {
    reject("Promise rejected!");
  }
});

// Using Promises
myPromise
  .then((response) => console.log(response))
  .catch((error) => console.log(error));

// Async/Await
async function myAsyncFunction() {
  try {
    let response = await myPromise;
    console.log(response);
  } catch (error) {
    console.log(error);
  }
}
```

## DOM Manipulation

```javascript
// Selecting Elements
let element = document.getElementById("myId");
let elements = document.getElementsByClassName("myClass");
let allElements = document.querySelectorAll("div");

// Modifying Elements
element.textContent = "Hello, World!";
element.innerHTML = "<strong>Hello, World!</strong>";

// Adding/Removing Classes
element.classList.add("newClass");
element.classList.remove("oldClass");

// Adding Event Listeners
element.addEventListener("click", function () {
  alert("Element clicked!");
});
```

## JSON

```javascript
// JSON to Object
let jsonString = '{"name": "John", "age": 30}';
let jsonObject = JSON.parse(jsonString);

// Object to JSON
let person = { name: "John", age: 30 };
let jsonString = JSON.stringify(person);
```

## Error Handling

```javascript
try {
  // code that may throw an error
} catch (error) {
  console.log(error.message);
} finally {
  // code that will always run
}
```

## ES6+ Features

```javascript
// Destructuring
let person = { name: "John", age: 30 };
let { name, age } = person;

// Template Literals
let greeting = `Hello, ${name}!`;

// Spread Operator
let newArray = [...arr, 4, 5, 6];
let newObject = { ...obj, newKey: "newValue" };

// Rest Parameters
function sum(...numbers) {
  return numbers.reduce((acc, number) => acc + number, 0);
}

// Default Parameters
function greet(name = "Guest") {
  console.log(`Hello, ${name}!`);
}
```

## Modules

```javascript
// Exporting (in module.js)
export const myVariable = "value";
export function myFunction() {
  // code
}
export default class MyClass {
  // code
}

// Importing (in main.js)
import { myVariable, myFunction } from "./module.js";
import MyClass from "./module.js";
```

## AJAX and Fetch API

```javascript
// Using XMLHttpRequest
let xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data");
xhr.onload = () => {
  if (xhr.status === 200) {
    console.log(xhr.responseText);
  }
};
xhr.send();

// Using Fetch API
fetch("https://api.example.com/data")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error));
```

## Local Storage

```javascript
// Set Item
localStorage.setItem("key", "value");

// Get Item
let value = localStorage.getItem("key");

// Remove Item
localStorage.removeItem("key");

// Clear All Items
localStorage.clear();
```

## Date and Time

```javascript
// Current Date and Time
let now = new Date();

// Specific Date
let specificDate = new Date("2023-01-01");

// Date Methods
let year = now.getFullYear();
let month = now.getMonth(); // 0-11
let day = now.getDate(); // 1-31
let hours = now.getHours(); // 0-23
let minutes = now.getMinutes(); // 0-59
let seconds = now.getSeconds(); // 0-59
```

## Useful Built-in Methods

```javascript
// Array Methods
let array = [1, 2, 3, 4, 5];
array.push(6); // [1, 2, 3, 4, 5, 6]
array.pop(); // [1, 2, 3, 4, 5]
array.shift(); // [2, 3, 4, 5]
array.unshift(1); // [1, 2, 3, 4, 5]
array.slice(1, 3); // [2, 3]
array.splice(2, 1); // [1, 2, 4, 5]

// String Methods
let str = "Hello, World!";
str.length; // 13
str.toUpperCase(); // "HELLO, WORLD!"
str.toLowerCase(); // "hello, world!"
str.indexOf("World"); // 7
str.substring(0, 5); // "Hello"
str.split(", "); // ["Hello", "World!"]
str.replace("World", "Everyone"); // "Hello, Everyone!"

// Number Methods
let num = 123.456;
num.toFixed(2); // "123.46"
num.toString(); // "123.456"
Number.parseInt("123"); // 123
Number.parseFloat("123.45"); // 123.45
```

## Event Handling

```javascript
// Add Event Listener
element.addEventListener("click", function (event) {
  console.log("Element clicked!");
});

// Remove Event Listener
element.removeEventListener("click", function (event) {
  console.log("Element clicked!");
});

// Event Object
element.addEventListener("click", function (event) {
  console.log(event.target); // Element that was clicked
  console.log(event.type); // "click"
  event.preventDefault(); // Prevent default action
});
```
