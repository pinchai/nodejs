# JavaScript ES Modules — Lesson

## Learning Objectives

By the end of this lesson, students will be able to:

1. Explain what **ES Modules** are.
2. Differentiate between **CommonJS** and **ES Modules**.
3. Export variables and functions.
4. Import modules using different techniques.
5. Create reusable JavaScript modules.
6. Build a simple multi-file application using ES Modules.

---

# 1. What Are ES Modules?

**ES Modules (ESM)** are the standard JavaScript module system introduced in **ECMAScript 2015 (ES6)**.

Modules allow us to split a large JavaScript application into multiple smaller files.

Instead of:

```text
app.js
└── 1000 lines of code
```

we can organize our application:

```text
project/
├── app.js
├── math.js
├── user.js
└── message.js
```

Each file can contain its own variables and functions.

### Why use modules?

Modules help us:

- Organize code
- Reuse code
- Avoid global variables
- Separate responsibilities
- Make applications easier to maintain
- Build larger applications

---

# 2. ES Modules vs CommonJS

JavaScript has two common module systems.

| Feature | ES Modules | CommonJS |
|---|---|---|
| Standard | Modern JavaScript standard | Traditionally Node.js |
| Export | `export` | `module.exports` |
| Import | `import` | `require()` |
| File extension | `.js` / `.mjs` | `.js` / `.cjs` |
| Syntax | Modern | Older Node.js style |
| Browser support | Native | Not directly |
| Node.js | Yes | Yes |

### CommonJS

```javascript
// math.js

function add(a, b) {
    return a + b;
}

module.exports = {
    add
};
```

Import:

```javascript
const { add } = require("./math");

console.log(add(10, 20));
```

### ES Modules

```javascript
// math.js

export function add(a, b) {
    return a + b;
}
```

Import:

```javascript
import { add } from "./math.js";

console.log(add(10, 20));
```

### Main difference

CommonJS:

```javascript
const math = require("./math");
```

ES Modules:

```javascript
import math from "./math.js";
```

For modern JavaScript projects, **ES Modules are generally the preferred standard**.

---

# 3. Export Variables

We can export variables using the `export` keyword.

## Named Export

```javascript
// config.js

export const appName = "Student Management System";
export const version = "1.0.0";
```

Then import them:

```javascript
// app.js

import { appName, version } from "./config.js";

console.log(appName);
console.log(version);
```

Output:

```text
Student Management System
1.0.0
```

---

# 4. Export Functions

Functions can also be exported.

```javascript
// math.js

export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}
```

Import:

```javascript
// app.js

import { add, subtract } from "./math.js";

console.log(add(10, 5));
console.log(subtract(10, 5));
```

Output:

```text
15
5
```

---

# 5. Export Multiple Items

We can define everything first and export them later.

```javascript
// math.js

function add(a, b) {
    return a + b;
}

function subtract(a, b) {
    return a - b;
}

const PI = 3.14159;

export {
    add,
    subtract,
    PI
};
```

Import:

```javascript
import {
    add,
    subtract,
    PI
} from "./math.js";
```

---

# 6. Default Export

A module can have **one default export**.

```javascript
// user.js

export default function getUser() {
    return {
        id: 1,
        name: "Dara"
    };
}
```

Import:

```javascript
import getUser from "./user.js";

console.log(getUser());
```

Notice that we don't use `{ }` for a default import.

### Named export

```javascript
export function getUser() {}
```

Import:

```javascript
import { getUser } from "./user.js";
```

### Default export

```javascript
export default function getUser() {}
```

Import:

```javascript
import getUser from "./user.js";
```

---

# 7. Import Techniques

## 7.1 Import a Named Export

```javascript
import { add } from "./math.js";
```

## 7.2 Import Multiple Named Exports

```javascript
import { add, subtract, PI } from "./math.js";
```

## 7.3 Rename an Import

We can use `as`.

```javascript
import { add as sum } from "./math.js";

console.log(sum(10, 20));
```

## 7.4 Import Everything

Use `* as`.

```javascript
import * as math from "./math.js";

console.log(math.add(10, 20));
console.log(math.subtract(20, 5));
```

If `math.js` contains:

```javascript
export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}
```

we can access:

```javascript
math.add()
math.subtract()
```

## 7.5 Import Default Export

```javascript
import getUser from "./user.js";
```

## 7.6 Import Default + Named Exports

```javascript
import getUser, { login, logout } from "./auth.js";
```

---

# 8. Reusable JavaScript Modules

A good module normally has **one main responsibility**.

For example:

```text
src/
├── app.js
├── math.js
├── user.js
└── message.js
```

### math.js

```javascript
export function add(a, b) {
    return a + b;
}

export function multiply(a, b) {
    return a * b;
}
```

### user.js

```javascript
export function createUser(name, age) {
    return {
        name,
        age
    };
}
```

### message.js

```javascript
export function welcome(name) {
    return `Welcome, ${name}!`;
}
```

### app.js

```javascript
import { add, multiply } from "./math.js";
import { createUser } from "./user.js";
import { welcome } from "./message.js";

const user = createUser("Dara", 20);

console.log(welcome(user.name));

console.log(add(10, 20));
console.log(multiply(5, 4));
```

This is much easier to maintain than putting everything into one file.

---

# 9. ES Modules in the Browser

To use ES Modules in HTML, use:

```html
<script type="module" src="./app.js"></script>
```

Example:

```text
project/
├── index.html
├── app.js
├── math.js
└── user.js
```

### index.html

```html
<!DOCTYPE html>
<html>
<head>
    <title>ES Modules</title>
</head>
<body>

    <h1>ES Modules Example</h1>

    <script type="module" src="./app.js"></script>

</body>
</html>
```

### math.js

```javascript
export function add(a, b) {
    return a + b;
}
```

### app.js

```javascript
import { add } from "./math.js";

const result = add(10, 20);

console.log(result);
```

Output:

```text
30
```

> When testing browser modules, it is recommended to use a local development server rather than opening the HTML file directly with `file://`.

---

# 10. Simple Multi-File Application

Let's build a small **Student Management Application**.

## Project Structure

```text
student-app/
│
├── index.html
│
└── js/
    ├── app.js
    ├── student.js
    └── message.js
```

## Step 1 — Student Module

### `student.js`

```javascript
export function createStudent(id, name, age) {
    return {
        id,
        name,
        age
    };
}

export function showStudent(student) {
    console.log(`
ID: ${student.id}
Name: ${student.name}
Age: ${student.age}
`);
}
```

## Step 2 — Message Module

### `message.js`

```javascript
export function welcome(name) {
    return `Welcome ${name}`;
}

export function goodbye(name) {
    return `Goodbye ${name}`;
}
```

## Step 3 — Main Application

### `app.js`

```javascript
import {
    createStudent,
    showStudent
} from "./student.js";

import {
    welcome,
    goodbye
} from "./message.js";

const student = createStudent(
    1,
    "Dara",
    20
);

console.log(welcome(student.name));

showStudent(student);

console.log(goodbye(student.name));
```

## Step 4 — HTML

### `index.html`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Student App</title>
</head>

<body>

    <h1>Student Management</h1>

    <script type="module" src="./js/app.js"></script>

</body>

</html>
```

---

# 11. Module Dependency

Our application now has this relationship:

```text
                index.html
                    │
                    ▼
                  app.js
                 /     \
                ▼       ▼
          student.js   message.js
```

`app.js` imports functionality from:

```text
student.js
message.js
```

This is called a **module dependency**.

---

# 12. Node.js ES Modules

Node.js supports ES Modules.

For example:

```text
project/
├── package.json
├── app.js
└── math.js
```

`package.json`:

```json
{
    "type": "module"
}
```

Now Node.js treats `.js` files as ES Modules.

### math.js

```javascript
export function add(a, b) {
    return a + b;
}
```

### app.js

```javascript
import { add } from "./math.js";

console.log(add(10, 20));
```

Run:

```bash
node app.js
```

Output:

```text
30
```

---

# 13. Important Rule: File Extensions

When using native ES Modules in Node.js, include the extension:

```javascript
import { add } from "./math.js";
```

Instead of:

```javascript
import { add } from "./math";
```

This is especially important when working with native Node.js ESM.

---

# 14. ES Modules Best Practices

### 1. Keep modules focused

Good:

```text
user.js
product.js
order.js
database.js
```

Avoid one huge:

```text
everything.js
```

### 2. Use named exports when there are multiple related functions

```javascript
export function add() {}
export function subtract() {}
export function multiply() {}
```

### 3. Use default export for the main functionality

```javascript
export default class User {}
```

### 4. Use meaningful file names

```text
user-service.js
product-service.js
auth-service.js
```

### 5. Avoid unnecessary global variables

Modules naturally provide scope.

---

# 15. Quick Cheat Sheet

### Export variable

```javascript
export const name = "Dara";
```

### Export function

```javascript
export function hello() {
    console.log("Hello");
}
```

### Named import

```javascript
import { hello } from "./message.js";
```

### Multiple imports

```javascript
import { add, subtract } from "./math.js";
```

### Rename import

```javascript
import { add as sum } from "./math.js";
```

### Import everything

```javascript
import * as math from "./math.js";
```

### Default export

```javascript
export default function hello() {}
```

### Default import

```javascript
import hello from "./hello.js";
```

### Browser

```html
<script type="module" src="./app.js"></script>
```

### Node.js

```json
{
    "type": "module"
}
```

---

# Practice Exercises

## Exercise 1 — Math Module

Create:

```text
math.js
app.js
```

Export:

```javascript
add()
subtract()
multiply()
divide()
```

Import them into `app.js` and test them.

---

## Exercise 2 — Student Module

Create:

```text
student.js
app.js
```

Create:

```javascript
createStudent()
showStudent()
```

A student should contain:

```javascript
{
    id: 1,
    name: "Dara",
    age: 20
}
```

---

## Exercise 3 — Product Application

Create:

```text
product-app/
├── index.html
└── js/
    ├── app.js
    ├── product.js
    └── cart.js
```

Requirements:

### `product.js`

Create:

```javascript
createProduct()
```

### `cart.js`

Create:

```javascript
addToCart()
removeFromCart()
getTotal()
```

### `app.js`

Import the functions and create a simple shopping-cart application.

---

# Key Concept

```text
One large application
        ↓
Many small modules
        ↓
      export
        ↓
      import
        ↓
Reusable + maintainable code
```

ES Modules are the foundation for the module systems used by modern JavaScript applications and frameworks such as **Node.js, React, Vue, and Angular**.
