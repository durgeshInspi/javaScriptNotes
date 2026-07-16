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

---

# Interview Questions

### Basic

1. What is DOM?

2. Why is DOM used?

3. What is Document Object?

4. Difference between HTML and DOM?

5. What is getElementById()?

6. Difference between querySelector() and querySelectorAll()?

7. Difference between innerHTML and innerText?

8. Difference between innerText and textContent?

9. What is an Event?

10. What is addEventListener()?

---

# Practice Exercises

✅ Change heading color.

✅ Read user input.

✅ Display user input in paragraph.

✅ Increase Counter.

✅ Hide Paragraph.

✅ Show Paragraph.

✅ Change Image.

✅ Create New Button.

✅ Remove Paragraph.

✅ Build a Digital Clock.

---

# Summary

Today you learned

- What is DOM
- DOM Tree
- getElementById()
- querySelector()
- querySelectorAll()
- innerHTML
- innerText
- textContent
- style
- value
- createElement()
- appendChild()
- remove()
- Events
- onclick
- oninput
- addEventListener()

