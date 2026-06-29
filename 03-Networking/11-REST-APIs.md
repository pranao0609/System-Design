# REST APIs (Representational State Transfer)

> *"REST (Representational State Transfer) is an architectural style for designing web APIs that enables communication between clients and servers using standard HTTP methods."*

---

# Table of Contents

* What is REST?
* What is an API?
* REST Architecture
* REST Principles
* HTTP Methods
* Resource Naming
* Request & Response
* Status Codes
* Authentication
* API Versioning
* Pagination
* REST vs gRPC
* Best Practices
* Interview Questions
* Quick Revision

---

# What is an API?

An **API (Application Programming Interface)** is a set of rules that allows two software applications to communicate with each other.

Example:

```text id="rest1"
Mobile App

↓

REST API

↓

Database
```

The client sends requests, and the server returns responses.

---

# What is REST?

**REST (Representational State Transfer)** is an architectural style introduced by **Roy Fielding** in 2000.

REST APIs use standard **HTTP methods** to perform operations on resources.

Example:

```text id="rest2"
GET /users/101
```

Retrieve user information.

---

# REST Architecture

```text id="rest3"
Client

↓

HTTP Request

↓

REST API

↓

Business Logic

↓

Database

↓

HTTP Response

↓

Client
```

The client never accesses the database directly.

---

# REST Principles

A RESTful API follows these principles.

---

## 1. Client-Server Architecture

The client handles the user interface.

The server manages data and business logic.

This separation improves scalability and maintainability.

---

## 2. Stateless

Each request is independent.

The server does not remember previous requests.

Example:

```text id="rest4"
Request 1

↓

Response

↓

Request 2

(No Previous State Stored)
```

Authentication is typically handled using:

* JWT
* OAuth
* Session Cookies

---

## 3. Uniform Interface

Resources are identified using URLs.

Example:

```text id="rest5"
GET /users

GET /orders

GET /products
```

---

## 4. Cacheable

Responses can be cached to improve performance.

Example:

```text id="rest6"
Cache-Control: max-age=3600
```

---

## 5. Layered System

A client may communicate through:

```text id="rest7"
Client

↓

Load Balancer

↓

API Gateway

↓

REST API

↓

Database
```

The client doesn't need to know the internal architecture.

---

# HTTP Methods

| Method | Purpose          |
| ------ | ---------------- |
| GET    | Retrieve data    |
| POST   | Create resource  |
| PUT    | Replace resource |
| PATCH  | Update resource  |
| DELETE | Remove resource  |

Example:

```http id="rest8"
GET /products/25
```

Returns product details.

---

# Resource Naming

Good REST APIs use **nouns**, not verbs.

Good:

```text id="rest9"
GET /users

POST /orders

DELETE /products/10
```

Bad:

```text id="rest10"
getUsers()

deleteProduct()
```

URLs should represent resources.

---

# Request Example

```http id="rest11"
POST /users HTTP/1.1
Content-Type: application/json

{
  "name": "John",
  "age": 25
}
```

---

# Response Example

```http id="rest12"
HTTP/1.1 201 Created

{
  "id": 101,
  "name": "John"
}
```

---

# Common Status Codes

| Code | Meaning               |
| ---- | --------------------- |
| 200  | OK                    |
| 201  | Created               |
| 204  | No Content            |
| 400  | Bad Request           |
| 401  | Unauthorized          |
| 403  | Forbidden             |
| 404  | Not Found             |
| 500  | Internal Server Error |

---

# Authentication

REST APIs commonly use:

### JWT (JSON Web Token)

```text id="rest13"
Authorization

Bearer <token>
```

---

### API Key

```text id="rest14"
x-api-key

abc123xyz
```

---

### OAuth 2.0

Used by:

* Google
* GitHub
* Microsoft
* Facebook

for secure third-party authentication.

---

# API Versioning

Versioning prevents breaking existing clients.

Common approaches:

```text id="rest15"
URL Versioning

/api/v1/users

/api/v2/users
```

or

```text id="rest16"
Header Versioning
```

---

# Pagination

Large datasets should not be returned in a single response.

Example:

```text id="rest17"
GET /products?page=2&limit=20
```

Benefits:

* Faster responses
* Reduced bandwidth
* Better user experience

---

# REST vs gRPC

| Feature         | REST      | gRPC      |
| --------------- | --------- | --------- |
| Data Format     | JSON      | Protobuf  |
| Protocol        | HTTP      | HTTP/2    |
| Performance     | Good      | Excellent |
| Browser Support | Excellent | Limited   |
| Streaming       | Limited   | Built-in  |
| Human Readable  | Yes       | No        |

---

# Best Practices

* Use nouns for resources.
* Use appropriate HTTP methods.
* Return meaningful status codes.
* Keep APIs stateless.
* Version APIs.
* Secure APIs with HTTPS.
* Validate user input.
* Use pagination for large datasets.
* Document APIs using OpenAPI/Swagger.

---

# Real-World Example

E-commerce API:

```text id="rest18"
GET    /products

GET    /products/15

POST   /orders

PUT    /users/10

DELETE /cart/5
```

These endpoints allow clients to interact with the application.

---

# Interview Questions

* What is REST?
* What is a REST API?
* What are REST principles?
* Why are REST APIs stateless?
* Difference between PUT and PATCH?
* Difference between POST and PUT?
* Difference between REST and gRPC?
* Why is versioning important?
* How do you secure a REST API?

---

# Quick Revision

```text id="rest19"
REST

↓

HTTP

↓

Resources

↓

JSON

↓

Stateless

HTTP Methods

GET

POST

PUT

PATCH

DELETE

Authentication

JWT

API Key

OAuth

Best Practices

✔ Nouns

✔ Versioning

✔ Pagination

✔ HTTPS
```

---

# Key Takeaways

* **REST** is an architectural style for building scalable web APIs.
* REST APIs communicate over **HTTP** and typically exchange data using **JSON**.
* They follow principles such as **statelessness**, **client-server architecture**, **uniform interfaces**, and **cacheability**.
* Proper use of HTTP methods, status codes, authentication, pagination, and versioning leads to maintainable and scalable APIs.
* REST remains the most widely adopted approach for building public web services, while gRPC is often preferred for high-performance internal microservice communication.

---

# Networking Fundamentals Complete

You have now completed **03 - Networking Fundamentals**.

## Topics Covered

* ✅ OSI Model
* ✅ TCP/IP Model
* ✅ TCP vs UDP
* ✅ HTTP
* ✅ HTTPS
* ✅ HTTP/2 & HTTP/3
* ✅ DNS
* ✅ TLS & SSL
* ✅ WebSockets
* ✅ gRPC
* ✅ REST APIs

These concepts form the communication backbone of modern distributed systems and are essential for understanding web architecture, microservices, cloud platforms, and system design interviews.

---


