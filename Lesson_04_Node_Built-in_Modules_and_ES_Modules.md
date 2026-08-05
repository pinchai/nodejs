# Node.js Built-in Modules and ES Modules

## Do Node.js built-in modules use ES Modules?

Yes. **Node.js built-in modules fully support ES Modules.**

Many examples use the `node:` prefix because it identifies the module as
a built-in Node.js module. It is **not** an alternative to ES Modules.

------------------------------------------------------------------------

## CommonJS (Older Style)

``` javascript
const fs = require("fs");
const path = require("path");
```

------------------------------------------------------------------------

## ES Modules (Modern Style)

``` javascript
import fs from "node:fs";
import path from "node:path";
```

Or import only what you need:

``` javascript
import { readFile } from "node:fs/promises";
```

------------------------------------------------------------------------

## Why use the `node:` prefix?

Example:

``` javascript
import fs from "node:fs";
```

instead of

``` javascript
import fs from "fs";
```

Both work, but `node:` is recommended because it:

-   Makes it clear the module is built into Node.js.
-   Prevents confusion with third-party packages that have the same
    name.
-   Matches modern Node.js documentation.

------------------------------------------------------------------------

## Examples

### Reading a file

``` javascript
import { readFile } from "node:fs/promises";

const data = await readFile("test.txt", "utf8");
console.log(data);
```

### Creating an HTTP server

``` javascript
import http from "node:http";

const server = http.createServer((req, res) => {
    res.end("Hello Node!");
});

server.listen(3000);
```

### Using the `path` module

``` javascript
import path from "node:path";

console.log(path.basename("/home/user/test.txt"));
```

------------------------------------------------------------------------

## Why do many tutorials still use `require()`?

Because:

-   Node.js originally used CommonJS.
-   Many existing projects still use CommonJS.
-   Older tutorials have not been updated.
-   Some older npm packages were designed around CommonJS.

------------------------------------------------------------------------

## Recommendation for New Node.js and Express Projects

Use **ES Modules**.

### package.json

``` json
{
  "type": "module"
}
```

### app.js

``` javascript
import express from "express";
import fs from "node:fs/promises";
import path from "node:path";

const app = express();

app.listen(3000, () => {
    console.log("Server running");
});
```

------------------------------------------------------------------------

## Best Practice

When learning modern Node.js and Express.js:

-   Use `import` and `export`.
-   Set `"type": "module"` in `package.json`.
-   Import built-in modules using the `node:` prefix (for example,
    `node:fs`, `node:path`, and `node:http`).

This approach follows current Node.js best practices and prepares you
for modern Express.js development.
