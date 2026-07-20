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
        name:"abcd",
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
"abcd",
"Rahul",
"Amit"
]
```

---

## Example 3 (Modify Objects)

```javascript
const employees = [

    {
        name:"abcd",
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
name:"abcd",
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
        name:"abcd",
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
name:"abcd",
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
        name:"abcd",
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
name:"abcd",
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
        name:"abcd",
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
"abcd",
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


# What is ES6?

**ES6 (ECMAScript 2015)** introduced many modern JavaScript features that make code shorter, cleaner, and easier to read.

Some popular ES6 features are:

- let and const
- Arrow Functions
- Template Literals
- Destructuring
- Rest Operator
- Spread Operator
- Default Parameters
- Classes
- Modules
- Promises

---

# What is Destructuring?

**Destructuring** is an ES6 feature that allows us to extract values from an **array** or **object** and store them directly into variables.

Instead of writing multiple lines of code, we can extract values in a single line.

---

## Without Destructuring

```javascript
const student = {
    name: "abcd",
    age: 22,
    city: "Lucknow"
};

const name = student.name;
const age = student.age;
const city = student.city;

console.log(name);
console.log(age);
console.log(city);
```

---

## With Destructuring

```javascript
const student = {
    name: "abcd",
    age: 22,
    city: "Lucknow"
};

const { name, age, city } = student;

console.log(name);
console.log(age);
console.log(city);
```

Output

```text
abcd
22
Lucknow
```

---

# Why Do We Use Destructuring?

- Less code
- Cleaner syntax
- Easy to read
- Faster access to values
- Commonly used in React and API responses

---

# Array Destructuring

```javascript
const numbers = [10, 20, 30];

const [a, b, c] = numbers;

console.log(a);
console.log(b);
console.log(c);
```

Output

```text
10
20
30
```

---

# Skip Values

```javascript
const numbers = [10,20,30,40];

const [first, , third] = numbers;

console.log(first);
console.log(third);
```

Output

```text
10
30
```

---

# Default Values

```javascript
const numbers = [10];

const [a, b = 100] = numbers;

console.log(a);
console.log(b);
```

Output

```text
10
100
```

---

# Object Destructuring

```javascript
const student = {
    name: "abcd",
    age: 22,
    city: "Lucknow"
};

const { name, age, city } = student;

console.log(name);
console.log(age);
console.log(city);
```

Output

```text
abcd
22
Lucknow
```

---

# Rename Variables

```javascript
const student = {
    name: "abcd",
    age: 22
};

const { name: studentName } = student;

console.log(studentName);
```

Output

```text
abcd
```

---

# Nested Object Destructuring

```javascript
const user = {

    id: 1,

    profile: {

        name: "abcd",

        city: "Lucknow"

    }

};

const {

    profile: {

        name,

        city

    }

} = user;

console.log(name);
console.log(city);
```

Output

```text
abcd
Lucknow
```

---

# Destructuring Function Parameters

```javascript
function printUser({ name, age }) {

    console.log(name);

    console.log(age);

}

const student = {

    name: "abcd",

    age: 22

};

printUser(student);
```

---

# What is Rest Operator?

The **Rest Operator (`...`)** collects multiple values into a single array or object.

Think of it as:

> **Collect the remaining values.**

---

# Rest Operator with Arrays

```javascript
const numbers = [10,20,30,40,50];

const [a, b, ...rest] = numbers;

console.log(a);
console.log(b);
console.log(rest);
```

Output

```text
10
20
[30,40,50]
```

---

# Visualization

```
[10,20,30,40,50]

↓

a = 10

b = 20

rest = [30,40,50]
```

---

# Rest Operator with Objects

```javascript
const student = {

    name: "abcd",

    age: 22,

    city: "Lucknow",

    country: "India"

};

const { name, ...details } = student;

console.log(details);
```

Output

```javascript
{
    age:22,
    city:"Lucknow",
    country:"India"
}
```

---

# Rest Operator in Functions

```javascript
function sum(...numbers){

    console.log(numbers);

}

sum(10,20,30,40,50);
```

Output

```text
[10,20,30,40,50]
```

---

# Sum Using Rest Operator

```javascript
function sum(...numbers){

    return numbers.reduce((total,number)=>total+number,0);

}

console.log(sum(10,20,30,40));
```

Output

```text
100
```

---

# What is Spread Operator?

The **Spread Operator (`...`)** expands an array or object into individual values.

Think of it as:

> **Expand all values.**

---

# Copy Array

```javascript
const numbers = [10,20,30];

const copy = [...numbers];

console.log(copy);
```

Output

```text
[10,20,30]
```

---

# Merge Arrays

```javascript
const arr1 = [10,20];

const arr2 = [30,40];

const result = [...arr1,...arr2];

console.log(result);
```

Output

```text
[10,20,30,40]
```

---

# Add New Values

```javascript
const numbers = [20,30];

const result = [10,...numbers,40];

console.log(result);
```

Output

```text
[10,20,30,40]
```

---

# Copy Object

```javascript
const student = {

    name: "abcd",

    age: 22

};

const copy = {

    ...student

};

console.log(copy);
```

Output

```javascript
{
    name:"abcd",
    age:22
}
```

---

# Merge Objects

```javascript
const student = {

    name:"abcd"

};

const address = {

    city:"Lucknow"

};

const user = {

    ...student,

    ...address

};

console.log(user);
```

Output

```javascript
{
    name:"abcd",
    city:"Lucknow"
}
```

---

# Override Object Properties

```javascript
const student = {

    name:"abcd",

    age:22

};

const updatedStudent = {

    ...student,

    age:25

};

console.log(updatedStudent);
```

Output

```javascript
{
    name:"abcd",
    age:25
}
```

---

# Rest vs Spread Operator

| Rest Operator | Spread Operator |
|--------------|----------------|
| Collects values | Expands values |
| Used on the left side of `=` | Used on the right side of `=` |
| Creates one array/object | Expands array/object |
| Used in function parameters | Used while copying or merging |

---

# Easy Trick to Remember

## Destructuring

```
Take values out
```

```
Object

↓

Variables
```

---

## Rest Operator

```
Collect remaining values
```

```
10

20

30

40

↓

rest

↓

[30,40]
```

---

## Spread Operator

```
Expand values
```

```
[10,20,30]

↓

10

20

30
```

---

# Real-World Examples

## Destructuring

- API Response
- React Props
- React State
- Function Parameters

---

## Rest Operator

- Unlimited Function Arguments
- Remaining Object Properties
- Remaining Array Values

---

## Spread Operator

- Copy Arrays
- Copy Objects
- Merge Arrays
- Merge Objects
- Update React State
- Clone Data

---


# JavaScript Exception Handling (try...catch)

## Table of Contents

1. Introduction to Exception Handling
2. What is try...catch?
3. Why Do We Use try...catch?
4. How try...catch Works
5. try Block
6. catch Block
7. Error Object
8. finally Block
9. throw Statement
10. Custom Errors
11. Real-World Examples
12. try...catch with async/await
13. Best Practices
14. Interview Questions
15. Summary

---

# Introduction to Exception Handling

In JavaScript, errors can occur while a program is running. These errors are called **Exceptions** or **Runtime Errors**.

If we don't handle these errors, the program may stop executing.

To avoid this problem, JavaScript provides **Exception Handling** using the `try...catch` statement.

---

# What is try...catch?

The `try...catch` statement is used to handle runtime errors in JavaScript.

Instead of crashing the application, JavaScript catches the error and allows the remaining code to continue executing.

In simple words:

> **try...catch allows your program to continue running even if an error occurs.**

---

# Why Do We Use try...catch?

We use `try...catch` because:

- Prevents application crashes
- Handles runtime errors
- Displays user-friendly error messages
- Continues program execution
- Helps in debugging
- Commonly used with APIs and databases

---

# How try...catch Works

```text
Program Starts

↓

try Block Executes

↓

Error Found?

↓

No
↓

Continue Program

OR

Yes
↓

catch Block Executes

↓

Continue Program

↓

finally Block (if available)
```

---

# Syntax

```javascript
try {

    // Code that may produce an error

}
catch(error){

    // Handle the error

}
```

---

# try Block

The `try` block contains code that may throw an error.

If no error occurs, the `catch` block is skipped.

Example

```javascript
try{

    console.log("Hello World");

}
catch(error){

    console.log(error);

}
```

Output

```text
Hello World
```

---

# Example with Error

```javascript
try{

    console.log(user);

}
catch(error){

    console.log("Error Found");

}
```

Output

```text
Error Found
```

---

# Without try...catch

```javascript
console.log("Program Started");

console.log(user);

console.log("Program Finished");
```

Output

```text
Program Started

ReferenceError: user is not defined
```

The program stops immediately.

---

# With try...catch

```javascript
console.log("Program Started");

try{

    console.log(user);

}
catch(error){

    console.log("User variable not found.");

}

console.log("Program Finished");
```

Output

```text
Program Started

User variable not found.

Program Finished
```

The program continues executing.

---

# catch Block

The `catch` block executes only if an error occurs inside the `try` block.

Syntax

```javascript
catch(error){

}
```

The `error` parameter contains complete information about the error.

---

# Error Object

JavaScript automatically creates an **Error Object**.

Example

```javascript
try{

    console.log(data);

}
catch(error){

    console.log(error);

}
```

---

# error.message

Returns the error message.

```javascript
try{

    console.log(data);

}
catch(error){

    console.log(error.message);

}
```

Output

```text
data is not defined
```

---

# error.name

Returns the type of error.

```javascript
try{

    console.log(data);

}
catch(error){

    console.log(error.name);

}
```

Output

```text
ReferenceError
```

---

# error.stack

Returns the complete stack trace.

```javascript
try{

    console.log(data);

}
catch(error){

    console.log(error.stack);

}
```

---

# finally Block

The `finally` block always executes whether an error occurs or not.

Syntax

```javascript
try{

}
catch(error){

}
finally{

}
```

---

# Example

```javascript
try{

    console.log("Database Connected");

}
catch(error){

    console.log(error);

}
finally{

    console.log("Database Connection Closed");

}
```

Output

```text
Database Connected

Database Connection Closed
```

---

# Example with Error

```javascript
try{

    console.log(user);

}
catch(error){

    console.log(error.message);

}
finally{

    console.log("Execution Completed");

}
```

Output

```text
user is not defined

Execution Completed
```

---

# throw Statement

The `throw` statement is used to create custom errors.

Syntax

```javascript
throw new Error("Message");
```

---

# Example

```javascript
try{

    let age = 15;

    if(age < 18){

        throw new Error("Age must be 18 or above.");

    }

    console.log("Eligible");

}
catch(error){

    console.log(error.message);

}
```

Output

```text
Age must be 18 or above.
```

---

# Example: Division by Zero

```javascript
function divide(a,b){

    try{

        if(b===0){

            throw new Error("Cannot divide by zero.");

        }

        console.log(a/b);

    }
    catch(error){

        console.log(error.message);

    }

}

divide(20,0);
```

Output

```text
Cannot divide by zero.
```

---

# Example: JSON Parsing

```javascript
try{

    const user = JSON.parse('{"name":"abcd"}');

    console.log(user);

}
catch(error){

    console.log("Invalid JSON");

}
```

Output

```javascript
{
    name: "abcd"
}
```

---

# Example: Invalid JSON

```javascript
try{

    JSON.parse("{name:'abcd'}");

}
catch(error){

    console.log("Invalid JSON Format");

}
```

Output

```text
Invalid JSON Format
```

---

# Real-World Example: Login Validation

```javascript
function login(username,password){

    try{

        if(username===""){

            throw new Error("Username is required.");

        }

        if(password===""){

            throw new Error("Password is required.");

        }

        console.log("Login Successful");

    }
    catch(error){

        console.log(error.message);

    }

}

login("","123456");
```

Output

```text
Username is required.
```

---

# try...catch with async/await

One of the most common uses of `try...catch` is with `async/await`.

```javascript
async function getUsers(){

    try{

        const response = await fetch("https://jsonplaceholder.typicode.com/users");

        const data = await response.json();

        console.log(data);

    }
    catch(error){

        console.log(error.message);

    }

}
```

---

# Best Practices

- Use `try...catch` only for code that may throw errors.
- Do not leave the `catch` block empty.
- Display meaningful error messages.
- Use `finally` for cleanup operations.
- Use `throw` to create custom errors.
- Combine `try...catch` with `async/await` for API calls.

---

# Difference Between try, catch, finally, and throw

| Keyword | Purpose |
|----------|---------|
| `try` | Contains code that may throw an error |
| `catch` | Handles the error |
| `finally` | Executes whether an error occurs or not |
| `throw` | Creates a custom error |

---

# Real-World Uses

`try...catch` is used in:

- API Calls
- Fetch API
- Axios
- Database Operations
- File Reading
- JSON Parsing
- Payment Processing
- User Authentication
- Form Validation
- Cloud Services


----



# JavaScript Synchronous Programming, Asynchronous Programming, Async & Await

## Table of Contents

1. Introduction
2. What is Synchronous Programming?
3. Characteristics of Synchronous Programming
4. How Synchronous Programming Works
5. Real-Life Example
6. Synchronous Programming Example
7. What is Asynchronous Programming?
8. Characteristics of Asynchronous Programming
9. How Asynchronous Programming Works
10. Real-Life Example
11. Asynchronous Programming Example
12. Difference Between Synchronous and Asynchronous
13. What is `async`?
14. What is `await`?
15. Why Do We Need `async/await`?
16. Promise vs Async/Await
17. Using `async` and `await`
18. Multiple `await` Example
19. `async/await` with `try...catch`
20. Real-World Uses
21. Best Practices
22. Interview Questions
23. Summary

---

# Introduction

JavaScript is a **single-threaded programming language**, meaning it executes one instruction at a time.

However, many operations take time to complete, such as:

- API Calls
- Database Queries
- File Uploads
- File Downloads
- Payment Processing
- Reading Files
- Sending Emails
- Timers

If JavaScript waited for every long-running operation to finish, applications would become slow and unresponsive.

To solve this problem, JavaScript supports **Asynchronous Programming**.

Before learning asynchronous programming, let's first understand synchronous programming.

---

# What is Synchronous Programming?

**Synchronous Programming** means JavaScript executes code **one statement at a time**, in the exact order it is written.

The next statement will not execute until the current statement finishes.

## Simple Definition

> **Synchronous Programming executes one task after another.**

---

# Characteristics of Synchronous Programming

- Executes line by line
- One task at a time
- Blocking execution
- Easy to understand
- Waits until the current task finishes

---

# How Synchronous Programming Works

```text
Task 1

↓

Task 2

↓

Task 3

↓

Task 4
```

Each task waits for the previous task to complete.

---

# Example

```javascript
console.log("Task 1");

console.log("Task 2");

console.log("Task 3");
```

### Output

```text
Task 1

Task 2

Task 3
```

---

# Real-Life Example

Imagine standing in a bank queue.

```text
Customer 1

↓

Customer 2

↓

Customer 3

↓

Customer 4
```

Customer 2 must wait until Customer 1 finishes.

This is **Synchronous Programming**.

---

# Problem with Synchronous Programming

Imagine downloading a large file.

```javascript
console.log("Download Started");

// Download takes 10 seconds

console.log("Download Completed");
```

The program waits until the download finishes.

During this time, nothing else executes.

This is called **Blocking Execution**.

---

# What is Asynchronous Programming?

**Asynchronous Programming** allows JavaScript to start a long-running task and continue executing the remaining code without waiting.

## Simple Definition

> **Asynchronous Programming allows long-running tasks to execute without blocking other code.**

---

# Characteristics of Asynchronous Programming

- Non-blocking
- Faster
- Better user experience
- Used for APIs
- Used for databases
- Used for timers
- Used for file operations

---

# How Asynchronous Programming Works

```text
Start

↓

Long Running Task Started

↓

Continue Other Work

↓

Long Running Task Completed
```

---

# Example

```javascript
console.log("Start");

setTimeout(() => {

    console.log("Task Completed");

}, 2000);

console.log("End");
```

### Output

```text
Start

End

Task Completed
```

---

# Explanation

1. `"Start"` is printed.
2. `setTimeout()` starts.
3. JavaScript does **not** wait.
4. `"End"` is printed.
5. After 2 seconds, `"Task Completed"` is printed.

---

# Real-Life Example

Imagine ordering food online.

```text
Order Pizza

↓

Restaurant Starts Cooking

↓

Watch TV

↓

Pizza Delivered
```

You don't wait in the kitchen.

This is **Asynchronous Programming**.

---

# Difference Between Synchronous and Asynchronous

| Synchronous | Asynchronous |
|-------------|--------------|
| Executes line by line | Executes without blocking |
| Waits for each task | Doesn't wait |
| Blocking | Non-blocking |
| Slower for long tasks | Better performance |
| One task at a time | Multiple operations can overlap |

---

# What is `async`?

The `async` keyword is used before a function to make it asynchronous.

An `async` function **always returns a Promise**.

## Syntax

```javascript
async function functionName(){

}
```

---

# Example

```javascript
async function greet(){

    return "Hello JavaScript";

}

greet().then(console.log);
```

### Output

```text
Hello JavaScript
```

Even though the function returns a string, JavaScript automatically converts it into a Promise.

---

# What is `await`?

The `await` keyword waits for a Promise to complete before continuing execution inside an `async` function.

## Syntax

```javascript
const result = await promise;
```

### Important Points

- Works only with Promises
- Used inside an `async` function
- Makes asynchronous code easier to read

---

# Why Do We Need `async/await`?

Before `async/await`, JavaScript mainly used Promise chaining.

Example:

```javascript
login()

.then(getProfile)

.then(getOrders)

.then(getPayments)

.catch(console.log);
```

When there are many asynchronous operations, chaining becomes difficult to read.

`async/await` makes the same code look like normal synchronous code.

---

# Promise Example

```javascript
function fetchData(){

    return new Promise((resolve)=>{

        setTimeout(()=>{

            resolve("Data Loaded");

        },2000);

    });

}

fetchData()

.then(data=>{

    console.log(data);

});
```

### Output

```text
Data Loaded
```

---

# Same Example Using Async/Await

```javascript
function fetchData(){

    return new Promise((resolve)=>{

        setTimeout(()=>{

            resolve("Data Loaded");

        },2000);

    });

}

async function getData(){

    const result = await fetchData();

    console.log(result);

}

getData();
```

### Output

```text
Data Loaded
```

---

# Step-by-Step Execution

```text
Call getData()

↓

fetchData() Returns Promise

↓

await Waits

↓

Promise Resolved

↓

Store Result

↓

Print Result
```

---

# Multiple `await` Example

```javascript
function getUser(){

    return Promise.resolve("abcd");

}

function getCourse(){

    return Promise.resolve("JavaScript");

}

async function showDetails(){

    const user = await getUser();

    const course = await getCourse();

    console.log(user);

    console.log(course);

}

showDetails();
```

### Output

```text
abcd

JavaScript
```

---

# Async/Await with `try...catch`

This is the most common way to handle errors.

```javascript
async function getUsers(){

    try{

        const response = await fetch("https://jsonplaceholder.typicode.com/users");

        const users = await response.json();

        console.log(users);

    }

    catch(error){

        console.log(error.message);

    }

}
```

---

# Promise vs Async/Await

| Promise | Async/Await |
|----------|-------------|
| Uses `.then()` | Uses `await` |
| Can become difficult to read | Looks like synchronous code |
| Better for simple chains | Better for complex operations |
| Uses `.catch()` | Uses `try...catch` |

---

# Real-World Uses

`async` and `await` are widely used for:

- Fetch API
- Axios
- Database Queries
- Login Systems
- Payment Gateway
- Cloud Storage
- Authentication
- Reading Files
- Uploading Images
- Sending Emails

---

**Answer**

- API Calls
- Fetch API
- Axios
- Database Operations
- Authentication
- Payment Systems
- File Uploads
- Cloud Services

---

# Summary

- JavaScript supports both **Synchronous** and **Asynchronous** programming.
- **Synchronous Programming** executes one task at a time and waits for each task to finish.
- **Asynchronous Programming** allows long-running tasks to execute without blocking other code.
- The `async` keyword makes a function asynchronous and automatically returns a Promise.
- The `await` keyword waits for a Promise to settle before continuing execution inside an `async` function.
- `async/await` provides a cleaner and more readable way to write asynchronous code than Promise chaining.
- Use `try...catch` with `async/await` for proper error handling.
- `async/await` is widely used in modern JavaScript, React, Node.js, Express.js, and MERN Stack applications.

---








---


# JavaScript Promises


# Introduction to Promises

Promises are one of the most important concepts in modern JavaScript.

A Promise is used to handle **asynchronous operations**, such as:

- API Calls
- Database Queries
- Authentication
- File Uploads
- File Downloads
- Payment Processing
- Sending Emails
- Reading Files
- Timers (`setTimeout`)
- Loading Data from a Server

Promises make asynchronous code easier to read, write, and maintain.

---

# What is a Promise?

A **Promise** is an object that represents the **eventual completion (success)** or **failure** of an asynchronous operation.

In simple words:

> **A Promise is a guarantee that "I will give you the result later."**

A Promise doesn't immediately return the final result. Instead, it returns a Promise object, and JavaScript notifies us when the operation is completed.

---

# Why Do We Need Promises?

Before Promises, asynchronous operations were handled using callbacks.

When multiple callbacks were nested together, the code became difficult to read and maintain. This problem is known as **Callback Hell**.

Promises solve this problem by providing a cleaner and more readable way to handle asynchronous operations.

Benefits of Promises:

- Cleaner code
- Better error handling
- Easier to read
- Supports chaining
- Avoids Callback Hell
- Widely used with APIs and databases

---

# Real-Life Example

Imagine you order a pizza online.

```text
Place Order

↓

Restaurant Starts Preparing

↓

Pizza Delivered
```

There are three possible situations.

### 1. Waiting

```text
Pending
```

Your order is being prepared.

---

### 2. Delivered Successfully

```text
Fulfilled
```

You receive your pizza successfully.

---

### 3. Order Failed

```text
Rejected
```

Something went wrong with your order.

This is exactly how JavaScript Promises work.

---

# Promise States

Every Promise has **three states**.

```text
Promise

↓

Pending

↓

Fulfilled (Resolved)

OR

Rejected
```

---

## 1. Pending

The operation has started but has not finished yet.

Examples

- Loading...
- Request Sent...
- Waiting for Response...

---

## 2. Fulfilled (Resolved)

The operation completed successfully.

Examples

- Login Successful
- Data Received
- Payment Successful

---

## 3. Rejected

The operation failed.

Examples

- Network Error
- Login Failed
- Payment Failed

---

# Creating a Promise

A Promise is created using the `Promise` constructor.

## Syntax

```javascript
const promise = new Promise((resolve, reject) => {

    // Asynchronous operation

});
```

The constructor receives a callback function with two parameters:

- `resolve()` → Called when the operation succeeds.
- `reject()` → Called when the operation fails.

---

# Example 1 - Promise Resolved

```javascript
const promise = new Promise((resolve, reject) => {

    resolve("Promise Completed Successfully");

});

console.log(promise);
```

Output

```text
Promise { fulfilled }
```

---

# Example 2 - Promise Rejected

```javascript
const promise = new Promise((resolve, reject) => {

    reject("Something Went Wrong");

});

console.log(promise);
```

Output

```text
Promise { rejected }
```

---

# Understanding resolve()

`resolve()` is called when the asynchronous operation completes successfully.

```javascript
const promise = new Promise((resolve, reject) => {

    resolve("Data Loaded Successfully");

});
```

---

# Understanding reject()

`reject()` is called when the operation fails.

```javascript
const promise = new Promise((resolve, reject) => {

    reject("Unable to Load Data");

});
```

---

# Using .then()

The `.then()` method executes when the Promise is resolved successfully.

## Syntax

```javascript
promise.then(function(result){

});
```

---

## Example

```javascript
const promise = new Promise((resolve) => {

    resolve("Login Successful");

});

promise.then(function(result){

    console.log(result);

});
```

Output

```text
Login Successful
```

---

# Using .catch()

The `.catch()` method executes when the Promise is rejected.

## Syntax

```javascript
promise.catch(function(error){

});
```

---

## Example

```javascript
const promise = new Promise((resolve, reject) => {

    reject("Invalid Username or Password");

});

promise.catch(function(error){

    console.log(error);

});
```

Output

```text
Invalid Username or Password
```

---

# Using .finally()

The `.finally()` method always executes, whether the Promise is resolved or rejected.

## Example

```javascript
const promise = new Promise((resolve) => {

    resolve("Payment Successful");

});

promise

.then(result => {

    console.log(result);

})

.finally(() => {

    console.log("Transaction Completed");

});
```

Output

```text
Payment Successful

Transaction Completed
```

---

# Example Using setTimeout()

```javascript
const promise = new Promise((resolve) => {

    setTimeout(() => {

        resolve("Data Loaded");

    }, 3000);

});

promise.then(result => {

    console.log(result);

});
```

Output (after 3 seconds)

```text
Data Loaded
```

---

# Promise Chaining

Multiple `.then()` methods can be chained together.

```javascript
Promise.resolve(10)

.then(number => number * 2)

.then(number => number + 5)

.then(number => number * 10)

.then(result => {

    console.log(result);

});
```

Output

```text
250
```

---

# Real-World Example 1 - User Login

```javascript
function login(){

    return new Promise((resolve, reject) => {

        const success = true;

        if(success){

            resolve("Login Successful");

        }else{

            reject("Login Failed");

        }

    });

}

login()

.then(result => {

    console.log(result);

})

.catch(error => {

    console.log(error);

});
```

Output

```text
Login Successful
```

---

# Real-World Example 2 - Food Delivery

```javascript
function orderFood(){

    return new Promise((resolve) => {

        setTimeout(() => {

            resolve("Pizza Delivered");

        }, 2000);

    });

}

orderFood()

.then(result => {

    console.log(result);

});
```

Output

```text
Pizza Delivered
```

---

# Promise Flow

```text
Create Promise

↓

Pending

↓

Success?

↓

Yes ─────────► .then()

↓

No ─────────► .catch()

↓

.finally()
```

---

# Promise.resolve()

Creates a Promise that is already resolved.

```javascript
Promise.resolve("Success")

.then(console.log);
```

Output

```text
Success
```

---

# Promise.reject()

Creates a Promise that is already rejected.

```javascript
Promise.reject("Failed")

.catch(console.log);
```

Output

```text
Failed
```

---

# Promise vs Callback

| Callback | Promise |
|----------|----------|
| Difficult to Read | Easy to Read |
| Nested Code | Cleaner Code |
| Callback Hell | Promise Chaining |
| Hard Error Handling | Better Error Handling |
| Less Maintainable | More Maintainable |

---

# Real-World Uses of Promises

Promises are used in:

- Fetch API
- Axios API Calls
- Database Queries
- User Login
- Payment Gateways
- Cloud Storage
- Authentication
- File Upload
- File Download
- Reading Files
- Notifications
- Sending Emails

---

# Best Practices

- Always handle errors using `.catch()`.
- Use `.finally()` for cleanup tasks.
- Avoid deeply nested Promise chains.
- Prefer `async/await` for complex asynchronous code.
- Return Promises instead of nesting them.

---

# Interview Questions

### Question 1

What is a Promise?

**Answer**

A Promise is an object that represents the eventual success or failure of an asynchronous operation.

---

### Question 2

How many states does a Promise have?

**Answer**

- Pending
- Fulfilled (Resolved)
- Rejected

---

### Question 3

What is `resolve()`?

**Answer**

`resolve()` is called when the asynchronous operation completes successfully.

---

### Question 4

What is `reject()`?

**Answer**

`reject()` is called when the asynchronous operation fails.

---

### Question 5

What is `.then()`?

**Answer**

Used to handle successful Promise results.

---

### Question 6

What is `.catch()`?

**Answer**

Used to handle errors in a Promise.

---

### Question 7

What is `.finally()`?

**Answer**

Executes after the Promise settles, whether it succeeds or fails.

---

### Question 8

What is Promise Chaining?

**Answer**

Executing multiple asynchronous operations sequentially using multiple `.then()` methods.

---

### Question 9

What is the difference between Callback and Promise?

**Answer**

Promises provide cleaner syntax, better error handling, and avoid Callback Hell.

---

### Question 10

Where are Promises used?

**Answer**

Promises are commonly used with APIs, databases, authentication, payment systems, file handling, and asynchronous JavaScript operations.

---

# Summary

- A **Promise** is used to handle asynchronous operations.
- Every Promise has **three states**:
  - Pending
  - Fulfilled (Resolved)
  - Rejected
- `resolve()` indicates success.
- `reject()` indicates failure.
- `.then()` handles successful results.
- `.catch()` handles errors.
- `.finally()` always executes after the Promise settles.
- Promises make asynchronous code cleaner, more readable, and easier to maintain.
- Promises are widely used in **React**, **Node.js**, **Express.js**, and modern JavaScript applications.

# 📘 JavaScript Fetch API

> Complete Notes for Beginners to Advanced

---

# Table of Contents

* What is an API?
* What is Fetch API?
* Why Do We Use Fetch API?
* How Fetch Works
* Fetch Syntax
* Promise and Fetch
* HTTP Methods
* GET Request
* POST Request
* PUT Request
* PATCH Request
* DELETE Request
* Request Headers
* Request Body
* Response Object
* `response.json()`
* `JSON.stringify()`
* HTTP Status Codes
* Error Handling
* Fetch with Async/Await
* Fetch Workflow
* Fetch vs Axios
* Fetch vs XMLHttpRequest
* Advantages of Fetch
* Limitations of Fetch
* Best Practices
* Interview Questions
* Summary

---

# What is an API?

API stands for **Application Programming Interface**.

An API acts as a bridge between two applications, allowing them to exchange data.

### Example

Suppose you have a weather application.

```text
Weather App
      │
      ▼
 Weather API
      │
      ▼
 Weather Database
      │
      ▼
 Weather Information
```

The application requests weather information from the API, and the API returns the response.

---

# What is Fetch API?

The **Fetch API** is a built-in JavaScript function used to send HTTP requests to a server and receive HTTP responses.

It is the modern way of communicating with REST APIs.

Fetch always returns a **Promise**, so it works with:

* `.then()`
* `.catch()`
* `async/await`

---

# Why Do We Use Fetch API?

We use Fetch whenever our application needs to communicate with a backend server.

Common examples include:

* User Login
* User Registration
* Product Listing
* Dashboard
* Payment Gateway
* Upload Images
* Update Profile
* Delete Records
* Chat Applications
* Weather Applications

Without Fetch, the browser cannot request or send data to the server.

---

# How Fetch Works

```text
Browser

↓

fetch()

↓

HTTP Request

↓

Server

↓

Database

↓

Response

↓

Browser

↓

Display Data
```

---

# Fetch Syntax

```javascript
fetch(url);
```

Example

```javascript
fetch("https://jsonplaceholder.typicode.com/users");
```

---

# Fetch Returns a Promise

Every Fetch request returns a Promise.

```text
fetch()

↓

Promise

↓

Response Object

↓

JavaScript Object
```

---

# HTTP Methods

| Method | Purpose                |
| ------ | ---------------------- |
| GET    | Retrieve data          |
| POST   | Create new data        |
| PUT    | Replace existing data  |
| PATCH  | Update specific fields |
| DELETE | Remove data            |

---

# GET Request

Used to retrieve data from the server.

```javascript
fetch("https://jsonplaceholder.typicode.com/users")
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.log(error));
```

---

# POST Request

Used to create new data.

```javascript
fetch("https://jsonplaceholder.typicode.com/posts", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        title: "JavaScript",
        body: "Fetch API",
        userId: 1
    })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.log(error));
```

---

# PUT Request

Used to replace an existing resource.

```javascript
fetch(url, {
    method: "PUT",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        name: "Durgesh",
        city: "Lucknow"
    })
});
```

---

# PATCH Request

Used to update only selected fields.

```javascript
fetch(url, {
    method: "PATCH",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        city: "Delhi"
    })
});
```

---

# DELETE Request

Used to remove data.

```javascript
fetch(url, {
    method: "DELETE"
});
```

---

# Request Headers

Headers provide additional information to the server.

Example

```javascript
headers: {
    "Content-Type": "application/json"
}
```

Common headers:

* Content-Type
* Authorization
* Accept
* Cookie

---

# Request Body

The request body contains the data sent to the server.

```javascript
body: JSON.stringify({
    email: "student@gmail.com",
    password: "123456"
})
```

---

# Response Object

The Fetch API returns a **Response** object.

Useful properties:

* `response.ok`
* `response.status`
* `response.headers`
* `response.url`
* `response.type`

Example

```javascript
fetch(url)
.then(response => {
    console.log(response);
});
```

---

# Why Do We Use `response.json()`?

Servers usually send data in JSON format.

Example JSON

```json
{
    "id": 1,
    "name": "Durgesh",
    "city": "Lucknow"
}
```

`response.json()` converts the JSON response into a JavaScript object.

```javascript
fetch(url)
.then(response => response.json())
.then(data => console.log(data));
```

---

# Why Do We Use `JSON.stringify()`?

JavaScript objects cannot be sent directly to the server.

We convert them into JSON strings.

```javascript
const user = {
    name: "Durgesh",
    city: "Lucknow"
};

const jsonData = JSON.stringify(user);

console.log(jsonData);
```

Output

```text
{"name":"Durgesh","city":"Lucknow"}
```

---

# HTTP Status Codes

| Code | Meaning               |
| ---- | --------------------- |
| 200  | Success               |
| 201  | Created               |
| 204  | No Content            |
| 400  | Bad Request           |
| 401  | Unauthorized          |
| 403  | Forbidden             |
| 404  | Not Found             |
| 500  | Internal Server Error |

---

# Error Handling

Always check whether the request was successful.

```javascript
fetch(url)
.then(response => {

    if (!response.ok) {
        throw new Error("Request Failed");
    }

    return response.json();

})
.then(data => console.log(data))
.catch(error => console.log(error.message));
```

---

# Fetch with Async/Await

```javascript
async function getUsers() {

    try {

        const response = await fetch("https://jsonplaceholder.typicode.com/users");

        const data = await response.json();

        console.log(data);

    } catch (error) {

        console.log(error);

    }

}

getUsers();
```

---

# Fetch Workflow

```text
User Click

↓

fetch()

↓

HTTP Request

↓

Server

↓

Database

↓

Response

↓

response.json()

↓

JavaScript Object

↓

Display Data
```

---

# Fetch vs Axios

| Fetch API                  | Axios                     |
| -------------------------- | ------------------------- |
| Built into browser         | External library          |
| No installation            | Install with npm          |
| Requires `response.json()` | Automatically parses JSON |
| Lightweight                | More features             |

---

# Fetch vs XMLHttpRequest

| Fetch                | XMLHttpRequest                        |
| -------------------- | ------------------------------------- |
| Promise-based        | Callback-based                        |
| Cleaner syntax       | More verbose                          |
| Supports async/await | Does not directly support async/await |
| Modern               | Older API                             |

---

