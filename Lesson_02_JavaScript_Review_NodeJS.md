# Lesson 02: JavaScript Review (for Node.js)

> **Course:** Node.js for Beginners  
> **Lesson:** 02 – JavaScript Review  
> **Duration:** 2–3 Hours

## Learning Objectives

After completing this lesson, students will be able to:

- Understand modern JavaScript (ES6+) syntax
- Declare variables correctly
- Use different data types
- Work with operators
- Make decisions using conditions
- Repeat tasks using loops
- Create and use functions
- Work with arrays and objects
- Understand scope
- Use template literals
- Use destructuring
- Use the spread operator
- Understand modules (import/export)
- Prepare for asynchronous programming

---

# Why Review JavaScript?

Node.js **uses JavaScript** as its programming language.

Before learning Node.js APIs such as:

- File System (fs)
- HTTP Server
- Path
- Events
- Streams

Students must be comfortable with JavaScript.

---

# 1. Variables

## var

```javascript
var name = "John";
```

## let

```javascript
let age = 20;
```

```javascript
let score = 80;
score = 90;
console.log(score);
```

Output

```text
90
```

## const

```javascript
const PI = 3.14;
```

```javascript
const PI = 3.14;
PI = 5;
```

Output

```text
TypeError
```

| Keyword | Can Change? | Scope |
|---------|-------------|-------|
| var | Yes | Function |
| let | Yes | Block |
| const | No | Block |

Recommended:

- Use **const** by default
- Use **let** when value changes
- Avoid **var**

---

# 2. Data Types

## Primitive

```javascript
let name = "Alice";
let age = 20;
let price = 9.99;
let active = true;
let data = null;
let value;
let id = Symbol();
let big = 12345678901234567890n;
```

## Reference

```javascript
const student = { name: "Alice", age: 20 };
const numbers = [10,20,30];
function hello(){}
```

## typeof

```javascript
console.log(typeof "Hello");
console.log(typeof 100);
console.log(typeof true);
console.log(typeof {});
console.log(typeof []);
```

Output:

```text
string
number
boolean
object
object
```

---

# 3. Operators

## Arithmetic

```javascript
let a = 10;
let b = 5;

console.log(a + b);
console.log(a - b);
console.log(a * b);
console.log(a / b);
console.log(a % b);
```

## Comparison

```javascript
10 > 5
10 < 5
10 >= 5
10 <= 5
10 == "10"
10 === "10"
```

Always prefer `===`.

## Logical

```javascript
&&
||
!
```

---

# 4. Condition Statements

```javascript
if(score >= 50){
    console.log("Pass");
}else{
    console.log("Fail");
}
```

```javascript
switch(day){
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    default:
        console.log("Unknown");
}
```

---

# 5. Loops

```javascript
for(let i=1;i<=5;i++){
    console.log(i);
}
```

```javascript
while(i<=5){
    console.log(i);
    i++;
}
```

```javascript
do{
    console.log(i);
    i++;
}while(i<=5);
```

```javascript
for(const item of fruits){
    console.log(item);
}
```

```javascript
for(const key in student){
    console.log(key, student[key]);
}
```

---

# 6. Functions

```javascript
function add(a,b){
    return a+b;
}
```

```javascript
const add = function(a,b){
    return a+b;
};
```

```javascript
const add = (a,b)=>a+b;
```

---

# 7. Scope

- Global Scope
- Function Scope
- Block Scope

---

# 8. Arrays

```javascript
const fruits = ["Apple","Orange","Banana"];
```

Useful methods:

- push()
- pop()
- shift()
- unshift()
- includes()
- indexOf()
- forEach()
- map()
- filter()
- find()

---

# 9. Objects

```javascript
const student = {
    name: "John",
    age: 20,
    city: "New York"
};
```

---

# 10. Template Literals

```javascript
console.log(`Hello ${name}`);
```

---

# 11. Destructuring

```javascript
const [a,b,c] = colors;
```

```javascript
const {name, age} = student;
```

---

# 12. Spread Operator

```javascript
const b = [...a,3,4];
```

```javascript
const student = {
    ...user,
    age:20
};
```

---

# 13. Rest Parameters

```javascript
function total(...numbers){
    return numbers.reduce((a,b)=>a+b);
}
```

---

# 14. ES Modules

**math.js**

```javascript
export function add(a,b){
    return a+b;
}
```

**app.js**

```javascript
import { add } from "./math.js";
console.log(add(5,3));
```

---

# 15. Introduction to Asynchronous JavaScript

```javascript
console.log("Start");

setTimeout(()=>{
    console.log("Finish");
},2000);

console.log("End");
```

Output

```text
Start
End
Finish
```

---

# Summary

- Variables
- Data Types
- Operators
- Conditions
- Loops
- Functions
- Scope
- Arrays
- Objects
- Template Literals
- Destructuring
- Spread & Rest Operators
- ES Modules
- Asynchronous JavaScript

---

# Practice Exercises

1. Create a program that stores your personal information in an object and displays it using template literals.
2. Write a function that calculates the average of an array of numbers.
3. Use `filter()` to create a new array containing only numbers greater than 50.
4. Use `map()` to convert an array of lowercase names to uppercase.
5. Write a program that uses `setTimeout()` to display `"Hello Node.js!"` after 3 seconds.
6. Create two modules: `math.js` (exports `add` and `subtract`) and `app.js` (imports and uses them).
