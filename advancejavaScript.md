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



# Higher-Order Functions in JavaScript

## Table of Contents

1. What is a Higher-Order Function?
2. Why Do We Use Higher-Order Functions?
3. Characteristics of Higher-Order Functions
4. `map()`
5. `filter()`
6. `reduce()`
7. Difference Between `map()`, `filter()`, and `reduce()`
8. Real-World Examples
9. Method Chaining
10. Interview Questions
11. Summary

---

# What is a Higher-Order Function?

A **Higher-Order Function (HOF)** is a function that:

- Takes another function as an argument (callback), **or**
- Returns another function.

Many JavaScript array methods like **`map()`**, **`filter()`**, and **`reduce()`** are Higher-Order Functions because they accept a callback function.

Example

```javascript
const numbers = [10, 20, 30];

numbers.map(function (number) {
    return number * 2;
});
```

Here,

- `map()` is a Higher-Order Function.
- `function(number){...}` is a Callback Function.

---

# Why Do We Use Higher-Order Functions?

Higher-Order Functions help us:

- Write cleaner code
- Reduce code duplication
- Make code reusable
- Improve readability
- Process arrays easily

Instead of writing long `for` loops, we use methods like `map()`, `filter()`, and `reduce()`.

---

# Characteristics of Higher-Order Functions

- Accept another function as an argument.
- Return a new value or array.
- Do not usually modify the original array.
- Improve code readability.
- Used extensively in React and modern JavaScript.

---

# map()

## What is map()?

`map()` is used to transform every element of an array and returns a **new array**.

### Syntax

```javascript
array.map(function(currentValue, index, array){

    return newValue;

});
```

---

## Example 1

```javascript
const numbers = [10, 20, 30, 40];

const result = numbers.map(function(number){

    return number * 2;

});

console.log(result);
```

Output

```text
[20,40,60,80]
```

Original Array

```text
[10,20,30,40]
```

New Array

```text
[20,40,60,80]
```

---

## Example 2 (Objects)

```javascript
const students = [

    {
        id:1,
        name:"Durgesh",
        age:22
    },

    {
        id:2,
        name:"Rahul",
        age:23
    },

    {
        id:3,
        name:"Amit",
        age:21
    }

];

const names = students.map(student => student.name);

console.log(names);
```

Output

```text
[
"Durgesh",
"Rahul",
"Amit"
]
```

---

## Example 3 (Modify Objects)

```javascript
const employees = [

    {
        name:"Durgesh",
        salary:50000
    },

    {
        name:"Rahul",
        salary:30000
    }

];

const updatedEmployees = employees.map(employee => {

    return {

        ...employee,

        salary: employee.salary + 5000

    };

});

console.log(updatedEmployees);
```

Output

```javascript
[
{
name:"Durgesh",
salary:55000
},
{
name:"Rahul",
salary:35000
}
]
```

---

# filter()

## What is filter()?

`filter()` returns a **new array** containing only the elements that satisfy a condition.

### Syntax

```javascript
array.filter(function(currentValue){

    return condition;

});
```

---

## Example 1

```javascript
const numbers = [10,15,20,25,30];

const evenNumbers = numbers.filter(function(number){

    return number % 2 === 0;

});

console.log(evenNumbers);
```

Output

```text
[10,20,30]
```

---

## Example 2 (Objects)

```javascript
const students = [

    {
        name:"Durgesh",
        pass:true
    },

    {
        name:"Rahul",
        pass:false
    },

    {
        name:"Amit",
        pass:true
    }

];

const passedStudents = students.filter(student => student.pass);

console.log(passedStudents);
```

Output

```javascript
[
{
name:"Durgesh",
pass:true
},
{
name:"Amit",
pass:true
}
]
```

---

## Example 3 (Salary Filter)

```javascript
const employees = [

    {
        name:"Durgesh",
        salary:60000
    },

    {
        name:"Rahul",
        salary:25000
    },

    {
        name:"Amit",
        salary:70000
    }

];

const highSalary = employees.filter(employee => employee.salary > 50000);

console.log(highSalary);
```

Output

```javascript
[
{
name:"Durgesh",
salary:60000
},
{
name:"Amit",
salary:70000
}
]
```

---

# reduce()

## What is reduce()?

`reduce()` converts an entire array into a **single value**.

Used for

- Sum
- Average
- Maximum
- Minimum
- Shopping Cart Total
- Count Values

### Syntax

```javascript
array.reduce(function(accumulator,currentValue){

    return accumulator;

},initialValue);
```

---

## Example 1

```javascript
const numbers = [10,20,30];

const total = numbers.reduce(function(sum, number){

    return sum + number;

},0);

console.log(total);
```

Output

```text
60
```

---

## Step-by-Step

```
Initial Value = 0

0 + 10 = 10

10 + 20 = 30

30 + 30 = 60
```

Final Output

```text
60
```

---

## Example 2 (Shopping Cart)

```javascript
const cart = [

    {
        product:"Laptop",
        price:50000
    },

    {
        product:"Mouse",
        price:1000
    },

    {
        product:"Keyboard",
        price:2000
    }

];

const totalPrice = cart.reduce((total,item)=>{

    return total + item.price;

},0);

console.log(totalPrice);
```

Output

```text
53000
```

---

## Example 3 (Average)

```javascript
const marks = [80,90,70,60];

const total = marks.reduce((sum,mark)=>{

    return sum + mark;

},0);

const average = total / marks.length;

console.log(average);
```

Output

```text
75
```

---

# Difference Between map(), filter(), and reduce()

| Method | Returns | Purpose |
|----------|----------|---------|
| map() | New Array | Transform every element |
| filter() | New Array | Keep elements matching a condition |
| reduce() | Single Value | Convert array into one value |

---

# Real-World Examples

## map()

Extract product names

```javascript
const productNames = products.map(product => product.name);
```

---

## filter()

Get active users

```javascript
const activeUsers = users.filter(user => user.active);
```

---

## reduce()

Calculate shopping cart total

```javascript
const total = cart.reduce((sum,item)=>sum + item.price,0);
```

---

# Method Chaining

We can combine Higher-Order Functions together.

```javascript
const students = [

    {
        name:"Durgesh",
        marks:80
    },

    {
        name:"Rahul",
        marks:40
    },

    {
        name:"Amit",
        marks:90
    }

];

const result = students

.filter(student => student.marks >= 50)

.map(student => student.name)

console.log(result);
```

Output

```text
[
"Durgesh",
"Amit"
]
```

---

# Interview Questions

## Question 1

Which Higher-Order Function creates a new array?

**Answer**

```
map()
```

---

## Question 2

Which Higher-Order Function filters elements?

**Answer**

```
filter()
```

---

## Question 3

Which Higher-Order Function returns a single value?

**Answer**

```
reduce()
```

---

## Question 4

Can we chain `map()`, `filter()`, and `reduce()` together?

**Answer**

```
Yes
```

Example

```javascript
const result = numbers

.filter(number => number > 20)

.map(number => number * 2)

.reduce((sum,number)=>sum + number,0);
```

---

# Summary

- Higher-Order Functions accept another function as an argument.
- `map()` transforms every element and returns a new array.
- `filter()` returns only the elements that satisfy a condition.
- `reduce()` converts an array into a single value.
- All three methods are widely used in JavaScript, React, Node.js, and MERN Stack development.
- These methods can be combined using **Method Chaining** to write clean and efficient code.
