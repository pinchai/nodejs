# Node.js Query String Module

The Node.js **`querystring` module** provides utilities for working with URL query strings, such as converting between a query string and a JavaScript object.

> **Note:** For modern Node.js applications, the **`URLSearchParams`** API is generally preferred. The `querystring` module is considered legacy, but it is still available.

## 1. Import the Module

### CommonJS

```js
const querystring = require('node:querystring');
```

### ES Modules

```js
import querystring from 'node:querystring';
```

## 2. `querystring.parse()`

Converts a query string into an object.

```js
const querystring = require('node:querystring');

const result = querystring.parse('name=chai&age=25&city=Phnom%20Penh');

console.log(result);
```

Output:

```js
{
  name: 'chai',
  age: '25',
  city: 'Phnom Penh'
}
```

### Example

```js
const query = 'username=admin&password=1234';

const data = querystring.parse(query);

console.log(data.username);
console.log(data.password);
```

Output:

```text
admin
1234
```

## 3. `querystring.stringify()`

Converts an object into a query string.

```js
const querystring = require('node:querystring');

const data = {
  name: 'chai',
  age: 25,
  city: 'Phnom Penh'
};

const query = querystring.stringify(data);

console.log(query);
```

Output:

```text
name=chai&age=25&city=Phnom%20Penh
```

## 4. `querystring.escape()`

Encodes a string so it can safely be used in a URL query string.

```js
const querystring = require('node:querystring');

const text = 'Hello World & Node.js';

console.log(querystring.escape(text));
```

Output:

```text
Hello%20World%20%26%20Node.js
```

## 5. `querystring.unescape()`

Decodes an encoded query-string value.

```js
const querystring = require('node:querystring');

const text = 'Hello%20World%20%26%20Node.js';

console.log(querystring.unescape(text));
```

Output:

```text
Hello World & Node.js
```

## 6. Handling Multiple Values

A query string can contain the same key multiple times:

```js
const querystring = require('node:querystring');

const result = querystring.parse(
  'category=nodejs&category=mongodb&category=express'
);

console.log(result);
```

Output:

```js
{
  category: [ 'nodejs', 'mongodb', 'express' ]
}
```

This is useful for query strings such as:

```text
?category=nodejs&category=mongodb
```

## 7. Custom Separator

By default:

- `&` separates parameters
- `=` separates key and value

You can customize them.

```js
const querystring = require('node:querystring');

const result = querystring.parse(
  'name:chai;age:25',
  ';',
  ':'
);

console.log(result);
```

Output:

```js
{
  name: 'chai',
  age: '25'
}
```

## Common Methods

| Method | Purpose |
|---|---|
| `querystring.parse()` | Query string → Object |
| `querystring.stringify()` | Object → Query string |
| `querystring.escape()` | Encode a string |
| `querystring.unescape()` | Decode a string |

## Practical Example with HTTP Server

```js
const http = require('node:http');
const querystring = require('node:querystring');

const server = http.createServer((req, res) => {

  const query = req.url.split('?')[1];

  if (query) {
    const params = querystring.parse(query);

    console.log(params);

    res.end(`Hello ${params.name}`);
  } else {
    res.end('No query parameters');
  }
});

server.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

Request:

```text
http://localhost:3000/?name=Chai&age=25
```

The parsed object will be:

```js
{
  name: 'Chai',
  age: '25'
}
```

And the response:

```text
Hello Chai
```

## `querystring` vs `URLSearchParams`

For **new Node.js code**, prefer:

```js
const params = new URLSearchParams(
  'name=Chai&age=25'
);

console.log(params.get('name'));
console.log(params.get('age'));
```

`URLSearchParams` integrates naturally with the modern `URL` API and is usually the better choice for new applications.
