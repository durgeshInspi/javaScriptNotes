# JavaScript Hoisting

## What is Hoisting?

**Hoisting** is JavaScript's default behavior of moving **declarations** (variables and functions) to the top of their scope before the code is executed.

> **Important:** JavaScript does **not physically move** your code. During execution, it first scans the entire code and allocates memory for variables and functions. This process is called **Hoisting**.

---

# JavaScript Execution Phases

Whenever JavaScript runs a program, it executes in **two phases**.

```
JavaScript Engine
       │
       ▼
1. Memory Creation Phase
   (Hoisting)
       │
       ▼
2. Execution Phase
```

---

# 1. Memory Creation Phase

During this phase, JavaScript scans the entire code and allocates memory.

- Variables declared with `var` are initialized with `undefined`.
- Variables declared with `let` and `const` are hoisted but remain in the **Temporal Dead Zone (TDZ)**.
- Function declarations are stored completely in memory.

Example:

```javascript
var name = "abcd";

function greet() {
    console.log("Hello");
}
```

### Memory

```
name  ----------> undefined

greet ----------> Complete Function
```

At this stage:

- `"abcd"` is **not assigned** yet.
- Only memory is allocated.

---

# 2. Execution Phase

Now JavaScript executes the code line by line.

```javascript
var name = "abcd";

console.log(name);
```

Execution:

```
name = "abcd"

↓

console.log(name)

↓

abcd
```

---

# Variable Hoisting (`var`)

Example

```javascript
console.log(a);

var a = 10;
```

### Output

```text
undefined
```

---

## What Happens Internally?

### Original Code

```javascript
console.log(a);

var a = 10;
```

### Memory Creation Phase

```
a
↓

undefined
```

### Execution Phase

```
console.log(a)

↓

undefined

↓

a = 10
```

JavaScript behaves like this:

```javascript
var a;

console.log(a);

a = 10;
```

---

# Example 2

```javascript
console.log(city);

var city = "Lucknow";

console.log(city);
```

### Output

```text
undefined
Lucknow
```

---

# Function Hoisting

Function declarations are **fully hoisted**.

Example

```javascript
sayHello();

function sayHello() {
    console.log("Hello JavaScript");
}
```

### Output

```text
Hello JavaScript
```

---

### Memory Phase

```
sayHello

↓

Complete Function
```

Since the entire function is stored in memory, it can be called before its declaration.

---

# Another Function Example

```javascript
sum(10, 20);

function sum(a, b) {
    console.log(a + b);
}
```

### Output

```text
30
```

---

# Function Expression Hoisting

Example

```javascript
sayHi();

var sayHi = function () {
    console.log("Hi");
};
```

### Output

```text
TypeError: sayHi is not a function
```

---

## Why?

### Memory Phase

```
sayHi

↓

undefined
```

### Execution Phase

```javascript
sayHi();
```

JavaScript tries to execute:

```javascript
undefined();
```

Result:

```text
TypeError
```

After that,

```javascript
sayHi = function () {
    console.log("Hi");
};
```

Now `sayHi` becomes a function.

---

# Arrow Function Hoisting

Example

```javascript
hello();

const hello = () => {
    console.log("Hello");
};
```

### Output

```text
ReferenceError: Cannot access 'hello' before initialization
```

---

# Why?

Variables declared with `const` stay inside the **Temporal Dead Zone (TDZ)** until their declaration.

Memory

```
hello

↓

TDZ
```

---

# Hoisting with `let`

```javascript
console.log(age);

let age = 22;
```

### Output

```text
ReferenceError
```

---

# Hoisting with `const`

```javascript
console.log(name);

const name = "abcd";
```

### Output

```text
ReferenceError
```

---

# Temporal Dead Zone (TDZ)

The **Temporal Dead Zone (TDZ)** is the period between the start of the block and the point where a `let` or `const` variable is declared.

Diagram

```
Memory Creation

↓

TDZ

↓

let age = 22;

↓

Accessible
```

---

# Memory Diagram

```javascript
var a = 10;

let b = 20;

const c = 30;

function hello() {
    console.log("Hello");
}
```

## Memory Creation Phase

```
Global Memory

a ---------> undefined

b ---------> TDZ

c ---------> TDZ

hello -----> Complete Function
```

---

## Execution Phase

```
a = 10

↓

b = 20

↓

c = 30
```

---

# Real-Life Analogy

Imagine a teacher entering a classroom.

### Step 1

The teacher takes attendance.

```
Attendance

↓

Teaching
```

JavaScript also works in the same way.

### Step 1

It creates memory.

### Step 2

It executes the code.

```
Memory Creation

↓

Execution
```

---

# `var` vs `let` vs `const`

| Feature | var | let | const |
|----------|-----|-----|--------|
| Hoisted | ✅ Yes | ✅ Yes | ✅ Yes |
| Initial Value | `undefined` | TDZ | TDZ |
| Access Before Declaration | `undefined` | ReferenceError | ReferenceError |
| Redeclaration | ✅ Allowed | ❌ Not Allowed | ❌ Not Allowed |
| Reassignment | ✅ Allowed | ✅ Allowed | ❌ Not Allowed |
| Block Scope | ❌ No | ✅ Yes | ✅ Yes |

---

# Interview Questions

## Question 1

```javascript
console.log(a);

var a = 10;
```

Output

```text
undefined
```

---

## Question 2

```javascript
console.log(a);

let a = 10;
```

Output

```text
ReferenceError
```

---

## Question 3

```javascript
hello();

function hello() {
    console.log("Hello");
}
```

Output

```text
Hello
```

---

## Question 4

```javascript
hello();

var hello = function () {
    console.log("Hello");
};
```

Output

```text
TypeError
```

---

## Question 5

```javascript
function demo() {
    console.log(age);

    var age = 22;
}

demo();
```

Output

```text
undefined
```

Equivalent Code

```javascript
function demo() {

    var age;

    console.log(age);

    age = 22;

}
```

---

## Question 6

```javascript
console.log(typeof a);

var a = 10;
```

Output

```text
undefined
```

---

# Common Mistakes

### Mistake 1

```javascript
console.log(user);

let user = "abcd";
```

❌ Result

```text
ReferenceError
```

---

### Mistake 2

```javascript
login();

const login = () => {
    console.log("Login");
};
```

❌ Result

```text
ReferenceError
```

---

### Mistake 3

```javascript
show();

var show = function () {
    console.log("Show");
};
```

❌ Result

```text
TypeError
```

---

# Key Points to Remember

- Hoisting happens during the **Memory Creation Phase**.
- JavaScript executes code in **two phases**:
  1. Memory Creation Phase
  2. Execution Phase
- `var` is hoisted and initialized with `undefined`.
- `let` and `const` are hoisted but remain inside the **Temporal Dead Zone (TDZ)**.
- Function declarations are fully hoisted.
- Function expressions are **not** fully hoisted.
- Arrow functions behave like variables and cannot be used before initialization.
- Hoisting applies to **declarations**, not to **initializations**.

---

# Summary

✅ Hoisting is JavaScript's default behavior.

✅ JavaScript allocates memory before executing code.

✅ `var` variables are initialized with `undefined`.

✅ `let` and `const` remain inside the **Temporal Dead Zone (TDZ)** until their declaration.

✅ Function declarations can be called before they are defined.

✅ Function expressions and arrow functions cannot be called before initialization.
