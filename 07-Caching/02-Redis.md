# Redis

> *"Redis (Remote Dictionary Server) is an in-memory data store used as a cache, database, message broker, and session store. It is designed for extremely fast read and write operations."*

---

# Table of Contents

* What is Redis?
* Why Do We Need Redis?
* How Redis Works
* Redis Data Structures
* Common Use Cases
* Persistence
* Redis vs Memcached
* Advantages
* Disadvantages
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Redis?

**Redis** is an **open-source, in-memory key-value data store**.

Unlike traditional databases that primarily store data on disk, Redis stores data in **RAM**, making it extremely fast.

Redis can be used as:

* Cache
* Database
* Session Store
* Message Broker
* Queue
* Leaderboard Store

---

# Why Do We Need Redis?

Imagine an e-commerce website.

Every request fetches product details from the database.

```text id="redis1"
Client

↓

Application

↓

Database
```

As traffic grows:

* Database becomes overloaded.
* Response time increases.

Using Redis:

```text id="redis2"
Client

↓

Application

↓

Redis

↓

Database (Only if Needed)
```

Most requests are served directly from Redis.

---

# How Redis Works

Redis stores data as **key-value pairs** in memory.

Example:

```text id="redis3"
Key

user:101

↓

Value

{Name: Alice}
```

Lookup Process:

```text id="redis4"
Request

↓

Redis

↓

Found?

↓

Yes → Return Data

↓

No → Query Database

↓

Store in Redis

↓

Return Data
```

---

# Redis Data Structures

Redis supports multiple data structures.

### String

```text id="redis5"
user:name

↓

Alice
```

Used for simple values.

---

### Hash

Stores objects with multiple fields.

```text id="redis6"
User

↓

Name

Age

Email
```

---

### List

Stores ordered collections.

Use Cases:

* Task Queues
* Activity Feeds

---

### Set

Stores unique values.

Use Cases:

* Tags
* Friend Lists

---

### Sorted Set

Maintains ordered data using scores.

Use Cases:

* Leaderboards
* Rankings

---

### Stream

Stores ordered event data.

Used for:

* Event Streaming
* Messaging

---

# Common Use Cases

## Caching

Frequently accessed data.

---

## Session Storage

Store user login sessions.

---

## Rate Limiting

Track API requests.

Example:

```text id="redis7"
User

↓

Redis Counter

↓

Limit Exceeded?

↓

Reject Request
```

---

## Leaderboards

Games rank players using **Sorted Sets**.

---

## Pub/Sub Messaging

Applications communicate using publishers and subscribers.

---

## Distributed Locking

Prevent multiple services from modifying the same resource simultaneously.

---

# Persistence

Although Redis is memory-based, it supports persistence.

### RDB (Snapshot)

Periodically saves the dataset to disk.

---

### AOF (Append Only File)

Logs every write operation.

Provides better durability than snapshots.

---

# Redis vs Memcached

| Redis                    | Memcached            |
| ------------------------ | -------------------- |
| Multiple Data Structures | Strings Only         |
| Supports Persistence     | No Persistence       |
| Pub/Sub                  | Not Supported        |
| Transactions             | Not Supported        |
| Replication              | Limited              |
| Rich Feature Set         | Lightweight & Simple |

---

# Advantages

* Extremely fast (memory-based).
* Supports multiple data structures.
* High throughput.
* Supports replication.
* Built-in persistence.
* Widely used in distributed systems.

---

# Disadvantages

* RAM is expensive.
* Limited by available memory.
* Persistence is slower than dedicated databases.
* Not suitable as the primary database for every workload.

---

# Real-World Examples

## Twitter

Caches timelines and user profiles.

---

## Instagram

Stores user sessions and frequently accessed data.

---

## Netflix

Caches movie metadata and recommendations.

---

## Uber

Uses Redis for location lookups and rate limiting.

---

# Quick Revision

```text id="redis8"
Redis

↓

In-Memory Database

↓

Key-Value Store

Uses

✔ Cache

✔ Session Store

✔ Queue

✔ Pub/Sub

✔ Rate Limiting

Data Structures

String

Hash

List

Set

Sorted Set

Stream
```

---

# Key Takeaways

* **Redis** is an in-memory key-value data store designed for extremely fast data access.
* It is widely used for **caching, session storage, rate limiting, messaging, leaderboards, and distributed locking**.
* Redis supports advanced data structures such as **Strings, Hashes, Lists, Sets, Sorted Sets, and Streams**.
* Features like **replication** and **optional persistence (RDB and AOF)** make Redis suitable for many production workloads.
* Redis is one of the most commonly used technologies in modern backend systems and is a favorite topic in system design interviews.

---

> **Next Topic:** `03-Memcached.md`
