# Day 01 - JavaScript Fundamentals

> **Topic:** Variables (`var`, `let`, `const`)

---


# What is a Variable?

A **variable** is a named container used to store data in memory.

Think of it as a **box** that stores information.

Example:

```javascript
let name = "Rahul";
```

Here,

- `let` → Keyword
- `name` → Variable Name
- `"Rahul"` → Value

---

# Why Do We Need Variables?

Without variables, we cannot store data.

Examples:

- Student Name
- Age
- Marks
- Salary
- Product Price
- Mobile Number

Example:

```javascript
let studentName = "Rahul";
let age = 21;
let city = "Lucknow";

console.log(studentName);
console.log(age);
console.log(city);
```

Output

```
Rahul
21
Lucknow
```

---

# Variable Declaration Rules in JavaScript

1. A variable must be declared using `var`, `let`, or `const`.

2. A variable name cannot start with a number.

   ❌ `let 1name = "Rahul";`

   ✅ `let name1 = "Rahul";`

3. A variable name can start with:
   - Letter (a-z, A-Z)
   - Underscore (_)
   - Dollar sign ($)

4. Variable names cannot contain spaces.

   ❌ `let first name = "Rahul";`

   ✅ `let firstName = "Rahul";`

5. Variable names are case-sensitive.

   `name` and `Name` are different variables.

6. Use camelCase naming convention.

   Example:

   `let studentName = "Amit";`

7. Do not use JavaScript reserved keywords.

   ❌ `let class = "MERN";`

8. Variable names should be meaningful.

   ❌ `let x = 500;`

   ✅ `let productPrice = 500;`

9. Avoid special characters except `_` and `$`.

   ❌ `let user-name = "Rahul";`

10. Do not create variables with only single letters unless required.

11. Use `const` when the value does not change.

12. Use `let` when the value needs to change.

13. Avoid using `var` in modern JavaScript.

14. A variable should be declared before using it.

15. Variable names should be easy to understand for other developers.

16. Constants are usually written in uppercase.

   Example:

   `const PI = 3.14159;`

17. Variable names cannot contain hyphens (`-`).

18. Variable names can contain numbers after the first character.

   Example:

   `let user1 = "Rahul";`

19. Keep variable names short but descriptive.

20. Always follow consistent naming rules in your projects.

# JavaScript Variable Keywords

JavaScript provides three keywords for creating variables.

- var
- let
- const

---

# 1. var

`var` is the old way of creating variables.

It was introduced before ES6.

Nowadays, it is **not recommended** for modern JavaScript projects.

---

## Syntax

```javascript
var variableName = value;
```

Example

```javascript
var name = "Rahul";

console.log(name);
```

Output

```
Rahul
```

---

## Properties of var

- Function Scoped
- Can be Redeclared
- Can be Reassigned
- Hoisted
- Initial value is `undefined`

---

## Redeclaration Example

```javascript
var city = "Delhi";

var city = "Lucknow";

console.log(city);
```

Output

```
Lucknow
```

No error occurs because `var` allows redeclaration.

---

## Reassignment Example

```javascript
var age = 20;

age = 25;

console.log(age);
```

Output

```
25
```

---

# 2. let

`let` was introduced in **ES6 (2015)**.

It is the preferred keyword when a variable's value needs to change.

---

## Syntax

```javascript
let variableName = value;
```

Example

```javascript
let name = "Rahul";

console.log(name);
```

Output

```
Rahul
```

---

## Properties of let

- Block Scoped
- Cannot be Redeclared
- Can be Reassigned
- Hoisted (Temporal Dead Zone)

---

## Redeclaration Example

```javascript
let city = "Delhi";

let city = "Lucknow";
```

Output

```
SyntaxError
```

---

## Reassignment Example

```javascript
let marks = 80;

marks = 95;

console.log(marks);
```

Output

```
95
```

---

# 3. const

`const` is used for values that should not be reassigned.

It was also introduced in ES6.

---

## Syntax

```javascript
const variableName = value;
```

Example

```javascript
const PI = 3.14159;

console.log(PI);
```

Output

```
3.14159
```

---

## Properties of const

- Block Scoped
- Cannot be Redeclared
- Cannot be Reassigned
- Must be Initialized

---

## Reassignment Example

```javascript
const country = "India";

country = "USA";
```

Output

```
TypeError
```

---

# Important Note

Although a `const` variable cannot be reassigned, **objects and arrays declared with `const` can still have their contents modified.**

Example

```javascript
const student = {
    name: "Rahul"
};

student.name = "Aman";

console.log(student);
```

Output

```javascript
{
    name: "Aman"
}
```

---

# Scope

Scope means **where a variable can be accessed**.

JavaScript has two common scopes:

- Function Scope
- Block Scope

---

## var Example

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

Because `var` is function scoped.

---

## let Example

```javascript
if (true) {
    let y = 200;
}

console.log(y);
```

Output

```
ReferenceError
```

Because `let` is block scoped.

---

## const Example

```javascript
if (true) {
    const z = 300;
}

console.log(z);
```

Output

```
ReferenceError
```

---

# Hoisting

Hoisting means JavaScript moves variable declarations to the top of their scope before executing the code.

---

## var Hoisting

```javascript
console.log(a);

var a = 10;
```

Output

```
undefined
```

---

## let Hoisting

```javascript
console.log(b);

let b = 20;
```

Output

```
ReferenceError
```

---

## const Hoisting

```javascript
console.log(c);

const c = 30;
```

Output

```
ReferenceError
```

---

# Difference Between var, let and const

| Feature | var | let | const |
|----------|-----|-----|-------|
| Scope | Function | Block | Block |
| Redeclare | ✅ Yes | ❌ No | ❌ No |
| Reassign | ✅ Yes | ✅ Yes | ❌ No |
| Must Initialize | ❌ No | ❌ No | ✅ Yes |
| Hoisted | ✅ Yes | ✅ Yes (TDZ) | ✅ Yes (TDZ) |
| Modern Use | ❌ Avoid | ✅ Yes | ✅ Yes |

---

# Which One Should You Use?

### Use `const`

When the value should never change.

```javascript
const PI = 3.14;
```

---

### Use `let`

When the value needs to change.

```javascript
let score = 0;

score++;
```

---

### Avoid `var`

Only use it when maintaining old JavaScript code.

---

# Best Practice

Modern JavaScript developers usually follow this rule:

- Use **const** by default.
- Use **let** only when reassignment is required.
- Avoid **var**.

---

# Real-Life Example

```javascript
const collegeName = "ABC College";

let studentName = "Rahul";

let marks = 85;

marks = 95;

console.log(collegeName);
console.log(studentName);
console.log(marks);
```

Output

```
ABC College
Rahul
95
```

---

# Practice Programs

## Program 1

Create variables using all three keywords.

```javascript
var city = "Lucknow";

let age = 22;

const country = "India";

console.log(city);
console.log(age);
console.log(country);
```

---

## Program 2

Reassign a variable.

```javascript
let salary = 25000;

salary = 30000;

console.log(salary);
```

---

## Program 3

Try changing a constant.

```javascript
const PI = 3.14;

PI = 3.14159;
```

Observe the error.

---

## Program 4

Create a Student Object.

```javascript
const student = {
    name: "Rahul",
    age: 20
};

student.age = 21;

console.log(student);
```

---
