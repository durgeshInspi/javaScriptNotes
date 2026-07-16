# 📘 JavaScript DOM Manipulation (1 Hour Notes)

> **Module:** JavaScript
> **Topic:** DOM Manipulation
> **Duration:** 1 Hour
> **Level:** Beginner

---

# What is DOM?

DOM stands for **Document Object Model**.

The DOM is a programming interface provided by the browser that allows JavaScript to access, modify, add, delete, and update HTML elements dynamically.

Simply,

> **DOM is a bridge between JavaScript and HTML.**

Without the DOM, JavaScript cannot change the webpage.

---

# Real Life Example

Imagine a classroom.

- HTML = Classroom
- CSS = Decoration
- JavaScript = Teacher
- DOM = Students

The teacher (JavaScript) gives instructions to students (DOM).

Example:

- Change Text
- Change Color
- Hide Element
- Add Image
- Remove Button

All these actions happen through the DOM.

---

# Why Do We Use DOM?

Using DOM we can

- Change text
- Change images
- Change colors
- Read input values
- Create new elements
- Remove elements
- Show or hide elements
- Build interactive websites

---

# DOM Tree

```

Window
|
Document
|
HTML
|
|---------------------------|
Head Body
|
|----------------|
h1 p button

```

JavaScript accesses HTML through this tree.

---

# Selecting Elements

JavaScript first finds an HTML element.

There are several methods.

## 1. getElementById()

HTML

```html
<h1 id="title">Hello World</h1>
```

JavaScript

```javascript
const heading = document.getElementById("title");

console.log(heading);
```

---

## 2. getElementsByClassName()

```html
<p class="text">First</p>
<p class="text">Second</p>
```

```javascript
const items = document.getElementsByClassName("text");

console.log(items);
```

Returns an HTML Collection.

---

## 3. getElementsByTagName()

```javascript
const paragraphs = document.getElementsByTagName("p");
```

---

## 4. querySelector()

Returns only the first matching element.

```javascript
const heading = document.querySelector("#title");
```

or

```javascript
const paragraph = document.querySelector(".text");
```

---

## 5. querySelectorAll()

Returns all matching elements.

```javascript
const paragraphs = document.querySelectorAll(".text");
```

---

# Changing Content

## innerHTML

```javascript
document.getElementById("title").innerHTML = "Welcome";
```

Output

```
Welcome
```

---

## innerText

```javascript
document.getElementById("title").innerText = "JavaScript";
```

---

## textContent

```javascript
document.getElementById("title").textContent = "DOM";
```

Difference

| innerHTML | innerText | textContent |
|------------|-----------|-------------|
| Reads HTML | Reads Visible Text | Reads All Text |

---

# Changing CSS

```javascript
const heading = document.getElementById("title");

heading.style.color = "red";
heading.style.background = "yellow";
heading.style.fontSize = "40px";
```

---

# Changing Attributes

HTML

```html
<img id="image" src="cat.jpg">
```

JavaScript

```javascript
document.getElementById("image").src = "dog.jpg";
```

---

# Reading Input Value

HTML

```html
<input id="username">

<button onclick="showName()">
Show
</button>
```

JavaScript

```javascript
function showName(){

    let value = document.getElementById("username").value;

    console.log(value);

}
```

---

# Changing Paragraph

HTML

```html
<input id="name">

<p id="output"></p>

<button onclick="display()">

Show

</button>
```

JavaScript

```javascript
function display(){

    const name = document.getElementById("name").value;

    document.getElementById("output").innerText = name;

}
```

---

# Creating Elements

```javascript
const heading = document.createElement("h1");

heading.innerText = "JavaScript";

document.body.appendChild(heading);
```

---

# Removing Elements

```javascript
const heading = document.getElementById("title");

heading.remove();
```

---

# Events

An event is an action performed by the user.

Examples

- Click
- Double Click
- Mouse Over
- Keyboard Press
- Submit Form
- Input

---

# Click Event

HTML

```html
<button onclick="changeText()">

Click

</button>

<h1 id="title">

Hello

</h1>
```

JavaScript

```javascript
function changeText(){

    document.getElementById("title").innerText = "Welcome";

}
```

---

# Input Event

HTML

```html
<input id="name" oninput="typing()">

<p id="result"></p>
```

JavaScript

```javascript
function typing(){

    const text = document.getElementById("name").value;

    document.getElementById("result").innerText = text;

}
```

This is called **Live Typing**.

---

# addEventListener()

Recommended way.

HTML

```html
<button id="btn">

Click

</button>
```

JavaScript

```javascript
const button = document.getElementById("btn");

button.addEventListener("click", function(){

    alert("Button Clicked");

});
```

---

# Mini Project 1

Click Counter

HTML

```html
<button id="btn">

Click

</button>

<h2 id="count">

0

</h2>
```

JavaScript

```javascript
let count = 0;

const button = document.getElementById("btn");

button.addEventListener("click", function(){

    count++;

    document.getElementById("count").innerText = count;

});
```

---

# Mini Project 2

Change Background Color

```javascript
const button = document.getElementById("btn");

button.addEventListener("click", function(){

    document.body.style.background = "skyblue";

});
```

---

# Mini Project 3

Show Password

```javascript
const password = document.getElementById("password");

function togglePassword(){

    if(password.type=="password"){

        password.type="text";

    }else{

        password.type="password";

    }

}
```






# 📘 JavaScript Advanced - Scope

> **Module:** Advanced JavaScript  
> **Topic:** Scope  
> **Level:** Beginner to Advanced

---

# 📖 What is Scope?

In JavaScript, **Scope** determines **where a variable or function can be accessed** within your program.

In simple words:

> **Scope defines the visibility and accessibility of variables and functions.**

If a variable is inside a particular scope, it can only be accessed where that scope allows.

---

# Why Do We Need Scope?

Scope helps us to:

- Prevent variable conflicts
- Improve code organization
- Increase security by hiding variables
- Reduce bugs
- Make code easier to maintain
- Control the lifetime of variables

---

# Real-Life Example

Imagine a school.

- 🌍 **Playground** → Everyone can access it. (Global Scope)
- 🏫 **Classroom** → Only students of that class can enter. (Function Scope)
- 📚 **Library Reading Room** → Only people inside the room can use it. (Block Scope)

Similarly, JavaScript variables have different levels of accessibility.

---

# Types of Scope

JavaScript has **three main types of scope**:

1. Global Scope
2. Function Scope
3. Block Scope

---

# 1️⃣ Global Scope

A variable declared **outside all functions and blocks** belongs to the **Global Scope**.

A global variable can be accessed from anywhere in the program.

## Syntax

```javascript
let company = "OpenAI";
```

---

## Example 1

```javascript
let language = "JavaScript";

function showLanguage() {
    console.log(language);
}

console.log(language);

showLanguage();
```

### Output

```
JavaScript
JavaScript
```

---

## Example 2

```javascript
let country = "India";

function state() {
    console.log(country);
}

function city() {
    console.log(country);
}

state();
city();
```

### Output

```
India
India
```

---

# Global Scope Diagram

```
Global Scope

│

├── Function A

│      │
│      └── Can Access Global Variable

│

├── Function B

│      │
│      └── Can Access Global Variable
```

---

# 2️⃣ Function Scope

Variables declared inside a function are called **Function Scoped Variables**.

These variables are only accessible inside that function.

---

## Example

```javascript
function student() {

    let name = "Durgesh";

    console.log(name);

}

student();
```

### Output

```
Durgesh
```

---

Trying to access it outside the function:

```javascript
console.log(name);
```

### Output

```
ReferenceError: name is not defined
```

---

## Another Example

```javascript
function add() {

    let a = 10;
    let b = 20;

    console.log(a + b);

}

add();
```

Output

```
30
```

Outside

```javascript
console.log(a);
```

Output

```
ReferenceError
```

---

# Function Scope Diagram

```
Global Scope

│

└── add()

      │

      ├── a

      ├── b

      └── Accessible only here
```

---

# 3️⃣ Block Scope

A block is created using curly braces `{ }`.

Variables declared with **let** and **const** are **Block Scoped**.

---

## Example

```javascript
if (true) {

    let city = "Lucknow";

    console.log(city);

}
```

Output

```
Lucknow
```

Outside

```javascript
console.log(city);
```

Output

```
ReferenceError
```

---

## Another Example

```javascript
{

    const pi = 3.14;

    console.log(pi);

}
```

Output

```
3.14
```

Outside

```javascript
console.log(pi);
```

Output

```
ReferenceError
```

---

# Block Scope Diagram

```
if()

│

├── city

└── Accessible only inside this block
```

---

# Scope Chain

When JavaScript cannot find a variable inside the current scope, it searches in the outer scope.

This process continues until the variable is found or the global scope is reached.

This is called the **Scope Chain**.

---

## Example

```javascript
let company = "OpenAI";

function first() {

    function second() {

        console.log(company);

    }

    second();

}

first();
```

Output

```
OpenAI
```

---

# Scope Chain Flow

```
second()

↓

first()

↓

Global Scope

↓

Found company
```

---

# Nested Scope

A child scope can access variables from its parent scope.

The parent scope **cannot** access variables declared inside the child scope.

---

## Example

```javascript
let country = "India";

function state() {

    let city = "Lucknow";

    console.log(country);

    console.log(city);

}

state();
```

Output

```
India
Lucknow
```

Outside

```javascript
console.log(city);
```

Output

```
ReferenceError
```

---

# Lexical Scope

JavaScript follows **Lexical Scope**.

This means a function can access variables based on **where it is written**, not where it is called.

---

## Example

```javascript
let language = "JavaScript";

function outer() {

    let version = "ES6";

    function inner() {

        console.log(language);

        console.log(version);

    }

    inner();

}

outer();
```

Output

```
JavaScript
ES6
```

---

# var vs let vs const

## Using var

```javascript
if (true) {

    var number = 100;

}

console.log(number);
```

Output

```
100
```

Why?

Because **var is NOT Block Scoped**.

---

## Using let

```javascript
if (true) {

    let number = 100;

}

console.log(number);
```

Output

```
ReferenceError
```

---

## Using const

```javascript
if (true) {

    const number = 100;

}

console.log(number);
```

Output

```
ReferenceError
```

---

# Scope Comparison Table

| Feature | var | let | const |
|---------|-----|-----|-------|
| Global Scope | ✅ | ✅ | ✅ |
| Function Scope | ✅ | ✅ | ✅ |
| Block Scope | ❌ | ✅ | ✅ |
| Redeclare | ✅ | ❌ | ❌ |
| Reassign | ✅ | ✅ | ❌ |

---

# Global vs Function vs Block Scope

| Scope Type | Accessible From |
|------------|-----------------|
| Global Scope | Everywhere |
| Function Scope | Inside the Function Only |
| Block Scope | Inside the Block `{}` Only |

---

# Best Practices

✅ Use `const` by default.

✅ Use `let` when the value needs to change.

❌ Avoid using `var` in modern JavaScript because it ignores block scope and can cause unexpected bugs.

---

# Practice Programs

## Program 1

```javascript
let a = 10;

function demo() {

    console.log(a);

}

demo();
```

Output

```
10
```

---

## Program 2

```javascript
function demo() {

    let a = 20;

}

console.log(a);
```

Output

```
ReferenceError
```

---

## Program 3

```javascript
if (true) {

    var x = 100;

}

console.log(x);
```

Output

```
100
```

---

## Program 4

```javascript
if (true) {

    let x = 100;

}

console.log(x);
```

Output

```
ReferenceError
```

---

## Program 5

```javascript
const name = "Durgesh";

function greet() {

    console.log(name);

}

greet();
```

Output

```
Durgesh
```

---

# Common Mistakes

❌ Accessing a function variable outside the function.

```javascript
function demo() {
    let x = 10;
}

console.log(x);
```

Result:

```
ReferenceError
```

---

❌ Using `var` inside blocks expecting block scope.

```javascript
if (true) {
    var age = 22;
}

console.log(age);
```

Output

```
22
```



