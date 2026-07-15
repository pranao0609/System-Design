# Cache Invalidation

> *"Cache Invalidation is the process of removing or updating stale data in the cache to ensure users receive the latest and most accurate information."*

---

# Table of Contents

* What is Cache Invalidation?
* Why is Cache Invalidation Important?
* The Cache Invalidation Problem
* Cache Invalidation Techniques
* TTL-Based Invalidation
* Write-Through Invalidation
* Cache-Aside Invalidation
* Event-Based Invalidation
* Challenges
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Cache Invalidation?

A cache stores frequently accessed data to improve performance.

However, when the original data changes, the cached copy may become outdated.

**Cache Invalidation** ensures that stale cache entries are removed or refreshed.

```text id="ci1"
Database Updated

↓

Cache Updated / Removed

↓

Users Receive Latest Data
```

---

# Why is Cache Invalidation Important?

Imagine an e-commerce application.

```text id="ci2"
Laptop Price

Database

₹50,000
```

The price changes.

```text id="ci3"
Database

↓

₹45,000
```

But the cache still contains:

```text id="ci4"
₹50,000
```

Users now see incorrect information.

Cache invalidation prevents this issue.

---

# The Cache Invalidation Problem

One of the famous sayings in computer science is:

> **"There are only two hard things in Computer Science: Cache Invalidation and Naming Things."**

The challenge is deciding **when** and **how** to update or remove cached data while balancing:

* Performance
* Consistency
* Complexity

---

# Cache Invalidation Techniques

## 1. TTL (Time-To-Live)

Each cache entry has an expiration time.

```text id="ci5"
Cache Entry

↓

Expires After

30 Minutes

↓

Removed Automatically
```

### Advantages

* Simple implementation.
* Prevents long-lived stale data.

### Disadvantages

* Data may remain stale until TTL expires.

---

## 2. Write-Through Invalidation

Whenever the database is updated, the cache is updated immediately.

```text id="ci6"
Application

↓

Cache Updated

↓

Database Updated
```

### Advantages

* Strong consistency.
* Users always receive fresh data.

### Disadvantages

* Slower write operations.

---

## 3. Cache-Aside Invalidation

After updating the database, the application removes the corresponding cache entry.

```text id="ci7"
Update Database

↓

Delete Cache Entry

↓

Next Read

↓

Fetch Database

↓

Store New Value
```

This is one of the most commonly used approaches.

---

## 4. Event-Based Invalidation

When data changes, an event is published.

All cache servers listening to the event remove or update their cached copies.

```text id="ci8"
Database Update

↓

Publish Event

↓

Cache Nodes

↓

Invalidate Cache
```

Used in distributed systems.

---

# Challenges

## Stale Data

Users may temporarily see outdated information.

---

## Distributed Caches

Multiple cache nodes must remain synchronized.

---

## Race Conditions

A cache may be updated while another request is still reading stale data.

---

## Network Delays

Invalidation events may arrive late across regions.

---

# Best Practices

* Use **TTL** for data that changes infrequently.
* Use **Cache-Aside** for general web applications.
* Use **Write-Through** when consistency is critical.
* Use **Event-Based Invalidation** in distributed systems.
* Monitor cache hit ratio and stale data rates.
* Keep TTL values appropriate—not too long, not too short.

---

# Real-World Examples

## Amazon

When a product price changes, the corresponding cache entry is invalidated to ensure customers see the latest price.

---

## Netflix

Movie metadata caches are refreshed when content details change.

---

## Facebook

News Feed caches are invalidated when users create or edit posts.

---

## CDN

Static assets are refreshed using TTL expiration or explicit cache purge operations.

---

# Quick Revision

```text id="ci9"
Cache Invalidation

↓

Data Updated

↓

Refresh Cache

Methods

✔ TTL

✔ Cache-Aside

✔ Write-Through

✔ Event-Based

Challenges

✖ Stale Data

✖ Race Conditions

✖ Distributed Cache Sync
```

---

# Key Takeaways

* **Cache Invalidation** ensures cached data stays synchronized with the source of truth (usually the database).
* The most common techniques are **TTL, Cache-Aside, Write-Through, and Event-Based Invalidation**.
* Incorrect invalidation can lead to **stale data**, while overly aggressive invalidation reduces cache efficiency.
* Choosing the right invalidation strategy depends on the application's consistency requirements and update frequency.
* Cache invalidation is one of the most important and frequently discussed topics in system design because it directly impacts both **performance and correctness**.

---
