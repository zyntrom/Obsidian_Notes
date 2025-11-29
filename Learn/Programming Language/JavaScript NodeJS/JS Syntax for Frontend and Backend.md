# 📘 JavaScript Complete Notes (Frontend + Backend)

---

## 1. Basics of JavaScript

### 1.1 Introduction

- **JavaScript**: high-level, dynamic, interpreted programming language.
- Used for:
    - **Frontend**: DOM manipulation, events, UI.
    - **Backend**: Server logic with Node.js.
- Runs inside browser or Node.js runtime.

### 1.2 Variables

- Declaring variables:
    - `var`: old, function-scoped.
    - `let`: block-scoped, mutable.
    - `const`: block-scoped, immutable reference.

`let age = 21; const pi = 3.14; var oldVar = "deprecated";`

---

## 2. Data Types

### 2.1 Primitive Types

- **String**: `"hello"`
- **Number**: `42`, `3.14`
- **Boolean**: `true`, `false`
- **Null**: intentional empty value
- **Undefined**: declared but not assigned
- **Symbol**: unique identifier
- **BigInt**: large integers

### 2.2 Reference Types

- **Object**: `{ key: value }`
- **Array**: `[1,2,3]`
- **Function**: `function() {}`

---

## 3. Operators

### 3.1 Arithmetic

```
+, -, *, /, %, **
```

### 3.2 Comparison

```
== (loose), === (strict), !=, !== , <, >, <=, >=
```

### 3.3 Logical

```js
&& (AND), || (OR), ! (NOT)
```

### 3.4 Assignment

```js
=, +=, -=, *=, /=
```

### 3.5 Ternary

```js
let result = (age >= 18) ? "Adult" : "Minor";
```

---

## 4. Control Flow

### 4.1 Conditional Statements

```js
if (condition) {   
	// code 
} else if (another) {   
	// code 
} else {   
	// code 
}
```

### 4.2 Switch

```js
switch(day) {   
	case "Mon": 
		console.log("Work"); 
		break;   
	case "Sun": 
		console.log("Rest"); 
		break;   
	default: 
		console.log("Invalid"); 
}
```

---

## 5. Loops

### 5.1 For

```js
for (let i = 0; i < 5; i++) {   console.log(i); }
```

### 5.2 While

```js
let i = 0; while (i < 5) {   console.log(i);   i++; }
```

### 5.3 For...of (arrays)

```js
for (let num of [1,2,3]) console.log(num);
```

### 5.4 For...in (objects)

```js
for (let key in obj) console.log(key, obj[key]);
```

---

## 6. Functions

### 6.1 Declaration

```js
function add(a, b) {   return a + b; }
```

### 6.2 Expression

```js
const multiply = function(a, b) { return a * b; };
```

### 6.3 Arrow Function

```js
const square = (x) => x * x;
```

### 6.4 Default Params & Rest

```js
function greet(name="Guest") { console.log("Hello " + name); } 
function sum(...nums) { return nums.reduce((a,b) => a+b, 0); }
```

---

## 7. Objects

### 7.1 Create

```js
const person = { name: "John", age: 30 };
```

### 7.2 Access

```js
console.log(person.name); console.log(person["age"]);
```

### 7.3 Destructuring

```js
const {name, age} = person;
```

### 7.4 Spread Operator

```js
const newObj = { ...person, city: "NY" };
```

---

## 8. Arrays

### 8.1 Create

```js
let arr = [1,2,3];
```

### 8.2 Methods

- `push()`, `pop()`, `shift()`, `unshift()`
- `map()`, `filter()`, `reduce()`
- `forEach()`, `find()`, `some()`, `every()`
- `includes()`, `indexOf()`, `concat()`, `slice()`, `splice()`

---

## 9. Strings

### 9.1 Template Literals

```js
let name = "John"; console.log(`Hello, ${name}!`);
```

### 9.2 Common Methods

- `length`
- `toUpperCase()`, `toLowerCase()`
- `trim()`
- `slice(start,end)`
- `substring(start,end)`
- `split()`
- `replace()`
- `includes()`

---

## 10. Advanced Concepts

### 10.1 Closures

Function inside function remembers outer scope.

```js
function outer() {   
	let count = 0;   
	return function inner() { 
		count++; 
		return count; 
	}; 
} 
const counter = outer();
```

### 10.2 Callbacks

```js
function greet(cb) { cb("Hello"); } 
greet(msg => console.log(msg));
```

### 10.3 Promises

```js
let promise = new Promise((resolve,reject)=>{   
	resolve("Success"); }); 
promise.then(res=>console.log(res));
```

### 10.4 Async/Await

```js
async function fetchData() {   
	let res = await 
	fetch("url");   
	let data = await res.json(); 
}
```

---

## 11. DOM (Frontend only)

### 11.1 Selectors

```js
document.getElementById("id"); 
document.querySelector(".class"); 
document.querySelectorAll("p");
```

### 11.2 Manipulation

```js
element.textContent = "New Text"; 
element.style.color = "red";
element.setAttribute("href", "#");
```

### 11.3 Events

```js
button.addEventListener("click", () => alert("Clicked"));
```

---

## 12. ES6+ Features

- **Destructuring**
- **Spread & Rest**
- **Modules**

```js
//export.js 
export const pi = 3.14; 
// import.js 
import { pi } from "./export.js";
```

- **Classes**

```js
class Person {   
	constructor(name) { 
		this.name = name; 
	}   
	greet() { 
		console.log("Hi " + this.name); 
	}
}
```

---

## 13. Backend-Specific (Node.js)

### 13.1 Modules

```js
const fs = require("fs");
```

### 13.2 File System

```js
fs.readFile("file.txt", "utf-8", (err, data)=>{});
```

### 13.3 HTTP Server

```js
const http = require("http"); 
http.createServer((req,res)=> {   
	res.end("Hello Server"); 
}).listen(5000);
```

### 13.4 npm & Packages

- Install: `npm install express`
- Use in code.

---

## 14. Error Handling

```js
try {   
	throw new Error("Something went wrong"); 
} catch(err) {   
	console.error(err.message); 
} finally {   
	console.log("Cleanup"); 
}
```