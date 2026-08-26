# Node.js with Argon2

Argon2 is a modern password-hashing algorithm designed to make password cracking expensive. For new applications, **Argon2id** is a strong choice.

## 1. Install Argon2

```bash
npm install argon2
```

## 2. Hash a Password

```js
const argon2 = require("argon2");

async function hashPassword(password) {
    const hash = await argon2.hash(password, {
        type: argon2.argon2id
    });

    return hash;
}

const hash = await hashPassword("MyPassword123!");

console.log(hash);
```

An Argon2id hash looks roughly like:

```text
$argon2id$v=19$m=65536,t=3,p=4$...
```

Store the **entire hash string** in your database. Argon2 handles the salt as part of the encoded hash.

## 3. Verify a Password

```js
const argon2 = require("argon2");

async function verifyPassword(password, hash) {
    return await argon2.verify(hash, password);
}

const isValid = await verifyPassword(
    "MyPassword123!",
    hash
);

console.log(isValid); // true
```

### Login Example

```js
const isValid = await argon2.verify(
    user.password_hash,
    password
);

if (!isValid) {
    return res.status(401).json({
        message: "Invalid email or password"
    });
}

console.log("Login successful");
```

## 4. Configure Argon2id

You can explicitly configure Argon2id:

```js
const hash = await argon2.hash(password, {
    type: argon2.argon2id,
    memoryCost: 65536, // 64 MB
    timeCost: 3,
    parallelism: 4
});
```

There is no single configuration that is ideal for every server. Benchmark your application and choose parameters that make password verification sufficiently expensive without causing excessive server load.

## 5. Password Expiration

Argon2 itself does **not** provide password expiration.

Instead, store the date when the password was changed:

```sql
CREATE TABLE users (
    id INT PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    password_changed_at TIMESTAMP NOT NULL
);
```

Then check the password age in Node.js:

```js
const passwordAge =
    Date.now() - new Date(user.password_changed_at).getTime();

const maxAge = 90 * 24 * 60 * 60 * 1000;

if (passwordAge > maxAge) {
    // Require the user to change their password
}
```

## 6. Recommended Database Design

A typical user table can contain:

```text
users
├── id
├── email
├── password_hash
└── password_changed_at
```

The authentication flow is:

```text
User Password
     │
     ▼
   Argon2id
     │
     ▼
password_hash
     │
     ▼
   Database
     │
     └── password_changed_at
             │
             ▼
      Password expiration
```

## 7. Important Security Notes

- Use **Argon2id** for password hashing.
- Never store plain-text passwords.
- Never decrypt or attempt to recover an Argon2 password.
- Store the complete Argon2 hash returned by `argon2.hash()`.
- Use `argon2.verify()` to check passwords.
- Use a database field such as `password_changed_at` for password expiration.
- Choose Argon2 parameters based on benchmarking on your production hardware.
- Use HTTPS for login requests.
- Consider rate limiting login attempts.
- Do not log passwords or password hashes.

## Complete Example

```js
const argon2 = require("argon2");

async function registerUser(password) {
    const passwordHash = await argon2.hash(password, {
        type: argon2.argon2id
    });

    return {
        password_hash: passwordHash,
        password_changed_at: new Date()
    };
}

async function loginUser(password, passwordHash) {
    const isValid = await argon2.verify(
        passwordHash,
        password
    );

    if (!isValid) {
        throw new Error("Invalid password");
    }

    return true;
}
```

## Summary

| Feature | Argon2 |
|---|---|
| Password hashing | Yes |
| Argon2id | Yes |
| Salt handling | Built in |
| Password verification | Yes |
| Password encryption | No |
| Password expiration | No, implement separately |
| Plain-text password recovery | No |

Argon2id is a strong modern choice for storing passwords in Node.js applications.
