# React.js Complete Notes

# What is React.js?

**React.js** is a free and open-source JavaScript library used to build fast, interactive, and reusable User Interfaces (UI), especially for Single Page Applications (SPA).

React was developed by **Facebook (Meta)** in **2013**.

Instead of updating the entire webpage, React updates only the changed part of the page, making applications faster and more efficient.

---

# Definition

> React.js is a JavaScript library used to build reusable UI components and create fast, dynamic web applications.

---

# Why React.js?

Before React, developers mainly used JavaScript or jQuery to manipulate the DOM.

Problems with traditional JavaScript:

- Large codebase
- Slow DOM updates
- Difficult to maintain
- Repeated code
- Poor scalability
- Hard to manage application state

React solves these problems by introducing:

- Components
- Virtual DOM
- State Management
- One-way Data Flow
- Reusable Code

---

# Why is React Popular?

React is popular because it is:

- Fast
- Easy to learn
- Component-based
- Reusable
- Flexible
- SEO Friendly (with Next.js)
- Huge Community
- Used by large companies

---

# Companies Using React

Some popular companies that use React:

- Facebook
- Instagram
- Netflix
- WhatsApp Web
- Airbnb
- Dropbox
- Uber
- Discord
- Pinterest
- Atlassian

---

# What Can We Build with React?

Using React we can build:

- Portfolio Websites
- E-commerce Websites
- Admin Dashboards
- CRM Software
- ERP Systems
- Hospital Management Systems
- School Management Systems
- Social Media Applications
- Chat Applications
- Job Portals
- Banking Applications
- Food Delivery Apps
- OTT Platforms

---

# Features of React

## 1. Component-Based Architecture

React applications are divided into small reusable pieces called Components.

Example:

```
App
│
├── Navbar
├── Sidebar
├── Home
├── Footer
```

Benefits:

- Reusable
- Easy to Maintain
- Easy to Test

---

## 2. Virtual DOM

React creates a Virtual DOM instead of directly changing the Real DOM.

Flow:

```
User Action

↓

State Changes

↓

Virtual DOM Created

↓

Compare Old Virtual DOM

↓

Find Difference

↓

Update Only Changed Elements

↓

Real DOM Updated
```

Advantages:

- Faster rendering
- Better performance
- Less DOM manipulation

---

## 3. JSX

React uses JSX.

JSX stands for

**JavaScript XML**

Example:

```jsx
const element = <h1>Hello React</h1>;
```

Without JSX:

```javascript
React.createElement("h1", null, "Hello React");
```

---

## 4. Reusable Components

Create once.

Use many times.

Example:

```jsx
<Button />
<Button />
<Button />
<Button />
```

---

## 5. One-Way Data Binding

Data always flows

```
Parent

↓

Child
```

This makes debugging easier.

---

## 6. State Management

React can store dynamic data.

Example:

```jsx
const [count, setCount] = useState(0);
```

---

## 7. Props

Props are used to send data from Parent Component to Child Component.

Example:

```jsx
<Student name="Rahul" age="20" />
```

Child:

```jsx
function Student(props){
    return <h1>{props.name}</h1>
}
```

---

## 8. Fast Rendering

React updates only changed elements.

Not the complete webpage.

---

## 9. Cross Platform

React

↓

React Native

↓

Android + iOS Apps

---

## 10. Huge Ecosystem

React has thousands of libraries.

Examples:

- React Router
- Redux
- Axios
- Tailwind CSS
- Material UI
- Bootstrap
- React Hook Form

---

# Advantages of React

## 1. Reusable Components

Write once.

Use multiple times.

Example:

Navbar

can be used on every page.

---

## 2. Fast Performance

Because of

Virtual DOM

React is much faster than traditional DOM manipulation.

---

## 3. Easy to Learn

If you know

- HTML
- CSS
- JavaScript

Learning React becomes much easier.

---

## 4. Component-Based Development

Large applications become easier to manage.

---

## 5. Easy Maintenance

Each component has its own responsibility.

Easy to update.

---

## 6. Large Community Support

Millions of developers use React.

Thousands of tutorials are available.

---

## 7. SEO Support

Using Next.js

React becomes SEO friendly.

---

## 8. Rich Ecosystem

Many ready-made libraries are available.

Examples:

- Redux
- React Router
- Axios
- Tailwind

---

## 9. Better User Experience

Fast page updates.

Smooth navigation.

---

## 10. High Demand

React developers are highly demanded in the software industry.

---

# Disadvantages of React

## 1. Only UI Library

React handles only the User Interface.

For complete application development, additional libraries are needed.

Examples:

- React Router
- Redux
- Axios

---

## 2. Fast Changing Technology

React updates frequently.

Developers need to learn new features regularly.

---

## 3. Learning Curve

To master React you also need:

- JavaScript ES6+
- Hooks
- Routing
- State Management
- API Integration

---

## 4. More Configuration

For large projects additional setup is required.

Example:

- Routing
- Redux
- Authentication
- Folder Structure

---

## 5. JSX May Feel Strange Initially

HTML inside JavaScript can confuse beginners.

---

# React vs JavaScript

| JavaScript | React |
|------------|--------|
| Programming Language | JavaScript Library |
| Manipulates DOM Directly | Uses Virtual DOM |
| More Manual Coding | Component-Based |
| Less Reusable | Highly Reusable |
| Slower UI Updates | Faster UI Updates |
| Harder for Large Projects | Easier for Large Projects |

---

# React vs Angular

| React | Angular |
|--------|----------|
| Library | Framework |
| Developed by Meta | Developed by Google |
| Easy to Learn | Harder to Learn |
| Virtual DOM | Real DOM |
| JSX | HTML Templates |
| Flexible | Opinionated |
| Faster | Slightly Heavier |

---

# React vs Vue

| React | Vue |
|--------|------|
| JSX | HTML Templates |
| Large Community | Smaller Community |
| Meta | Evan You |
| More Jobs | Growing Popularity |
| Flexible | Easy for Beginners |

---

# React Folder Structure

```
my-app/

│

├── public/

│

├── src/

│   ├── assets/

│   ├── components/

│   ├── pages/

│   ├── hooks/

│   ├── services/

│   ├── context/

│   ├── App.jsx

│   ├── main.jsx

│

├── package.json

├── package-lock.json

├── vite.config.js

└── node_modules/
```

---

# React Application Flow

```
Browser

↓

main.jsx

↓

<App />

↓

Components

↓

JSX

↓

Virtual DOM

↓

Real DOM

↓

Display on Screen
```

---

# Real DOM vs Virtual DOM

## Real DOM

```
User Click

↓

Entire DOM Updated

↓

Slow Performance
```

---

## Virtual DOM

```
User Click

↓

Virtual DOM

↓

Compare Old Version

↓

Update Only Changed Part

↓

Fast Performance
```

---

# Common React Terminology

| Term | Meaning |
|------|----------|
| JSX | JavaScript XML |
| Component | Reusable UI Block |
| Props | Parent to Child Data |
| State | Component Data |
| Hook | Special React Function |
| Event | User Action |
| Virtual DOM | Virtual Copy of Real DOM |
| Rendering | Display UI |
| Router | Page Navigation |
| API | Backend Communication |

---

# Real-Life Example

Imagine a classroom.

Teacher changes one student's attendance.

### Traditional JavaScript

The teacher rewrites the entire attendance register.

### React

The teacher updates only that one student's attendance.

This saves time and effort.

---

# Where React is Used

- Facebook
- Instagram
- Netflix
- YouTube Dashboard
- WhatsApp Web
- Gmail-like Applications
- Amazon Dashboards
- Online Banking
- CRM Systems
- ERP Software
- Admin Panels
- E-commerce Websites

---

# React.js Rules

React follows some important rules and best practices. Following these rules helps you write clean, maintainable, and efficient React applications.

---

# 1. Component Names Must Start with a Capital Letter

React treats lowercase names as HTML elements. Always start component names with an uppercase letter.

✅ Correct

```jsx
function Home() {
    return <h1>Home Page</h1>;
}
```

❌ Incorrect

```jsx
function home() {
    return <h1>Home Page</h1>;
}
```

---

# 2. A Component Must Return Only One Parent Element

A React component should return a single parent element.

✅ Correct

```jsx
function App() {
    return (
        <div>
            <h1>Hello</h1>
            <p>Welcome</p>
        </div>
    );
}
```

You can also use a Fragment.

```jsx
function App() {
    return (
        <>
            <h1>Hello</h1>
            <p>Welcome</p>
        </>
    );
}
```

❌ Incorrect

```jsx
function App() {
    return (
        <h1>Hello</h1>
        <p>Welcome</p>
    );
}
```

---

# 3. Never Modify State Directly

Always use the state update function.

✅ Correct

```jsx
setCount(count + 1);
```

❌ Incorrect

```jsx
count = count + 1;
```

---

# 4. Never Mutate Objects or Arrays in State

Create a new object or array instead of modifying the existing one.

✅ Correct

```jsx
setUsers([...users, newUser]);
```

❌ Incorrect

```jsx
users.push(newUser);
setUsers(users);
```

---

# 5. Use `className` Instead of `class`

Since `class` is a JavaScript keyword, React uses `className`.

✅ Correct

```jsx
<div className="container"></div>
```

❌ Incorrect

```jsx
<div class="container"></div>
```

---

# 6. Use `htmlFor` Instead of `for`

React uses `htmlFor` for labels.

✅ Correct

```jsx
<label htmlFor="email">Email</label>
<input id="email" />
```

❌ Incorrect

```jsx
<label for="email">Email</label>
```

---

# 7. JSX Expressions Use Curly Braces `{}`

To display JavaScript values in JSX, wrap them in curly braces.

```jsx
const name = "Rahul";

function App() {
    return <h1>Hello {name}</h1>;
}
```

---

# 8. Props Are Read-Only

Never change props inside a child component.

✅ Correct

```jsx
function Student(props) {
    return <h1>{props.name}</h1>;
}
```

❌ Incorrect

```jsx
props.name = "Amit";
```

---

# 9. Hooks Can Only Be Called at the Top Level

Always call Hooks at the top of the component.

✅ Correct

```jsx
function App() {
    const [count, setCount] = useState(0);
}
```

❌ Incorrect

```jsx
if (true) {
    const [count, setCount] = useState(0);
}
```

---

# 10. Hooks Can Only Be Used Inside Functional Components or Custom Hooks

✅ Correct

```jsx
function App() {
    const [count, setCount] = useState(0);
}
```

❌ Incorrect

```jsx
function add() {
    useState(0);
}
```

---

# 11. Always Provide a `key` When Rendering Lists

Keys help React identify which items have changed.

✅ Correct

```jsx
const users = ["A", "B", "C"];

users.map((user, index) => (
    <li key={index}>{user}</li>
));
```

---

# 12. Use Event Handlers Instead of HTML Events

React uses camelCase event names.

✅ Correct

```jsx
<button onClick={handleClick}>Click</button>
```

❌ Incorrect

```jsx
<button onclick="handleClick()">Click</button>
```

---

# 13. Use Self-Closing Tags

Elements without children should be self-closing.

✅ Correct

```jsx
<img src="logo.png" />
<input />
<br />
```

---

# 14. Components Should Have a Single Responsibility

Each component should perform one main task.

Example:

- Navbar Component
- Footer Component
- Login Component
- Product Component

Avoid putting all code in one component.

---

# 15. Keep Components Small and Reusable

Instead of writing one large component, divide it into smaller components.

Example:

```
App
├── Navbar
├── Sidebar
├── Home
├── Footer
```

---

# 16. Use Meaningful Component Names

Choose names that describe the component.

✅ Good

- UserCard
- ProductList
- LoginForm
- Navbar

❌ Bad

- Data
- Test
- Temp

---

# 17. Avoid Inline Functions When Not Necessary

Instead of:

```jsx
<button onClick={() => handleClick()}>
    Click
</button>
```

Prefer:

```jsx
<button onClick={handleClick}>
    Click
</button>
```

---

# 18. Separate UI and Business Logic

Keep API calls and business logic separate from UI when possible.

Example:

```
components/
pages/
services/
hooks/
utils/
```

---

# 19. Use Destructuring for Props

✅ Better

```jsx
function Student({ name, age }) {
    return <h1>{name}</h1>;
}
```

Instead of:

```jsx
function Student(props) {
    return <h1>{props.name}</h1>;
}
```

---

# 20. Follow One-Way Data Flow

Data should flow from Parent Component to Child Component using props.

```
Parent Component
        ↓
   Child Component
```

This makes applications easier to understand and debug.



# JSX (JavaScript XML)

## What is JSX?

**JSX (JavaScript XML)** is a syntax extension for JavaScript that allows us to write HTML-like code inside JavaScript.

It makes React code easier to read, write, and understand.

Although JSX looks like HTML, it is **not HTML**. Before the browser executes it, React converts JSX into regular JavaScript using tools like **Babel**.

---

# Full Form of JSX

**JSX = JavaScript XML**

- **JavaScript** → Programming language
- **XML** → HTML-like syntax

---

# Why Do We Use JSX?

Without JSX, creating UI in React becomes difficult because we have to use `React.createElement()`.

JSX makes the code:

- More readable
- Easier to write
- Similar to HTML
- Easier to maintain
- Less complex

Instead of writing long JavaScript code to create HTML elements, we can simply write HTML-like syntax.

---

# Why Was JSX Introduced?

Before JSX, developers had to create every HTML element using JavaScript functions.

Example:

```javascript
React.createElement(
    "h1",
    null,
    "Hello World"
);
```

This code becomes difficult to read as the application grows.

With JSX, the same code becomes:

```jsx
<h1>Hello World</h1>
```

This is much cleaner and easier to understand.

---

# JSX vs HTML

JSX looks like HTML but there are some important differences.

| HTML | JSX |
|------|-----|
| Uses `class` | Uses `className` |
| Uses `for` | Uses `htmlFor` |
| Attributes are lowercase | Event names use camelCase |
| Cannot directly use JavaScript | JavaScript can be written using `{}` |

---

# Example of JSX

```jsx
function App() {
    return (
        <h1>Welcome to React</h1>
    );
}
```

---

# Example Without JSX

```javascript
function App() {
    return React.createElement(
        "h1",
        null,
        "Welcome to React"
    );
}
```

Both examples produce the same output, but JSX is much easier to write and understand.

---

# How JSX Works

When you write JSX:

```jsx
<h1>Hello React</h1>
```

React (using Babel) converts it into:

```javascript
React.createElement(
    "h1",
    null,
    "Hello React"
);
```

So, browsers never see JSX directly—they only execute the JavaScript generated from it.

---

# Advantages of JSX

### 1. Easy to Read

JSX looks like HTML, so developers can understand it quickly.

```jsx
<h1>React</h1>
```

---

### 2. Easy to Write

Creating user interfaces requires less code.

```jsx
<div>
    <h1>Hello</h1>
    <p>Welcome</p>
</div>
```

---

### 3. Improves Code Readability

The UI structure is easy to understand at a glance.

---

### 4. Supports JavaScript Expressions

You can display variables and expressions using curly braces `{}`.

```jsx
const name = "Rahul";

function App() {
    return <h1>Hello {name}</h1>;
}
```

Output:

```
Hello Rahul
```

---

### 5. Dynamic Content

JSX makes it easy to display changing data.

```jsx
const price = 1000;

<p>Price: ₹{price}</p>
```

Output:

```
Price: ₹1000
```

---

### 6. Supports Conditional Rendering

```jsx
const isLogin = true;

function App() {
    return (
        <h1>{isLogin ? "Welcome" : "Please Login"}</h1>
    );
}
```

---

### 7. Supports Loops

```jsx
const fruits = ["Apple", "Mango", "Orange"];

function App() {
    return (
        <ul>
            {fruits.map((fruit) => (
                <li key={fruit}>{fruit}</li>
            ))}
        </ul>
    );
}
```

---

### 8. Component Friendly

JSX allows components to be used like HTML tags.

```jsx
<Navbar />
<Home />
<Footer />
```

---

# JSX Rules

## Rule 1: Return a Single Parent Element

✅ Correct

```jsx
return (
    <div>
        <h1>Hello</h1>
        <p>Welcome</p>
    </div>
);
```

Or use a Fragment:

```jsx
return (
    <>
        <h1>Hello</h1>
        <p>Welcome</p>
    </>
);
```

❌ Incorrect

```jsx
return (
    <h1>Hello</h1>
    <p>Welcome</p>
);
```

---

## Rule 2: Close Every Tag

✅ Correct

```jsx
<img src="logo.png" />
<input />
<br />
```

❌ Incorrect

```jsx
<img src="logo.png">
```

---

## Rule 3: Use `className` Instead of `class`

✅ Correct

```jsx
<div className="container"></div>
```

❌ Incorrect

```jsx
<div class="container"></div>
```

---

## Rule 4: Use `htmlFor` Instead of `for`

✅ Correct

```jsx
<label htmlFor="email">Email</label>
```

❌ Incorrect

```jsx
<label for="email">Email</label>
```

---

## Rule 5: Use Curly Braces `{}` for JavaScript

```jsx
const age = 22;

<p>Age: {age}</p>
```

You can also use expressions:

```jsx
<p>{10 + 20}</p>
```

Output:

```
30
```

---

## Rule 6: Event Names Use camelCase

✅ Correct

```jsx
<button onClick={handleClick}>
    Click
</button>
```

❌ Incorrect

```jsx
<button onclick="handleClick()">
    Click
</button>
```

---

# Real-Life Example

Imagine you are designing a house.

- **HTML** is like the walls and rooms of the house.
- **JavaScript** adds functionality such as lights and fans.
- **JSX** lets you describe both the structure and dynamic content together in one place, making development easier.




