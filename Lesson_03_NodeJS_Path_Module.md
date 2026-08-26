# Node.js Path Module

The **Node.js `path` module** is a built-in module that provides utilities for working with file and directory paths. It helps create, manipulate, and normalize file paths in a way that works across different operating systems.

## Importing the Path Module

### CommonJS

```javascript
const path = require('path');
```

### ES Modules

```javascript
import path from 'path';
```

## Commonly Used Methods

### 1. `path.join()`

Joins path segments using the correct platform-specific separator.

```javascript
const path = require('path');

const filePath = path.join('folder', 'subfolder', 'file.txt');
console.log(filePath);
```

**Windows:**
```text
folder\subfolder\file.txt
```

**Linux/macOS:**
```text
folder/subfolder/file.txt
```

### 2. `path.resolve()`

Creates an absolute path.

```javascript
const path = require('path');

console.log(path.resolve('files', 'notes.txt'));
```

Example:

```text
C:\Users\John\project\files\notes.txt
```

or:

```text
/home/john/project/files/notes.txt
```

### 3. `path.basename()`

Returns the last portion (file name) of a path.

```javascript
const path = require('path');

console.log(path.basename('/users/admin/report.pdf'));
```

Output:

```text
report.pdf
```

Without the extension:

```javascript
console.log(path.basename('/users/admin/report.pdf', '.pdf'));
```

Output:

```text
report
```

### 4. `path.dirname()`

Returns the directory name.

```javascript
const path = require('path');

console.log(path.dirname('/users/admin/report.pdf'));
```

Output:

```text
/users/admin
```

### 5. `path.extname()`

Returns the file extension.

```javascript
const path = require('path');

console.log(path.extname('image.png'));
```

Output:

```text
.png
```

### 6. `path.parse()`

Converts a path into an object.

```javascript
const path = require('path');

console.log(path.parse('/users/admin/file.txt'));
```

Output:

```javascript
{
  root: '/',
  dir: '/users/admin',
  base: 'file.txt',
  ext: '.txt',
  name: 'file'
}
```

### 7. `path.format()`

Creates a path string from an object.

```javascript
const path = require('path');

const obj = {
  dir: '/users/admin',
  base: 'file.txt'
};

console.log(path.format(obj));
```

Output:

```text
/users/admin/file.txt
```

### 8. `path.normalize()`

Removes unnecessary separators and resolves `.` and `..`.

```javascript
const path = require('path');

console.log(path.normalize('/users//admin/../docs/file.txt'));
```

Output:

```text
/users/docs/file.txt
```

### 9. `path.isAbsolute()`

Checks whether a path is absolute.

```javascript
const path = require('path');

console.log(path.isAbsolute('/users/admin'));
```

Output:

```text
true
```

```javascript
console.log(path.isAbsolute('documents/file.txt'));
```

Output:

```text
false
```

## Useful Properties

### `path.sep`

Returns the platform-specific path separator.

```javascript
const path = require('path');

console.log(path.sep);
```

- Windows: `\`
- Linux/macOS: `/`

### `path.delimiter`

Returns the delimiter used in the system `PATH` environment variable.

```javascript
const path = require('path');

console.log(path.delimiter);
```

- Windows: `;`
- Linux/macOS: `:`

## Example: Building a File Path

```javascript
const path = require('path');

const uploadPath = path.join(__dirname, 'uploads', 'photo.jpg');

console.log(uploadPath);
```

If your project is:

```text
project/
│── app.js
│── uploads/
│   └── photo.jpg
```

The output might be:

```text
C:\project\uploads\photo.jpg
```

or:

```text
/home/user/project/uploads/photo.jpg
```

## Summary

| Method / Property | Purpose |
|---|---|
| `path.join()` | Join path segments safely |
| `path.resolve()` | Create an absolute path |
| `path.basename()` | Get the file name |
| `path.dirname()` | Get the directory path |
| `path.extname()` | Get the file extension |
| `path.parse()` | Convert a path into an object |
| `path.format()` | Convert a path object into a string |
| `path.normalize()` | Clean up a path |
| `path.isAbsolute()` | Check if a path is absolute |
| `path.sep` | Platform-specific path separator |
| `path.delimiter` | `PATH` environment variable delimiter |

The `path` module is especially useful when working with the Node.js `fs` (File System) module because it lets you build and manipulate file paths in a portable, cross-platform way.
