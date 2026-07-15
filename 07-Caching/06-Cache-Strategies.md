# Cache Strategies

> *"Cache Strategies define how data is read from and written to the cache and the database. Choosing the right strategy helps balance performance, consistency, and reliability."*

---

# Table of Contents

* What are Cache Strategies?
* Why Do We Need Cache Strategies?
* Cache-Aside
* Read-Through
* Write-Through
* Write-Back (Write-Behind)
* Write-Around
* Strategy Comparison
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What are Cache Strategies?

A **Cache Strategy** determines how an application interacts with:

* Cache
* Database

during **read** and **write** operations.

Different applications require different strategies depending on:

* Performance
* Consistency
* Write frequency
* Read frequency

---

# Why Do We Need Cache Strategies?

Consider an application:

```text id="cs1"
Application

↓

Cache

↓

Database
```

Questions arise:

* Should data be read from the cache first?
* When should the cache be updated?
* Should writes go directly to the database?
* What happens if the cache becomes outdated?

Cache strategies answer these questions.

---

# 1. Cache-Aside (Lazy Loading)

The application first checks the cache.

If data is not found:

1. Read from the database.
2. Store it in the cache.
3. Return the data.

```text id="cs2"
Request

↓

Cache

↓

Miss

↓

Database

↓

Update Cache

↓

Return Data
```

### Advantages

* Easy to implement.
* Only frequently used data is cached.
* Saves memory.

### Disadvantages

* First request is slower (cache miss).
* Cache can become stale.

**Common Use Cases:**

* Product Details
* User Profiles
* News Articles

---

# 2. Read-Through

The application always reads from the cache.

If data is missing:

The cache automatically retrieves it from the database.

```text id="cs3"
Application

↓

Cache

↓

Database
```

The application never communicates directly with the database.

### Advantages

* Simplifies application logic.
* Automatic cache population.

### Disadvantages

* More complex cache implementation.
* Cache layer becomes responsible for database access.

---

# 3. Write-Through

Every write updates:

* Cache
* Database

simultaneously.

```text id="cs4"
Application

↓

Cache

↓

Database
```

Both always contain the latest data.

### Advantages

* Strong consistency.
* No stale cache after writes.

### Disadvantages

* Slower write operations.
* Every write updates two systems.

**Use Cases:**

* Banking
* Inventory Management
* Financial Applications

---

# 4. Write-Back (Write-Behind)

Data is written to the cache immediately.

The database is updated **later** in the background.

```text id="cs5"
Application

↓

Cache

↓

Immediate Response

↓

Background Write

↓

Database
```

### Advantages

* Extremely fast writes.
* Reduced database load.

### Disadvantages

* Risk of data loss if the cache fails before flushing.
* More complex implementation.

**Use Cases:**

* Analytics
* Logging
* IoT Systems

---

# 5. Write-Around

Writes go **directly to the database**.

The cache is not updated.

```text id="cs6"
Application

↓

Database

↓

Future Read

↓

Cache
```

Data enters the cache only when it is read.

### Advantages

* Prevents caching rarely accessed data.
* Saves cache memory.

### Disadvantages

* First read after every write results in a cache miss.

**Use Cases:**

* Frequently updated data.
* Large datasets.

---

# Strategy Comparison

| Strategy      | Read       | Write            | Best For                |
| ------------- | ---------- | ---------------- | ----------------------- |
| Cache-Aside   | Cache → DB | DB Only          | General-purpose caching |
| Read-Through  | Cache      | DB via Cache     | Managed cache systems   |
| Write-Through | Cache      | Cache + DB       | Strong consistency      |
| Write-Back    | Cache      | Cache → DB Later | High write throughput   |
| Write-Around  | Cache      | DB Only          | Write-heavy workloads   |

---

# Real-World Examples

## Amazon

Product details commonly use **Cache-Aside**.

---

## Banking

Transactions often use **Write-Through** to maintain consistency.

---

## Facebook

News Feed caching commonly follows **Cache-Aside**.

---

## Analytics Platforms

Event ingestion often uses **Write-Back** for faster writes.

---

# Best Practices

* Use **Cache-Aside** for most web applications.
* Use **Write-Through** when data consistency is critical.
* Use **Write-Back** for high-volume write workloads.
* Use **Write-Around** to avoid caching rarely read data.
* Monitor cache hit ratio and adjust strategies based on access patterns.

---

# Quick Revision

```text id="cs7"
Cache Strategies

↓

Cache-Aside

↓

Read-Through

↓

Write-Through

↓

Write-Back

↓

Write-Around

Most Common

✔ Cache-Aside

Fastest Writes

✔ Write-Back

Strongest Consistency

✔ Write-Through
```

---

# Key Takeaways

* **Cache Strategies** define how applications coordinate reads and writes between the cache and the database.
* **Cache-Aside** is the most commonly used strategy because it is simple and efficient.
* **Write-Through** ensures strong consistency by updating both the cache and the database simultaneously.
* **Write-Back** provides excellent write performance by delaying database updates, while **Write-Around** avoids caching infrequently accessed data.
* Selecting the right cache strategy depends on the application's requirements for **performance, consistency, and access patterns**.

---

> **Next Topic:** `07-Cache-Eviction-Policies.md`
