# Pre-Lesson: Web, HTTP & Client–Server Basics

## 1. Learning Objectives

After this pre-lesson, students should understand:

- What a web application is
- What a server and client are
- What HTTP is
- What a URL is
- What an HTTP request is
- What an HTTP response is
- HTTP methods: `GET`, `POST`, `PUT`, `PATCH`, `DELETE`
- HTTP status codes
- Headers and body
- The basic request → response cycle

---

## 2. What is a Web Application?

A **web application** is an application that communicates between a **client** and a **server** over a network.

```text
Browser
   |
   | HTTP Request
   ↓
Web Server
   |
   | HTTP Response
   ↓
Browser
```

Examples of clients:

- Chrome
- Firefox
- Edge
- Mobile applications
- Frontend applications such as Angular, Vue, or React

Examples of servers:

- Node.js
- Flask
- Laravel
- Django
- Express.js

---

## 3. Client vs Server

### Client

The **client** sends requests to a server.

```text
Browser → Request → Server
```

### Server

The **server** receives requests, processes them, and sends responses.

```text
Server → Response → Browser
```

Example:

```text
Client:
"Give me the list of products."

Server:
"Here are the products."
```

---

## 4. What is HTTP?

**HTTP = HyperText Transfer Protocol**

HTTP is a protocol used for communication between clients and servers.

```text
Client
   |
   | HTTP
   ↓
Server
```

When you visit:

```text
https://example.com
```

your browser sends an HTTP request to the server.

The server sends an HTTP response back.

---

## 5. What is a URL?

A URL identifies a resource on a server.

Example:

```text
https://example.com/products/10
```

Break it down:

```text
https://
   ↓
Protocol

example.com
   ↓
Domain

/products/10
   ↓
Path
```

Another example:

```text
http://localhost:3000/products
```

```text
http://       → protocol
localhost     → host
3000          → port
/products     → path
```

---

## 6. HTTP Request

An HTTP request is a message sent from the client to the server.

Example:

```http
GET /products HTTP/1.1
Host: example.com
```

A request can contain:

```text
Method
URL
Headers
Body
```

For example:

```text
GET
/products
Authorization: Bearer xxx
```

---

## 7. HTTP Methods

Students should understand these before learning Node.js's HTTP module.

| Method | Purpose |
| --- | --- |
| GET | Get data |
| POST | Create data |
| PUT | Replace/update data |
| PATCH | Partially update data |
| DELETE | Delete data |

### GET

```http
GET /products
```

Means:

> Give me the products.

### POST

```http
POST /products
```

Means:

> Create a new product.

### DELETE

```http
DELETE /products/10
```

Means:

> Delete product 10.

---

## 8. HTTP Response

After receiving a request, the server sends a response.

Example:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": 1,
    "name": "Laptop"
}
```

A response normally contains:

```text
Status Code
Headers
Body
```

---

## 9. HTTP Status Codes

Students should know the basic status codes.

### 2xx — Success

```text
200 OK
201 Created
204 No Content
```

Example:

```text
GET /products
        ↓
200 OK
```

### 4xx — Client Error

```text
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
```

Example:

```text
GET /product/999
        ↓
404 Not Found
```

### 5xx — Server Error

```text
500 Internal Server Error
502 Bad Gateway
503 Service Unavailable
```

Example:

```text
Server has an unexpected error
        ↓
500 Internal Server Error
```

A useful summary:

```text
HTTP Status Codes

2xx → Success
3xx → Redirection
4xx → Client Error
5xx → Server Error
```

---

## 10. Request and Response

This is the **most important concept** before learning the Node.js HTTP Module.

```text
             HTTP Request
Client  ------------------------>  Server
        GET /products

             HTTP Response
Client  <------------------------  Server
        200 OK
        [products]
```

Students should understand that **Node.js HTTP Module can create both servers and HTTP clients**.

---

## 11. Simple Real-World Example

Imagine a restaurant.

```text
Customer = Client

Waiter = HTTP

Kitchen = Server
```

Customer asks:

```text
"I want fried rice."
```

This is similar to:

```http
GET /fried-rice
```

The kitchen processes the request.

The waiter returns:

```text
"Here is your fried rice."
```

This is similar to an HTTP response.

---

## 12. Mini Practice Before HTTP Module

### Question 1

What is HTTP?

### Question 2

What is the difference between a client and a server?

### Question 3

What does `GET` do?

### Question 4

What does `POST` do?

### Question 5

What does status code `200` mean?

### Question 6

What does status code `404` mean?

### Question 7

What does status code `500` mean?

### Question 8

What are the main parts of an HTTP request?

### Question 9

What are the main parts of an HTTP response?

### Question 10

Explain this flow:

```text
Browser → HTTP Request → Server
Browser ← HTTP Response ← Server
```

---

# Recommended Lesson Sequence

For learning Node.js HTTP, use this sequence:

```text
Pre-Lesson
   ↓
Client / Server
   ↓
HTTP
   ↓
Request / Response
   ↓
HTTP Methods
   ↓
HTTP Status Codes
   ↓
URL / Headers / Body
   ↓
Node.js HTTP Module
   ↓
http.createServer()
   ↓
req
   ↓
res
   ↓
Routing
   ↓
HTTP Client
   ↓
GET API
   ↓
POST API
   ↓
Mini REST API
```
