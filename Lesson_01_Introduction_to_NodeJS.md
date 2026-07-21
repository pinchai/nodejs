# Lesson 1: Introduction to Node.js

## Learning Objectives

After completing this lesson, students will be able to:

- Understand what Node.js is.
- Explain why Node.js was created.
- Understand the difference between JavaScript in the browser and
  Node.js.
- Install Node.js.
- Verify the installation.
- Write and execute their first Node.js program.
- Understand how Node.js executes JavaScript.
- Know where Node.js is commonly used.

## Lesson Outline

Topic Duration

---

What is Node.js?  
 History of Node.js  
 Why Use Node.js?  
 Browser JavaScript vs Node.js  
 How Node.js Works  
 Installing Node.js  
 First Node.js Program  
 Exercise

## What is Node.js?

Node.js is an **open-source JavaScript runtime environment** that allows
developers to run JavaScript **outside the web browser**.

### Runtime

A runtime is software that executes programming code.

```text
JavaScript
    ↓
Node.js Runtime
    ↓
Program Runs
```

## Why Was Node.js Created?

Before Node.js, JavaScript only ran in browsers. Ryan Dahl created
Node.js in **2009** so JavaScript could also run on servers, allowing
developers to use JavaScript for both frontend and backend development.

## What Can Node.js Build?

- REST APIs
- Web Servers
- Chat Applications
- Online Games
- Real-time Dashboards
- Streaming Services
- CLI Tools
- Desktop Apps (Electron)
- Automation Scripts
- Microservices

## Why Choose Node.js?

### Fast

Built on Google's V8 JavaScript Engine.

### Non-blocking I/O

Node.js handles many operations concurrently without blocking the main
thread.

### Single Language

Use JavaScript for both frontend and backend.

### Huge Ecosystem

Millions of packages are available through npm.

### Cross Platform

Runs on Windows, macOS, and Linux.

## Browser JavaScript vs Node.js

Browser JavaScript Node.js

---

Runs in browser Runs outside browser
Uses DOM No DOM
Has `window` No `window`
Has `document` No `document`
Limited system access Can access files, network, OS

Browser example:

```javascript
document.getElementById("title").innerHTML = "Hello";
```

Node.js example:

```javascript
console.log("Hello Node.js");
```

## Install Node.js

Download Node.js from:

https://nodejs.org

Verify installation:

```bash
node -v
npm -v
```

## First Program

Create `app.js`

```javascript
console.log("Hello Node.js!");
```

Run:

```bash
node app.js
```

## Useful Globals

```javascript
console.log(__dirname);
console.log(__filename);
console.log(process.version);
console.log(process.platform);
```

## REPL

Start:

```bash
node
```

Exit:

```text
.exit
```

## Advantages

- Fast
- Lightweight
- Cross-platform
- JavaScript everywhere
- Huge ecosystem

## Limitations

- Not ideal for CPU-intensive tasks

## Lab Exercises

1.  Create `hello.js` and print `Hello Node.js`.
2.  Create a program that prints your name.
3.  Display:
    - Node version
    - Operating system
    - Current directory

## Homework

1.  Install Node.js.
2.  Verify with `node -v` and `npm -v`.
3.  Create:
    - `hello.js`
    - `math.js`
    - `info.js`
4.  Run each program.

## Next Lesson

**Lesson 2: Setting Up a Node.js Project**

- Project structure
- package.json
- npm
- Installing packages
- Running scripts
