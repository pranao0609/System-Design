# Cache Basics

> *"Caching is the process of storing frequently accessed data in a fast storage layer so future requests can be served quickly without repeatedly accessing the original data source."*

---

# Table of Contents

* What is Caching?
* Why Do We Need Caching?
* How Caching Works
* Cache Hit & Cache Miss
* Cache Hit Ratio
* Types of Caches
* Benefits of Caching
* Challenges of Caching
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Caching?

A **Cache** is a high-speed storage layer that stores frequently accessed data temporarily.

Instead of retrieving data from a slower database every time, the application first checks the cache.

If the data exists, it is returned immediately.

```text id="cache1"
Client

↓

Application

↓

Cache

↓

Database
```

The cache acts as an intermediate layer between the application and the database.

---

# Why Do We Need Caching?

Suppose an application receives:

```text id="cache2"
100,000 Requests

↓

Same Product Data
```

Without caching:

```text id="cache3"
Every Request

↓

Database
```

The database becomes overloaded.

With caching:

```text id="cache4"
Request

↓

Cache

↓

Database (Only if Needed)
```

Most requests are served directly from memory.

---

# How Caching Works

Step-by-step process:

```text id="cache5"
Client

↓

Application

↓

Check Cache

↓

Found?

↓

Yes → Return Data

↓

No → Query Database

↓

Store in Cache

↓

Return Data
```

This reduces repeated database queries.

---

# Cache Hit & Cache Miss

## Cache Hit

A **Cache Hit** occurs when the requested data is found in the cache.

```text id="cache6"
Request

↓

Cache

↓

Data Found

↓

Return Immediately
```

Fast response.

---

## Cache Miss

A **Cache Miss** occurs when the requested data is not present in the cache.

```text id="cache7"
Request

↓

Cache

↓

Data Not Found

↓

Database

↓

Store in Cache

↓

Return Data
```

The first request is slower, but future requests become faster.

---

# Cache Hit Ratio

The **Cache Hit Ratio** measures cache effectiveness.

Formula:

```text id="cache8"
Cache Hit Ratio

=

Cache Hits

÷

Total Requests

× 100%
```

Example:

```text id="cache9"
90 Hits

10 Misses

↓

100 Requests

↓

90% Hit Ratio
```

A higher hit ratio means better cache performance.

---

# Types of Caches

### Browser Cache

Stores website resources locally in the user's browser.

---

### CDN Cache

Caches static content at edge servers closer to users.

---

### Application Cache

Stores frequently used application data.

Example:

* User Profiles
* Product Details
* Configuration Data

---

### Database Cache

Stores frequently executed query results.

---

### Distributed Cache

Shared cache used across multiple application servers.

Example:

* Redis
* Memcached

---

# Benefits of Caching

* Faster response times.
* Lower database load.
* Higher throughput.
* Reduced latency.
* Better scalability.
* Improved user experience.

---

# Challenges of Caching

## Stale Data

Cached data may become outdated after updates.

---

## Cache Invalidation

Determining when cached data should be removed or refreshed.

---

## Cache Consistency

Ensuring cache and database remain synchronized.

---

## Memory Limitations

Caches use RAM, which is limited and more expensive than disk storage.

---

# Real-World Examples

## Amazon

Product information is cached to reduce database queries.

---

## Netflix

Movie metadata and recommendations are cached for faster access.

---

## Google Search

Frequently accessed search results are cached to improve response times.

---

## Facebook

User profiles and news feed data are cached to reduce latency.

---

# Quick Revision

```text id="cache10"
Caching

↓

Fast Memory

↓

Cache

↓

Database

Cache Hit

↓

Fast

Cache Miss

↓

Database

↓

Store in Cache

Benefits

✔ Low Latency

✔ High Throughput

✔ Reduced Database Load
```

---

# Key Takeaways

* **Caching** stores frequently accessed data in a fast memory layer to reduce database access.
* A **Cache Hit** returns data immediately, while a **Cache Miss** requires fetching data from the database before storing it in the cache.
* A high **Cache Hit Ratio** indicates an efficient caching system.
* Caching improves **performance, scalability, throughput, and user experience**, making it a core component of modern distributed systems.
* Challenges such as **stale data, cache invalidation, and consistency** must be carefully managed in production systems.

---

> **Next Topic:** `02-Redis.md`
