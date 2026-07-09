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

# Summary

JavaScript operators are used for:

- Mathematical calculations
- Assigning values
- Comparing values
- Creating logical conditions
- Checking data types
- Working with strings
- Performing conditional operations


Understanding operators is an important foundation for JavaScript programming.
