# HTTP (HyperText Transfer Protocol)

> *"HTTP is the foundation of communication on the World Wide Web. It defines how clients and servers exchange requests and responses."*

---

# Table of Contents

* What is HTTP?
* HTTP Architecture
* HTTP Request–Response Cycle
* HTTP Methods
* HTTP Status Codes
* HTTP Headers
* Stateless Nature
* Cookies & Sessions
* Advantages & Limitations
* Interview Questions
* Quick Revision

---

# What is HTTP?

**HTTP (HyperText Transfer Protocol)** is an **Application Layer protocol** used for communication between a **client** (browser/mobile app) and a **server**.

It follows a **request-response model**, where:

* Client sends a request.
* Server processes it.
* Server returns a response.

Example:

```text
Browser  ───────►  Web Server
        Request

Browser  ◄───────  Web Server
        Response
```

HTTP is the protocol behind:

* Websites
* REST APIs
* Mobile Apps
* Cloud Applications

---

# HTTP Architecture

```text
Client
   │
   ▼
Internet
   │
   ▼
Web Server
   │
   ▼
Database
```

The client never communicates directly with the database—it always goes through the server.

---

# HTTP Request–Response Cycle

```text
1. User enters URL
        │
2. Browser sends HTTP Request
        │
3. Server processes request
        │
4. Server queries database (if needed)
        │
5. Server sends HTTP Response
        │
6. Browser displays webpage
```

---

# HTTP Methods

| Method  | Purpose               | Idempotent |
| ------- | --------------------- | ---------- |
| GET     | Retrieve data         | ✅          |
| POST    | Create resource       | ❌          |
| PUT     | Replace resource      | ✅          |
| PATCH   | Update resource       | ❌          |
| DELETE  | Delete resource       | ✅          |
| HEAD    | Retrieve headers only | ✅          |
| OPTIONS | Supported operations  | ✅          |

### Example

```http
GET /users/101 HTTP/1.1
```

---

# HTTP Request Structure

```http
GET /users HTTP/1.1
Host: example.com
Authorization: Bearer token

Request Body (Optional)
```

Components:

* Request Line
* Headers
* Body (Optional)

---

# HTTP Response Structure

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "name":"John"
}
```

Components:

* Status Line
* Headers
* Body

---

# HTTP Status Codes

### 1xx – Informational

```text
100 Continue
```

---

### 2xx – Success

```text
200 OK
201 Created
204 No Content
```

---

### 3xx – Redirection

```text
301 Moved Permanently
302 Found
304 Not Modified
```

---

### 4xx – Client Errors

```text
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
429 Too Many Requests
```

---

### 5xx – Server Errors

```text
500 Internal Server Error
502 Bad Gateway
503 Service Unavailable
504 Gateway Timeout
```

---

# HTTP Headers

Headers provide additional information about requests and responses.

Common Request Headers:

```text
Host
Authorization
Content-Type
Accept
User-Agent
Cookie
```

Common Response Headers:

```text
Content-Type
Content-Length
Cache-Control
Set-Cookie
Server
```

---

# Stateless Nature

HTTP is **stateless**.

This means each request is independent.

```text
Request 1

↓

Server Responds

↓

Connection Ends

↓

Request 2

↓

Server Doesn't Remember Request 1
```

Because of this, HTTP uses:

* Cookies
* Sessions
* JWT Tokens

to maintain user state.

---

# Cookies & Sessions

## Cookie

Stored in the browser.

Example:

```text
SessionID=abc123
```

Sent with every request.

---

## Session

Stored on the server.

```text
Browser

↓

Cookie

↓

Server

↓

Session Data
```

Sessions help identify logged-in users.

---

# Advantages

* Simple
* Widely Supported
* Stateless
* Flexible
* Platform Independent

---

# Limitations

* Stateless by default
* Plain HTTP is not encrypted
* Higher latency due to request-response communication
* Requires HTTPS for secure communication

---

# Real-World Example

Opening:

```text
https://www.google.com
```

Flow:

```text
Browser
   │
HTTP Request
   │
Google Server
   │
HTTP Response
   │
Browser Renders Page
```

---

# Interview Questions

* What is HTTP?
* Why is HTTP stateless?
* Difference between GET and POST?
* Difference between PUT and PATCH?
* What are HTTP headers?
* Explain HTTP request-response cycle.
* What are cookies and sessions?
* Explain HTTP status codes.

---

# Quick Revision

```text
HTTP

Application Layer

↓

Request → Response

Methods

GET
POST
PUT
PATCH
DELETE

Status Codes

2xx Success

3xx Redirect

4xx Client Error

5xx Server Error

Stateless

Uses Cookies & Sessions
```

---

# Key Takeaways

* HTTP is an **Application Layer protocol** used for client-server communication.
* It follows a **request-response** architecture.
* HTTP is **stateless**, so cookies, sessions, or tokens are used to maintain user state.
* Common methods include **GET, POST, PUT, PATCH, and DELETE**.
* Status codes indicate the outcome of a request.
* HTTP forms the foundation of web applications and REST APIs.

---

> **Next Topic:** `05-HTTPS.md`
