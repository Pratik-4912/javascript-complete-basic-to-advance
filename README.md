## Part 1: What is JavaScript?

JavaScript (JS) gives a web page **logic/behavior/interactivity**. HTML builds the structure, CSS handles the styling, and JS makes the page **live/dynamic** (button clicks, form validation, animations, etc.).

**Where to write JS:**

```html
<!-- 1. Internal - at the end of body -->
<body>
  ...
  <script>
    console.log("Hello!");
  </script>
</body>

<!-- 2. External file (best practice) -->
<head>
  <script src="script.js" defer></script>
</head>
```

The `defer` attribute runs the JS only after the HTML has fully loaded — this is best practice.

---

## Part 2: Variables

```javascript
var x = 10;      // old way, avoid it (function-scoped, can be redeclared)
let y = 20;       // modern way, value can change (block-scoped)
const z = 30;      // value stays fixed, cannot be changed

console.log(y);   // 20
y = 25;             // fine
// z = 35;          // Error! const cannot be changed
```

---

## Part 3: Data Types

```javascript
let name = "Ram";           // String
let age = 25;                // Number
let isStudent = true;        // Boolean
let hobbies = ["cricket", "reading"];  // Array
let person = { name: "Ram", age: 25 }; // Object
let empty = null;             // Null (intentionally empty)
let notDefined;                // Undefined (no value assigned)

console.log(typeof age);      // "number"
console.log(typeof name);     // "string"
```

---

## Part 4: Operators

```javascript
// Arithmetic
let sum = 5 + 3;      // 8
let diff = 5 - 3;      // 2
let mul = 5 * 3;        // 15
let div = 5 / 3;         // 1.666
let mod = 5 % 3;          // 2 (remainder)
let power = 5 ** 2;        // 25

// Comparison
console.log(5 == "5");    // true (checks value only)
console.log(5 === "5");   // false (checks value + type both) - use this!
console.log(5 !== "5");   // true

// Logical
console.log(true && false);   // AND - false
console.log(true || false);   // OR - true
console.log(!true);            // NOT - false

// Assignment
let a = 5;
a += 3;   // a = a + 3
a -= 2;   // a = a - 2
```

---

## Part 5: Strings

```javascript
let firstName = "Ram";
let lastName = "Sharma";

// Template literals (using backticks)
let fullName = `${firstName} ${lastName}`;
console.log(fullName);   // Ram Sharma

// Common string methods
let str = "Hello World";
console.log(str.length);            // 11
console.log(str.toUpperCase());     // HELLO WORLD
console.log(str.toLowerCase());     // hello world
console.log(str.includes("World")); // true
console.log(str.slice(0, 5));        // Hello
console.log(str.replace("World", "There")); // Hello There
console.log(str.split(" "));          // ["Hello", "World"]
console.log(str.trim());               // removes extra spaces
```

---

## Part 6: Conditionals (Decision Making)

```javascript
let age = 20;

if (age >= 18) {
  console.log("You are an adult");
} else if (age >= 13) {
  console.log("You are a teenager");
} else {
  console.log("You are a child");
}

// Ternary operator (short if-else)
let result = age >= 18 ? "Adult" : "Minor";

// Switch case
let day = 2;
switch (day) {
  case 1:
    console.log("Monday");
    break;
  case 2:
    console.log("Tuesday");
    break;
  default:
    console.log("Unknown day");
}
```

---

## Part 7: Loops

```javascript
// For loop
for (let i = 0; i < 5; i++) {
  console.log(i);   // 0,1,2,3,4
}

// While loop
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}

// Do-while (runs at least once)
let j = 0;
do {
  console.log(j);
  j++;
} while (j < 5);

// For...of (for arrays)
let fruits = ["Apple", "Mango", "Banana"];
for (let fruit of fruits) {
  console.log(fruit);
}

// For...in (for objects)
let person = { name: "Ram", age: 25 };
for (let key in person) {
  console.log(key, person[key]);
}

// break and continue
for (let i = 0; i < 10; i++) {
  if (i === 5) break;      // stops the loop
  if (i === 2) continue;    // skips that iteration
  console.log(i);
}
```

---

## Part 8: Functions

```javascript
// Normal function
function greet(name) {
  return `Hello, ${name}!`;
}
console.log(greet("Ram"));

// Function expression
const add = function(a, b) {
  return a + b;
};

// Arrow function (modern, short syntax)
const multiply = (a, b) => a * b;
const square = x => x * x;   // parentheses optional for single param

// Default parameters
function greetUser(name = "Guest") {
  console.log(`Hi ${name}`);
}

// Rest parameters (unlimited arguments)
function sumAll(...numbers) {
  return numbers.reduce((total, n) => total + n, 0);
}
console.log(sumAll(1, 2, 3, 4));   // 10
```

---

## Part 9: Arrays

```javascript
let numbers = [10, 20, 30, 40, 50];

console.log(numbers[0]);        // 10 (indexing starts at 0)
console.log(numbers.length);     // 5

numbers.push(60);          // add to the end
numbers.pop();               // remove from the end
numbers.unshift(5);           // add to the beginning
numbers.shift();                // remove from the beginning

console.log(numbers.indexOf(30)); // find the index of an element

// Important array methods (VERY IMPORTANT!)
let nums = [1, 2, 3, 4, 5];

let doubled = nums.map(n => n * 2);          // [2,4,6,8,10] - transforms each item
let evens = nums.filter(n => n % 2 === 0);    // [2,4] - filters by condition
let total = nums.reduce((sum, n) => sum + n, 0); // 15 - combines everything into one value
let found = nums.find(n => n > 3);             // 4 - first matching element
let hasEven = nums.some(n => n % 2 === 0);       // true - true if any match
let allPositive = nums.every(n => n > 0);         // true - true if all match

nums.forEach(n => console.log(n));    // loops over each item

let sorted = [5, 2, 8, 1].sort((a, b) => a - b);  // ascending sort
```

---

## Part 10: Objects

```javascript
let person = {
  name: "Ram",
  age: 25,
  city: "Pune",
  greet: function() {
    console.log(`Hello, I am ${this.name}`);
  }
};

console.log(person.name);      // dot notation
console.log(person["age"]);     // bracket notation
person.greet();                   // Hello, I am Ram

person.job = "Engineer";        // add a new property
delete person.city;              // remove a property

// Object destructuring
let { name, age } = person;
console.log(name, age);

// Object.keys, values, entries
console.log(Object.keys(person));     // all keys
console.log(Object.values(person));   // all values
```

---

## Part 11: DOM Manipulation (Very Important!)

The DOM (Document Object Model) is what gives JS the power to change HTML.

```javascript
// Selecting elements
document.getElementById("myId");
document.querySelector(".myClass");     // first matching element
document.querySelectorAll("p");          // all matching elements (list)

// Changing content
let elem = document.getElementById("title");
elem.textContent = "New Text";     // text only
elem.innerHTML = "<b>Bold Text</b>"; // includes HTML

// Changing style
elem.style.color = "red";
elem.style.fontSize = "20px";

// Managing classes
elem.classList.add("active");
elem.classList.remove("active");
elem.classList.toggle("active");    // removes if present, adds if not

// Managing attributes
elem.setAttribute("src", "photo.jpg");
elem.getAttribute("src");

// Creating a new element
let newDiv = document.createElement("div");
newDiv.textContent = "I am a new div";
document.body.appendChild(newDiv);

// Removing an element
elem.remove();
```

---

## Part 12: Events (User Interaction)

```javascript
let btn = document.getElementById("myButton");

btn.addEventListener("click", function() {
  console.log("Button was clicked!");
});

// Using an arrow function
btn.addEventListener("click", () => {
  alert("Hello!");
});

// Common events
elem.addEventListener("mouseover", () => console.log("Mouse entered"));
elem.addEventListener("keydown", (e) => console.log(e.key));
form.addEventListener("submit", (e) => {
  e.preventDefault();   // stops the form's default submit behavior
  console.log("Form submitted");
});

// Event object
btn.addEventListener("click", function(event) {
  console.log(event.target);   // which element was clicked
});
```

---

## Part 13: Timers

```javascript
// Runs once after a set time
setTimeout(() => {
  console.log("This prints after 3 seconds");
}, 3000);

// Runs repeatedly at a set interval
let interval = setInterval(() => {
  console.log("This prints every 1 second");
}, 1000);

clearInterval(interval);   // to stop an interval
clearTimeout(timeoutId);    // to stop a timeout
```

---

## Part 14: Async JavaScript (Advanced)

```javascript
// Callback (old way)
function fetchData(callback) {
  setTimeout(() => {
    callback("Data received!");
  }, 1000);
}
fetchData((data) => console.log(data));

// Promises
let promise = new Promise((resolve, reject) => {
  let success = true;
  if (success) {
    resolve("Task completed!");
  } else {
    reject("An error occurred!");
  }
});

promise
  .then((result) => console.log(result))
  .catch((error) => console.log(error));

// Async/Await (modern, the easiest way)
async function getData() {
  try {
    let response = await fetch("https://api.example.com/data");
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.log("Error:", error);
  }
}
getData();
```

---

## Part 15: Fetch API (Getting Data From a Server)

```javascript
fetch("https://jsonplaceholder.typicode.com/users")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.log("Error:", error));

// Using async/await (better approach)
async function loadUsers() {
  let res = await fetch("https://jsonplaceholder.typicode.com/users");
  let users = await res.json();
  users.forEach(user => console.log(user.name));
}
```

---

## Part 16: Error Handling

```javascript
try {
  let result = someUndefinedFunction();
} catch (error) {
  console.log("An error occurred:", error.message);
} finally {
  console.log("This always runs");
}

// Manually throwing an error
function checkAge(age) {
  if (age < 0) {
    throw new Error("Age cannot be negative");
  }
  return age;
}
```

---

## Part 17: ES6+ Advanced Features

```javascript
// Spread operator
let arr1 = [1, 2, 3];
let arr2 = [...arr1, 4, 5];   // [1,2,3,4,5]

let obj1 = { a: 1, b: 2 };
let obj2 = { ...obj1, c: 3 };   // {a:1, b:2, c:3}

// Destructuring
let [first, second] = [10, 20];
let { name, age } = { name: "Ram", age: 25 };

// Template literals
let msg = `Name: ${name}, Age: ${age}`;

// Optional chaining
let user = { address: { city: "Pune" } };
console.log(user?.address?.city);    // Pune (safely accesses without throwing an error)

// Nullish coalescing
let value = null ?? "Default Value";   // uses the default only if value is null/undefined

// Modules (export/import)
// file1.js
export function greet() { console.log("Hi"); }
// file2.js
import { greet } from './file1.js';
```

---

## Part 18: Classes (OOP in JS)

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, I am ${this.name}`);
  }
}

let p1 = new Person("Ram", 25);
p1.greet();

// Inheritance
class Student extends Person {
  constructor(name, age, course) {
    super(name, age);
    this.course = course;
  }

  study() {
    console.log(`${this.name} is studying ${this.course}`);
  }
}

let s1 = new Student("Sita", 20, "Computer Science");
s1.greet();
s1.study();
```

---

## Part 19: Local Storage (Saving Data in the Browser)

```javascript
// Saving data
localStorage.setItem("username", "Ram");

// Retrieving data
console.log(localStorage.getItem("username"));

// Removing data
localStorage.removeItem("username");
localStorage.clear();    // removes everything

// Saving an object requires JSON
localStorage.setItem("user", JSON.stringify({ name: "Ram", age: 25 }));
let user = JSON.parse(localStorage.getItem("user"));
