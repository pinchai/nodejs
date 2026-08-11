# JavaScript ES Modules And CommonJS

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
