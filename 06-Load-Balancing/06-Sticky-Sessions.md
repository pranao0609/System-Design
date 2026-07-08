# Sticky Sessions

> *"Sticky Sessions (Session Affinity) ensure that requests from the same client are consistently routed to the same backend server during a session."*

---

# Table of Contents

* What are Sticky Sessions?
* Why Do We Need Sticky Sessions?
* How Sticky Sessions Work
* Session Affinity Methods
* Advantages
* Disadvantages
* Sticky Sessions vs Stateless Applications
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What are Sticky Sessions?

**Sticky Sessions**, also known as **Session Affinity**, are a load balancing technique where all requests from the same client are directed to the same backend server.

Example:

```text id="ss1"
Client A

↓

Load Balancer

↓

Server 1

(All Requests)
```

Even if multiple servers are available, the user's session remains tied to one server.

---

# Why Do We Need Sticky Sessions?

Consider a user logging into a website.

```text id="ss2"
Login

↓

Server A

↓

Session Created
```

If the next request goes to another server:

```text id="ss3"
Dashboard Request

↓

Server B

↓

Session Not Found

↓

User Logged Out
```

Sticky Sessions prevent this problem by routing all requests to the same server.

---

# How Sticky Sessions Work

```text id="ss4"
User

↓

Load Balancer

↓

Server A

↓

Server Stores Session
```

Subsequent requests:

```text id="ss5"
Same User

↓

Load Balancer

↓

Server A
```

The user continues interacting with the same backend server.

---

# Session Affinity Methods

## 1. Cookie-Based

The load balancer sets a cookie identifying the backend server.

```text id="ss6"
Cookie

↓

Server A

↓

Future Requests

↓

Server A
```

This is the most common approach for web applications.

---

## 2. IP-Based

The client's IP address determines the backend server.

```text id="ss7"
Client IP

↓

Hash

↓

Server B
```

Simple to implement but less reliable when clients share IP addresses or use dynamic IPs.

---

## 3. Session ID-Based

The application session ID is used to route requests consistently to the same server.

---

# Advantages

* Simple session management.
* No need for shared session storage.
* Easy to deploy for legacy applications.
* Faster access to locally stored session data.

---

# Disadvantages

## Uneven Load Distribution

Some servers may receive significantly more users than others.

---

## Server Failure

If the assigned server crashes:

```text id="ss8"
Server A

↓

Crash

↓

User Session Lost
```

Unless sessions are replicated or stored externally, users may need to log in again.

---

## Reduced Scalability

Sticky Sessions make horizontal scaling more difficult because user state is tied to individual servers.

---

# Sticky Sessions vs Stateless Applications

| Sticky Sessions           | Stateless Applications                |
| ------------------------- | ------------------------------------- |
| Session stored on server  | Session stored externally or in token |
| Requires Session Affinity | Any server can handle any request     |
| Less scalable             | Highly scalable                       |
| Easier for legacy apps    | Preferred for cloud-native systems    |

Modern microservices typically prefer **stateless applications**.

---

# Alternatives to Sticky Sessions

Instead of storing sessions on individual servers:

* Store sessions in Redis.
* Store sessions in a shared database.
* Use JWT (JSON Web Tokens).
* Use distributed session stores.

Example:

```text id="ss9"
Client

↓

Load Balancer

↓

Any Server

↓

Redis Session Store
```

Any backend server can retrieve the user's session.

---

# Real-World Examples

## Legacy Web Applications

Many traditional Java and PHP applications rely on Sticky Sessions.

---

## Kubernetes

Supports session affinity when required, but stateless services are generally recommended.

---

## E-Commerce

Modern platforms often store sessions in Redis, allowing requests to be served by any backend instance.

---

# Best Practices

* Prefer stateless application design whenever possible.
* Use shared session storage for scalability.
* Use Sticky Sessions only when necessary.
* Replicate session data if server failures are a concern.
* Monitor server load to prevent imbalance.

---

# Quick Revision

```text id="ss10"
Sticky Sessions

↓

Same Client

↓

Same Server

Methods

✔ Cookie

✔ IP Hash

✔ Session ID

Challenges

✖ Server Failure

✖ Load Imbalance

Alternative

↓

Redis

↓

JWT

↓

Stateless Apps
```

---

# Key Takeaways

* **Sticky Sessions** ensure that requests from the same client are consistently routed to the same backend server.
* They simplify session management but reduce scalability and fault tolerance.
* Common affinity methods include **cookies, IP hashing, and session IDs**.
* Modern distributed systems generally prefer **stateless applications** with shared session stores or JWT-based authentication.
* Understanding the trade-offs between Sticky Sessions and stateless architectures is important for designing scalable web applications.

---

> **Next Topic:** `07-Global-Load-Balancing.md`
