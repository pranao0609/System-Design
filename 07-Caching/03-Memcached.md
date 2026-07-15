# Memcached

> *"Memcached is a high-performance, distributed in-memory caching system that stores key-value pairs to reduce database load and improve application response times."*

---

# Table of Contents

* What is Memcached?
* Why Do We Need Memcached?
* How Memcached Works
* Memcached Architecture
* Redis vs Memcached
* Common Use Cases
* Advantages
* Disadvantages
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Memcached?

**Memcached** is an **open-source, in-memory distributed cache**.

It stores frequently accessed data in RAM as **simple key-value pairs**.

Unlike Redis, Memcached is **only a caching system**. It does not support advanced data structures or persistence.

Example:

```text id="mc1"
Key

product:101

↓

Value

Laptop Details
```

---

# Why Do We Need Memcached?

Suppose thousands of users request the same product information.

Without Memcached:

```text id="mc2"
Client

↓

Application

↓

Database
```

Every request reaches the database.

With Memcached:

```text id="mc3"
Client

↓

Application

↓

Memcached

↓

Database (Only if Cache Miss)
```

The database receives far fewer requests.

---

# How Memcached Works

Step-by-step process:

```text id="mc4"
Client

↓

Application

↓

Check Memcached

↓

Found?

↓

Yes → Return Data

↓

No → Query Database

↓

Store in Memcached

↓

Return Data
```

Most repeated requests are served directly from memory.

---

# Memcached Architecture

Memcached is designed to be:

* Distributed
* Lightweight
* Memory-based

Example:

```text id="mc5"
Application

↓

Memcached Cluster

↓

Node 1

Node 2

Node 3
```

Data is distributed across multiple cache nodes.

---

# Redis vs Memcached

| Redis                    | Memcached             |
| ------------------------ | --------------------- |
| Multiple Data Structures | Strings Only          |
| Supports Persistence     | No Persistence        |
| Pub/Sub Support          | Not Supported         |
| Transactions             | Not Supported         |
| Rich Features            | Lightweight & Simple  |
| More Memory Overhead     | Lower Memory Overhead |

---

# Common Use Cases

## Database Query Cache

Frequently executed queries.

---

## Web Page Cache

Store rendered HTML pages.

---

## Session Cache

Store temporary user session data.

---

## Product Catalog Cache

Frequently viewed products.

---

## API Response Cache

Store responses from expensive API calls.

---

# Advantages

* Extremely fast.
* Simple architecture.
* Low memory overhead.
* Easy horizontal scaling.
* Reduces database load.

---

# Disadvantages

* No persistence.
* Supports only simple key-value pairs.
* No replication.
* No advanced data structures.
* Limited feature set compared to Redis.

---

# Real-World Examples

## Wikipedia

Historically used Memcached to reduce database load for frequently accessed pages.

---

## Facebook

Used Memcached extensively to cache user profiles and social graph data, helping serve billions of requests efficiently.

---

## E-Commerce Websites

Cache product details, pricing, and frequently viewed pages.

---

## News Websites

Cache articles and homepage content to handle traffic spikes.

---

# When to Use Memcached

Choose Memcached when:

* Only simple key-value caching is required.
* Persistence is not needed.
* Maximum speed with minimal overhead is desired.
* Large numbers of cache nodes are used.

For advanced caching features, Redis is often the preferred choice.

---

# Quick Revision

```text id="mc6"
Memcached

↓

In-Memory Cache

↓

Key-Value Store

Uses

✔ Query Cache

✔ Session Cache

✔ API Cache

✔ Web Cache

Features

✔ Fast

✔ Lightweight

✔ Distributed

Limitations

✖ No Persistence

✖ Strings Only

✖ No Replication
```

---

# Key Takeaways

* **Memcached** is a lightweight, distributed in-memory caching system designed to reduce database load and improve application performance.
* It stores **simple key-value pairs** in RAM and is optimized for high-speed read and write operations.
* Unlike Redis, Memcached does **not** support persistence, replication, or advanced data structures.
* Memcached is ideal for **temporary caching** of frequently accessed data such as query results, web pages, sessions, and API responses.
* Choosing between **Redis** and **Memcached** depends on whether you need advanced features or a simple, high-performance cache.

---

> **Next Topic:** `04-Distributed-Cache.md`
