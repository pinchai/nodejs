# Lesson 3 – Node.js Core Modules

**Duration:** 2 Hours

## Learning Objectives

By the end of this lesson, students will be able to:

- Explain what Node.js Core Modules are.
- Import and use built-in modules.
- Read and write files using `fs`.
- Create a basic web server using `http`.
- Work with file paths using `path`.
- Retrieve operating system information using `os`.
- Generate hashes and random values using `crypto`.
- Parse URLs using `url`.
- Handle query strings using `querystring`.

---

# Lesson Outline

| Time | Topic |
|------|-------|
| 10 min | Introduction to Core Modules |
| 20 min | File System (`fs`) |
| 20 min | HTTP Server (`http`) |
| 15 min | Path Module (`path`) |
| 10 min | Operating System (`os`) |
| 15 min | Crypto Module (`crypto`) |
| 15 min | URL Module (`url`) |
| 15 min | Query String Module (`querystring`) |

---

# 1. Introduction to Core Modules

## What are Core Modules?

Core Modules are built into Node.js.

They do **NOT** require installation using npm.

```javascript
const fs = require('fs');
```

Unlike external packages:

```bash
npm install express
```

## Common Core Modules

| Module | Purpose |
|---------|----------|
| fs | File operations |
| http | Web server |
| path | File paths |
| os | Operating system info |
| crypto | Encryption & hashing |
| url | URL parsing |
| querystring | Query string parsing |

---

# 2. File System Module (fs)

## Read a File

```javascript
const fs = require('fs');

fs.readFile('message.txt', 'utf8', (err, data) => {
    if (err) return console.log(err);
    console.log(data);
});
```

## Write a File

```javascript
const fs = require('fs');

fs.writeFile('note.txt', 'Hello Node.js!', (err) => {
    if (err) return console.log(err);
    console.log('File created.');
});
```

## Append a File

```javascript
const fs = require('fs');

fs.appendFile('note.txt', '\nWelcome Students!', (err) => {
    if (err) throw err;
    console.log('Data appended.');
});
```

## Delete a File

```javascript
const fs = require('fs');

fs.unlink('note.txt', (err) => {
    if (err) throw err;
    console.log('Deleted');
});
```

### Exercise

- Create a file.
- Write your name.
- Append your student ID.
- Read the file.
- Delete the file.

---

# 3. HTTP Module

## Basic HTTP Server

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end('Hello Node.js');
});

server.listen(3000);

console.log('Server running on http://localhost:3000');
```

## Routing Example

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    if (req.url === '/') {
        res.end('Home Page');
    } else if (req.url === '/about') {
        res.end('About Page');
    } else {
        res.statusCode = 404;
        res.end('Page Not Found');
    }
});

server.listen(3000);
```

### Exercise

Create the following routes:

- /
- /about
- /contact
- /products

---

# 4. Path Module

```javascript
const path = require('path');

console.log(path.basename(__filename));
console.log(path.extname(__filename));
console.log(__dirname);

const file = path.join('public', 'images', 'logo.png');
console.log(file);
```

---

# 5. OS Module

```javascript
const os = require('os');

console.log(os.platform());
console.log(os.arch());
console.log(os.hostname());
console.log(os.cpus().length);
console.log(os.totalmem());
console.log(os.freemem());
```

### Exercise

Display:

- Computer name
- Platform
- CPU cores
- Total memory
- Free memory

---

# 6. Crypto Module

## SHA256 Hash

```javascript
const crypto = require('crypto');

const hash = crypto.createHash('sha256')
    .update('Hello Node')
    .digest('hex');

console.log(hash);
```

## Random UUID

```javascript
const crypto = require('crypto');

console.log(crypto.randomUUID());
```

## Random Token

```javascript
const crypto = require('crypto');

console.log(crypto.randomBytes(16).toString('hex'));
```

---

# 7. URL Module

```javascript
const myURL = new URL(
'http://localhost:3000/products?id=5&category=computer'
);

console.log(myURL.pathname);
console.log(myURL.searchParams.get('id'));
console.log(myURL.searchParams.get('category'));
```

---

# 8. Query String Module

## Parse Query

```javascript
const querystring = require('querystring');

const query = 'name=John&age=20&city=Phnom Penh';

console.log(querystring.parse(query));
```

## Stringify Object

```javascript
const querystring = require('querystring');

const data = {
    name: 'Alice',
    age: 25,
    city: 'Siem Reap'
};

console.log(querystring.stringify(data));
```

---

# Mini Project

Build a simple Node.js server that:

- Uses **http** to create a server.
- Uses **url** to read query parameters.
- Uses **querystring** to parse data.
- Uses **path** to display the current file path.
- Uses **os** to show system information.
- Uses **crypto** to generate a request ID.
- Uses **fs** to log each visitor into `visitors.txt`.

Example:

```
http://localhost:3000/?name=Alice
```

Expected response:

```
Welcome Alice!

Request ID:
xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

Platform:
win32

Current File:
server.js
```

---

# Summary

| Module | Main Purpose | Common Functions |
|---------|--------------|------------------|
| fs | File operations | readFile(), writeFile(), appendFile(), unlink() |
| http | Web server | createServer(), listen() |
| path | File paths | join(), basename(), extname() |
| os | System information | platform(), cpus(), freemem() |
| crypto | Security | createHash(), randomUUID(), randomBytes() |
| url | URL parsing | URL(), searchParams |
| querystring | Query parsing | parse(), stringify() |

---

# Homework

Create a **Student Information Server**.

1. Create an HTTP server on port **3000**.
2. Read:

```
http://localhost:3000/student?name=John&id=1001
```

3. Display:

```
Student Name : John
Student ID   : 1001
```

4. Generate a random request ID using `crypto.randomUUID()`.
5. Save every request to `logs.txt` using `fs`.
6. Display operating system information using the `os` module.
