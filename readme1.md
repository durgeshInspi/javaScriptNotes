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


# JavaScript Operators

Operators are special symbols or keywords used to perform operations on variables and values.

Example:

```javascript
let a = 10;
let b = 5;

let result = a + b;

console.log(result);
```

Output:

```
15
```

JavaScript provides different types of operators:

1. Arithmetic Operators
2. Assignment Operators
3. Comparison Operators
4. Logical Operators
5. Unary Operators
6. Ternary Operator
7. Bitwise Operators
8. String Operators
9. Type Operators
10. Optional Chaining Operator

---

# 1. Arithmetic Operators

Arithmetic operators are used to perform mathematical calculations.

| Operator | Name | Example |
|----------|------|---------|
| + | Addition | a + b |
| - | Subtraction | a - b |
| * | Multiplication | a * b |
| / | Division | a / b |
| % | Modulus | a % b |
| ** | Exponentiation | a ** b |
| ++ | Increment | a++ |
| -- | Decrement | a-- |

---

## Addition Operator (+)

The addition operator adds two values.

Example:

```javascript
let a = 20;
let b = 10;

console.log(a + b);
```

Output:

```
30
```

---

## Subtraction Operator (-)

The subtraction operator subtracts one value from another.

Example:

```javascript
let a = 20;
let b = 10;

console.log(a - b);
```

Output:

```
10
```

---

## Multiplication Operator (*)

The multiplication operator multiplies two values.

Example:

```javascript
let price = 100;
let quantity = 5;

console.log(price * quantity);
```

Output:

```
500
```

---

## Division Operator (/)

The division operator divides one value by another.

Example:

```javascript
let total = 100;
let number = 5;

console.log(total / number);
```

Output:

```
20
```

---

## Modulus Operator (%)

The modulus operator returns the remainder after division.

Example:

```javascript
let number = 10;

console.log(number % 3);
```

Output:

```
1
```

---

## Exponentiation Operator (**)

The exponentiation operator is used to calculate power.

Example:

```javascript
let result = 2 ** 3;

console.log(result);
```

Output:

```
8
```

---

## Increment Operator (++)

The increment operator increases a value by 1.

Example:

```javascript
let count = 5;

count++;

console.log(count);
```

Output:

```
6
```

---

## Decrement Operator (--)

The decrement operator decreases a value by 1.

Example:

```javascript
let count = 5;

count--;

console.log(count);
```

Output:

```
4
```

---

# 2. Assignment Operators

Assignment operators are used to assign values to variables.

| Operator | Description |
|----------|-------------|
| = | Assign value |
| += | Add and assign |
| -= | Subtract and assign |
| *= | Multiply and assign |
| /= | Divide and assign |
| %= | Modulus and assign |

---

## Assignment (=)

Example:

```javascript
let name = "JavaScript";

console.log(name);
```

Output:

```
JavaScript
```

---

## Add Assignment (+=)

Example:

```javascript
let value = 10;

value += 5;

console.log(value);
```

Output:

```
15
```

---

## Subtract Assignment (-=)

Example:

```javascript
let value = 20;

value -= 5;

console.log(value);
```

Output:

```
15
```

---

## Multiply Assignment (*=)

Example:

```javascript
let value = 5;

value *= 3;

console.log(value);
```

Output:

```
15
```

---

# 3. Comparison Operators

Comparison operators compare two values and return either:

- true
- false


| Operator | Description |
|----------|-------------|
| == | Equal to |
| === | Strict equal |
| != | Not equal |
| !== | Strict not equal |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal |
| <= | Less than or equal |

---

## Equal Operator (==)

Checks only value.

Example:

```javascript
console.log(10 == "10");
```

Output:

```
true
```

---

## Strict Equal Operator (===)

Checks value and data type.

Example:

```javascript
console.log(10 === "10");
```

Output:

```
false
```

---

## Not Equal Operator (!=)

Example:

```javascript
console.log(10 != 5);
```

Output:

```
true
```

---

## Greater Than (>)

Example:

```javascript
console.log(20 > 10);
```

Output:

```
true
```

---

## Less Than (<)

Example:

```javascript
console.log(5 < 10);
```

Output:

```
true
```

---

# 4. Logical Operators

Logical operators are used to combine multiple conditions.

| Operator | Name |
|----------|------|
| && | AND |
| || | OR |
| ! | NOT |

---

## AND Operator (&&)

Returns true when all conditions are true.

Example:

```javascript
let age = 25;

console.log(age >= 18 && age <= 30);
```

Output:

```
true
```

---

## OR Operator (||)

Returns true when at least one condition is true.

Example:

```javascript
let marks = 80;

console.log(marks > 90 || marks > 70);
```

Output:

```
true
```

---

## NOT Operator (!)

Reverses the boolean value.

Example:

```javascript
let login = false;

console.log(!login);
```

Output:

```
true
```

---

# 5. Unary Operators

Unary operators work with only one operand.

Examples:

- typeof
- delete
- increment
- decrement


---

## typeof Operator

The typeof operator returns the data type.

Example:

```javascript
let value = 100;

console.log(typeof value);
```

Output:

```
number
```

Example:

```javascript
let name = "John";

console.log(typeof name);
```

Output:

```
string
```

---

## delete Operator

The delete operator removes properties from objects.

Example:

```javascript
let user = {
    name: "John",
    age: 25
};

delete user.age;

console.log(user);
```

Output:

```
{name: "John"}
```

---

# 6. Ternary Operator

The ternary operator is a short form of if-else statement.

Syntax:

```javascript
condition ? trueValue : falseValue;
```

Example:

```javascript
let age = 18;

let result = age >= 18 ? "Adult" : "Minor";

console.log(result);
```

Output:

```
Adult
```

---

# 7. Bitwise Operators

Bitwise operators work with binary numbers.

| Operator | Name |
|----------|------|
| & | AND |
| | | OR |
| ^ | XOR |
| ~ | NOT |
| << | Left Shift |
| >> | Right Shift |

Example:

```javascript
let a = 5;
let b = 1;

console.log(a & b);
```

Output:

```
1
```

---

# 8. String Operators

The + operator is also used to join strings.

Example:

```javascript
let firstName = "John";
let lastName = "Smith";

console.log(firstName + " " + lastName);
```

Output:

```
John Smith
```

---

# 9. Type Operators

JavaScript provides operators to check data types.

## typeof Operator

Example:

```javascript
console.log(typeof "Hello");
```

Output:

```
string
```

---

## instanceof Operator

The instanceof operator checks whether an object belongs to a specific type.

Example:

```javascript
let numbers = [1,2,3];

console.log(numbers instanceof Array);
```

Output:

```
true
```

---

# 10. Optional Chaining Operator (?.)

Optional chaining allows safe access to object properties.

Example:

```javascript
let user = {
    profile:{
        name:"Alex"
    }
};

console.log(user.profile?.name);
```

Output:

```
Alex
```

If the property does not exist:

```javascript
console.log(user.address?.city);
```

Output:

```
undefined
```

---

# Operator Precedence

Operator precedence decides the order in which operations are performed.

Example:

```javascript
let result = 10 + 5 * 2;

console.log(result);
```

Output:

```
20
```

Explanation:

```
5 * 2 = 10

10 + 10 = 20
```

Multiplication has higher priority than addition.

---

# 📘 JavaScript Notes - Condition Statements

> **Module:** JavaScript Fundamentals  
> **Topic:** Conditional Statements  
> **Level:** Beginner to Intermediate

---

# 📖 What is a Conditional Statement?

A **Conditional Statement** is used to make decisions in a JavaScript program.

It allows the program to execute different blocks of code depending on whether a condition is **true** or **false**.

### Real-Life Example

Imagine you are logging into a website.

- If the username and password are correct → Login Successfully ✅
- Otherwise → Show "Invalid Credentials" ❌

This is called **Decision Making**.

---

# Why do we use Conditional Statements?

Conditional statements help us:

- Make decisions
- Control program flow
- Execute different code based on conditions
- Validate user input
- Handle different scenarios

---

# Flow of Condition Statement

```

Start
|
Check Condition
|
True? ---------------- No
| |
Execute Code Execute Other Code
|
End

```

---

# Types of Conditional Statements

JavaScript provides the following conditional statements:

1. if Statement
2. if...else Statement
3. else if Statement
4. Nested if Statement
5. switch Statement
6. Ternary Operator (Short-hand if...else)

---

# 1. if Statement

The `if` statement executes code only when the condition is true.

## Syntax

```javascript
if (condition) {
    // code
}
```

## Example 1

```javascript
let age = 20;

if (age >= 18) {
    console.log("You can vote.");
}
```

### Output

```
You can vote.
```

---

## Example 2

```javascript
let marks = 90;

if (marks >= 35) {
    console.log("Pass");
}
```

Output

```
Pass
```

---

## Example 3

```javascript
let isLoggedIn = true;

if (isLoggedIn) {
    console.log("Welcome User");
}
```

Output

```
Welcome User
```

---

# 2. if...else Statement

If the condition is true, the `if` block runs.

Otherwise, the `else` block runs.

## Syntax

```javascript
if (condition) {
    // true block
}
else {
    // false block
}
```

---

## Example 1

```javascript
let age = 16;

if (age >= 18) {
    console.log("Eligible");
}
else {
    console.log("Not Eligible");
}
```

Output

```
Not Eligible
```

---

## Example 2

```javascript
let number = 10;

if (number % 2 == 0) {
    console.log("Even Number");
}
else {
    console.log("Odd Number");
}
```

Output

```
Even Number
```

---

## Example 3

```javascript
let password = "admin123";

if (password === "admin123") {
    console.log("Login Successful");
}
else {
    console.log("Wrong Password");
}
```

Output

```
Login Successful
```

---

# 3. else if Statement

Used when multiple conditions need to be checked.

## Syntax

```javascript
if (condition1) {

}
else if (condition2) {

}
else {

}
```

---

## Example 1 (Student Grade)

```javascript
let marks = 82;

if (marks >= 90) {
    console.log("Grade A+");
}
else if (marks >= 75) {
    console.log("Grade A");
}
else if (marks >= 60) {
    console.log("Grade B");
}
else if (marks >= 35) {
    console.log("Grade C");
}
else {
    console.log("Fail");
}
```

Output

```
Grade A
```

---

## Example 2 (Weather)

```javascript
let weather = "Rainy";

if (weather == "Sunny") {
    console.log("Go Outside");
}
else if (weather == "Rainy") {
    console.log("Take an Umbrella");
}
else {
    console.log("Stay Home");
}
```

Output

```
Take an Umbrella
```

---

# 4. Nested if Statement

An `if` statement inside another `if` statement.

## Syntax

```javascript
if (condition1) {

    if (condition2) {

    }

}
```

---

## Example

```javascript
let username = "admin";
let password = "12345";

if (username == "admin") {

    if (password == "12345") {
        console.log("Login Successful");
    }
    else {
        console.log("Incorrect Password");
    }

}
else {
    console.log("Username Not Found");
}
```

Output

```
Login Successful
```

---

# 5. switch Statement

The `switch` statement is used when there are multiple possible values for one variable.

## Syntax

```javascript
switch (expression) {

    case value1:
        // code
        break;

    case value2:
        // code
        break;

    default:
        // code

}
```

---

## Example 1

```javascript
let day = 3;

switch (day) {

    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    case 3:
        console.log("Wednesday");
        break;

    default:
        console.log("Invalid Day");

}
```

Output

```
Wednesday
```

---

## Example 2

```javascript
let color = "red";

switch (color) {

    case "red":
        console.log("Stop");
        break;

    case "yellow":
        console.log("Ready");
        break;

    case "green":
        console.log("Go");
        break;

    default:
        console.log("Unknown Color");

}
```

Output

```
Stop
```

---

# 6. Ternary Operator

A shorthand version of `if...else`.

## Syntax

```javascript
condition ? trueValue : falseValue;
```

---

## Example 1

```javascript
let age = 20;

let result = age >= 18 ? "Adult" : "Minor";

console.log(result);
```

Output

```
Adult
```

---

## Example 2

```javascript
let number = 15;

console.log(number % 2 == 0 ? "Even" : "Odd");
```

Output

```
Odd
```

---

# Comparison Operators

| Operator | Meaning | Example |
|----------|---------|---------|
| == | Equal | 10 == "10" |
| === | Strict Equal | 10 === 10 |
| != | Not Equal | 10 != 20 |
| !== | Strict Not Equal | 10 !== "10" |
| > | Greater Than | 20 > 10 |
| < | Less Than | 10 < 20 |
| >= | Greater Than or Equal | 10 >= 10 |
| <= | Less Than or Equal | 10 <= 20 |

---

# Logical Operators

## AND (&&)

Returns true only if all conditions are true.

```javascript
let age = 22;
let citizen = true;

if (age >= 18 && citizen) {
    console.log("Eligible to Vote");
}
```

---

## OR (||)

Returns true if at least one condition is true.

```javascript
let isStudent = false;
let hasID = true;

if (isStudent || hasID) {
    console.log("Entry Allowed");
}
```

---

## NOT (!)

Reverses the boolean value.

```javascript
let isLoggedIn = false;

if (!isLoggedIn) {
    console.log("Please Login");
}
```

---

# Truthy and Falsy Values

## Falsy Values

```javascript
false
0
-0
0n
""
null
undefined
NaN
```

Everything else is considered **Truthy**.

---

## Example

```javascript
let name = "";

if (name) {
    console.log("Name Exists");
}
else {
    console.log("Name is Empty");
}
```

Output

```
Name is Empty
```

---

# Difference Between if...else and switch

| if...else | switch |
|------------|---------|
| Checks conditions | Checks values |
| Supports ranges | Best for exact values |
| Can use logical operators | Cannot directly use logical operators |
| Better for complex logic | Better for menus/options |

---

# Best Practices

- Use `===` instead of `==`.
- Keep conditions simple and readable.
- Use `switch` when checking many fixed values.
- Use the ternary operator only for short conditions.
- Avoid deeply nested `if` statements.
- Add comments for complex conditions.

---

# Practice Programs

### 1. Check Positive or Negative Number

```javascript
let number = -5;

if (number > 0) {
    console.log("Positive");
}
else if (number < 0) {
    console.log("Negative");
}
else {
    console.log("Zero");
}
```

---

### 2. Find Largest Number

```javascript
let a = 15;
let b = 20;

if (a > b) {
    console.log("A is Greater");
}
else {
    console.log("B is Greater");
}
```

---

### 3. Voting Eligibility

```javascript
let age = 17;

if (age >= 18) {
    console.log("Eligible");
}
else {
    console.log("Not Eligible");
}
```

---

### 4. Leap Year Checker

```javascript
let year = 2024;

if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0) {
    console.log("Leap Year");
}
else {
    console.log("Not a Leap Year");
}
```

---

### 5. Calculator using switch

```javascript
let num1 = 20;
let num2 = 10;
let operator = "+";

switch (operator) {

    case "+":
        console.log(num1 + num2);
        break;

    case "-":
        console.log(num1 - num2);
        break;

    case "*":
        console.log(num1 * num2);
        break;

    case "/":
        console.log(num1 / num2);
        break;

    default:
        console.log("Invalid Operator");
}
```

---


# 📘 JavaScript Notes - Functions

> **Module:** JavaScript Fundamentals
> **Topic:** Functions
> **Level:** Beginner to Advanced

---

# 📖 What is a Function?

A **Function** is a reusable block of code that performs a specific task.

Instead of writing the same code again and again, we write it once inside a function and call it whenever needed.

## Definition

> **A function is a block of code designed to perform a particular task. It executes only when it is called (invoked).**

---

# Why Do We Use Functions?

Functions help us to:

- Reuse code
- Reduce code duplication
- Improve readability
- Make debugging easier
- Break large programs into smaller modules
- Increase maintainability

---

# Real-Life Example

Imagine you make tea every morning.

Instead of remembering every step every day:

- Boil Water
- Add Tea
- Add Sugar
- Add Milk

You simply call a process called **makeTea()**.

The same concept applies in JavaScript.

```
Start

↓

Call Function

↓

Execute Code

↓

Return Result

↓

Continue Program
```

---

# Syntax of Function

```javascript
function functionName() {

    // Code

}
```

Example

```javascript
function greet() {
    console.log("Welcome to JavaScript");
}

greet();
```

Output

```
Welcome to JavaScript
```

---

# Function with Parameters

Parameters are variables that receive values.

```javascript
function greet(name) {
    console.log("Welcome " + name);
}

greet("Durgesh");
```

Output

```
Welcome Durgesh
```

---

# Function with Multiple Parameters

```javascript
function add(a, b) {
    console.log(a + b);
}

add(10,20);
```

Output

```
30
```

---

# Parameters vs Arguments

| Parameter | Argument |
|------------|----------|
| Variables in function definition | Actual values passed while calling |
| Receive data | Send data |

Example

```javascript
function add(a,b){

}

add(10,20);
```

Here

```
a,b → Parameters

10,20 → Arguments
```

---

# Return Statement

The return keyword sends a value back from a function.

```javascript
function add(a,b){

    return a+b;

}

let result = add(20,30);

console.log(result);
```

Output

```
50
```

---

# Types of Functions

JavaScript provides many types of functions.

1. Function Declaration
2. Function Expression
3. Anonymous Function
4. Arrow Function
5. Immediately Invoked Function (IIFE)
6. Callback Function
7. Higher Order Function
8. Constructor Function
9. Generator Function
10. Recursive Function

---

# 1. Function Declaration

Also called **Named Function**.

Syntax

```javascript
function greet(){

}
```

Example

```javascript
function greet(){

    console.log("Hello Students");

}

greet();
```

Output

```
Hello Students
```

### Features

- Has a name
- Hoisted
- Can be called before declaration

Example

```javascript
greet();

function greet(){

    console.log("Hello");

}
```

Output

```
Hello
```

---

# 2. Function Expression

A function stored inside a variable.

Syntax

```javascript
const variable = function(){

};
```

Example

```javascript
const greet = function(){

    console.log("Hello JavaScript");

};

greet();
```

Output

```
Hello JavaScript
```

### Features

- Stored inside variable
- Not hoisted like declaration
- More common in modern JavaScript

Example

```javascript
sayHello();

const sayHello = function(){

    console.log("Hello");

};
```

Output

```
ReferenceError
```

---

# 3. Anonymous Function

A function without a name.

Example

```javascript
const greet = function(){

    console.log("Hello");

};

greet();
```

Another Example

```javascript
setTimeout(function(){

    console.log("Executed");

},2000);
```

Output

```
Executed
```

Anonymous functions are mostly used

- Events
- Timers
- Callback Functions

---

# 4. Arrow Function (ES6)

Introduced in ES6.

Short syntax.

Syntax

```javascript
const functionName = ()=>{

}
```

Example

```javascript
const greet = ()=>{

    console.log("Hello");

};

greet();
```

Output

```
Hello
```

---

# Arrow Function with Parameters

```javascript
const add = (a,b)=>{

    return a+b;

}

console.log(add(10,20));
```

Output

```
30
```

---

# Arrow Function (Short Form)

```javascript
const square = number => number * number;

console.log(square(5));
```

Output

```
25
```

---

# Difference Between Normal Function and Arrow Function

| Normal Function | Arrow Function |
|----------------|----------------|
| Uses function keyword | Uses => |
| Has its own this | Doesn't have its own this |
| Can be Constructor | Cannot be Constructor |
| Supports arguments object | Doesn't support arguments |

---

# 5. Immediately Invoked Function Expression (IIFE)

Runs immediately after creation.

Syntax

```javascript
(function(){

})();
```

Example

```javascript
(function(){

    console.log("Application Started");

})();
```

Output

```
Application Started
```

---

# 6. Callback Function

A function passed as an argument to another function.

Example

```javascript
function greet(name){

    console.log("Hello " + name);

}

function processUser(callback){

    callback("Durgesh");

}

processUser(greet);
```

Output

```
Hello Durgesh
```

Another Example

```javascript
setTimeout(function(){

    console.log("Executed after 3 seconds");

},3000);
```

---

# 7. Higher Order Function

A function that

- Accepts another function
- Returns another function

Example

```javascript
function calculator(operation,a,b){

    return operation(a,b);

}

function add(a,b){

    return a+b;

}

console.log(calculator(add,10,20));
```

Output

```
30
```

---

# 8. Recursive Function

A function that calls itself.

Example

```javascript
function countdown(number){

    if(number==0){

        return;

    }

    console.log(number);

    countdown(number-1);

}

countdown(5);
```

Output

```
5
4
3
2
1
```

---

# 9. Constructor Function

Used to create objects.

```javascript
function Student(name,age){

    this.name=name;
    this.age=age;

}

const s1 = new Student("Durgesh",22);

console.log(s1);
```

Output

```
Student { name: 'Durgesh', age: 22 }
```

---

# Function Scope

```javascript
function demo(){

    let name="Durgesh";

    console.log(name);

}

demo();
```

Output

```
Durgesh
```

Outside

```javascript
console.log(name);
```

Output

```
ReferenceError
```

---

# Default Parameters

```javascript
function greet(name="Guest"){

    console.log(name);

}

greet();
```

Output

```
Guest
```

---

# Rest Parameter

```javascript
function total(...numbers){

    console.log(numbers);

}

total(10,20,30,40);
```

Output

```
[10,20,30,40]
```

---

# Spread Operator

```javascript
const numbers=[10,20,30];

console.log(...numbers);
```

Output

```
10 20 30
```

---

# Practice Programs

## Addition

```javascript
function add(a,b){

    return a+b;

}

console.log(add(10,20));
```

---

## Even or Odd

```javascript
function evenOdd(number){

    if(number%2==0)

        return "Even";

    return "Odd";

}

console.log(evenOdd(15));
```

---

## Find Maximum

```javascript
function max(a,b){

    return a>b?a:b;

}

console.log(max(10,25));
```

---

## Factorial

```javascript
function factorial(n){

    if(n==1)

        return 1;

    return n*factorial(n-1);

}

console.log(factorial(5));
```

Output

```
120
```

---

## Reverse String

```javascript
function reverse(text){

    return text.split("").reverse().join("");

}

console.log(reverse("JavaScript"));
```

Output

```
tpircSavaJ
```





