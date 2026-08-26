# Node.js OS Module

The **`os` module** in **Node.js** is a built-in module that provides information about the operating system. You don't need to install it—just import it into your project.

## Importing the `os` Module

### CommonJS

```javascript
const os = require("os");
```

### ES Modules

```javascript
import os from "os";
```

## Commonly Used Methods

| Method | Description |
|---|---|
| `os.platform()` | Returns the operating system platform |
| `os.arch()` | Returns CPU architecture |
| `os.cpus()` | Returns information about each CPU/core |
| `os.hostname()` | Returns the computer's hostname |
| `os.homedir()` | Returns the user's home directory |
| `os.tmpdir()` | Returns the system temporary directory |
| `os.freemem()` | Returns free memory in bytes |
| `os.totalmem()` | Returns total memory in bytes |
| `os.uptime()` | Returns system uptime in seconds |
| `os.userInfo()` | Returns information about the current user |
| `os.networkInterfaces()` | Returns network interface details |
| `os.type()` | Returns the OS name |
| `os.release()` | Returns the OS version |
| `os.endianness()` | Returns CPU byte order (`BE` or `LE`) |

## Examples

### 1. Operating System Platform

```javascript
const os = require("os");

console.log(os.platform());
```

Windows:

```text
win32
```

Linux:

```text
linux
```

macOS:

```text
darwin
```

### 2. CPU Architecture

```javascript
console.log(os.arch());
```

Example:

```text
x64
```

### 3. Total and Free Memory

```javascript
console.log("Total Memory:", os.totalmem());
console.log("Free Memory:", os.freemem());
```

Display memory in GB:

```javascript
console.log(
  "Total Memory:",
  (os.totalmem() / 1024 / 1024 / 1024).toFixed(2),
  "GB"
);
```

### 4. Home Directory

```javascript
console.log(os.homedir());
```

Example:

```text
C:\Users\John
```

or:

```text
/home/john
```

### 5. Hostname

```javascript
console.log(os.hostname());
```

Example:

```text
DESKTOP-ABCD123
```

### 6. User Information

```javascript
console.log(os.userInfo());
```

Example:

```javascript
{
  uid: -1,
  gid: -1,
  username: "John",
  homedir: "C:\\Users\\John",
  shell: null
}
```

### 7. CPU Information

```javascript
console.log(os.cpus());
```

The result contains information about each CPU/core.

To get the number of CPU cores:

```javascript
console.log(os.cpus().length);
```

### 8. System Uptime

```javascript
console.log(os.uptime());
```

Example:

```text
3600
```

This means the system has been running for **3600 seconds (1 hour)**.

### 9. Network Interfaces

```javascript
console.log(os.networkInterfaces());
```

This returns details of network adapters and their IP addresses.

### 10. Temporary Directory

```javascript
console.log(os.tmpdir());
```

Example:

```text
C:\Users\John\AppData\Local\Temp
```

## Complete Example

```javascript
const os = require("os");

console.log("Platform:", os.platform());
console.log("Architecture:", os.arch());
console.log("Hostname:", os.hostname());
console.log("Home Directory:", os.homedir());
console.log("CPU Cores:", os.cpus().length);
console.log("OS Type:", os.type());
console.log("OS Release:", os.release());

console.log(
  "Total Memory:",
  (os.totalmem() / 1024 / 1024 / 1024).toFixed(2),
  "GB"
);

console.log(
  "Free Memory:",
  (os.freemem() / 1024 / 1024 / 1024).toFixed(2),
  "GB"
);

console.log("System Uptime:", os.uptime(), "seconds");
```

### Sample Output

```text
Platform: win32
Architecture: x64
Hostname: DESKTOP-ABCD123
Home Directory: C:\Users\John
CPU Cores: 8
OS Type: Windows_NT
OS Release: 10.0.22631
Total Memory: 16.00 GB
Free Memory: 7.42 GB
System Uptime: 84520 seconds
```

## When to Use the `os` Module

The `os` module is useful for:

- Displaying system information in CLI applications.
- Checking available memory before memory-intensive tasks.
- Detecting the operating system for cross-platform applications.
- Getting the current user's home directory.
- Getting the system temporary directory.
- Inspecting CPU information.
- Inspecting network interface information.
- Building system monitoring and diagnostic tools.

## Key Takeaway

The Node.js `os` module gives your application access to useful information about the operating system and computer hardware without requiring an external package.

```javascript
const os = require("os");

console.log(os.platform());
console.log(os.arch());
console.log(os.cpus().length);
console.log(os.totalmem());
console.log(os.freemem());
```
