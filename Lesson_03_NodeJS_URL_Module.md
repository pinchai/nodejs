# Node.js URL Module

The **`url` module** in Node.js provides utilities for parsing, constructing, and manipulating URLs. In modern Node.js, the standard **WHATWG `URL` API** is recommended over the older legacy API.

## Importing the URL module

```javascript
const url = require('url'); // CommonJS

// OR (ES Modules)
import { URL } from 'node:url';
```

## 1. Creating a URL object

```javascript
const { URL } = require('url');

const myUrl = new URL(
  'https://example.com:8080/path/page?name=John&age=25#section'
);

console.log(myUrl);
```

## 2. Accessing URL properties

```javascript
const { URL } = require('url');

const myUrl = new URL(
  'https://example.com:8080/path/page?name=John&age=25#section'
);

console.log(myUrl.href);       // Full URL
console.log(myUrl.protocol);   // https:
console.log(myUrl.hostname);   // example.com
console.log(myUrl.port);       // 8080
console.log(myUrl.pathname);   // /path/page
console.log(myUrl.search);     // ?name=John&age=25
console.log(myUrl.hash);       // #section
```

### Output

```text
https://example.com:8080/path/page?name=John&age=25#section
https:
example.com
8080
/path/page
?name=John&age=25
#section
```

## 3. Reading query parameters

```javascript
const { URL } = require('url');

const myUrl = new URL('https://example.com?name=John&age=25');

console.log(myUrl.searchParams.get('name')); // John
console.log(myUrl.searchParams.get('age'));  // 25
```

## 4. Adding query parameters

```javascript
const { URL } = require('url');

const myUrl = new URL('https://example.com');

myUrl.searchParams.append('city', 'London');
myUrl.searchParams.append('country', 'UK');

console.log(myUrl.href);
```

### Output

```text
https://example.com/?city=London&country=UK
```

## 5. Updating query parameters

```javascript
myUrl.searchParams.set('city', 'New York');

console.log(myUrl.href);
```

### Output

```text
https://example.com/?city=New+York&country=UK
```

## 6. Deleting query parameters

```javascript
myUrl.searchParams.delete('country');

console.log(myUrl.href);
```

### Output

```text
https://example.com/?city=New+York
```

## 7. Creating a URL from a base URL

```javascript
const { URL } = require('url');

const myUrl = new URL('/about', 'https://example.com');

console.log(myUrl.href);
```

### Output

```text
https://example.com/about
```

## 8. Legacy `url.parse()` API

Although still available, `url.parse()` is considered a legacy API.

```javascript
const url = require('url');

const myUrl = url.parse(
  'https://example.com/path?page=1',
  true
);

console.log(myUrl.hostname);  // example.com
console.log(myUrl.pathname);  // /path
console.log(myUrl.query);     // { page: '1' }
```

## Common URL Methods and Properties

| Method/Property | Description |
|---|---|
| `new URL(url)` | Creates a URL object |
| `href` | Complete URL |
| `protocol` | URL protocol (`http:`, `https:`) |
| `hostname` | Domain name |
| `port` | Port number |
| `pathname` | Path part of the URL |
| `search` | Query string |
| `hash` | Fragment identifier |
| `searchParams.get()` | Get a query parameter |
| `searchParams.set()` | Update a query parameter |
| `searchParams.append()` | Add a query parameter |
| `searchParams.delete()` | Remove a query parameter |

## Summary

- Use the **WHATWG `URL` class** (`new URL()`) for new Node.js applications.
- Use `searchParams` to easily read and modify query parameters.
- Avoid the legacy `url.parse()` API unless maintaining older code.
