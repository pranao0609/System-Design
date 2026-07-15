#  07. Caching

Caching is one of the most powerful techniques for improving application performance. Instead of repeatedly fetching data from slow storage (such as databases), frequently accessed data is stored in a fast memory layer called a **cache**.

Modern applications like **Google, Netflix, Amazon, Facebook, and YouTube** rely heavily on caching to reduce latency, increase throughput, lower database load, and serve millions of users efficiently.

---

# 📚 Topics Covered

## Cache Basics

Learn the fundamentals of caching, cache hits and misses, and why caching is essential for scalable systems.

📄 **File:** `01-Cache-Basics.md`

---

## Redis

Understand Redis, one of the most popular in-memory databases used for caching, session storage, rate limiting, and messaging.

📄 **File:** `02-Redis.md`

---

## Memcached

Learn about Memcached, a lightweight distributed caching system designed for high-speed key-value storage.

📄 **File:** `03-Memcached.md`

---

## Distributed Cache

Explore how caching works across multiple servers and how distributed caches improve scalability and fault tolerance.

📄 **File:** `04-Distributed-Cache.md`

---

## CDN (Content Delivery Network)

Learn how CDNs cache static content closer to users to reduce latency and improve website performance.

📄 **File:** `05-CDN.md`

---

## Cache Strategies

Understand common caching strategies such as Cache-Aside, Write-Through, Write-Back, and Write-Around.

📄 **File:** `06-Cache-Strategies.md`

---

## Cache Eviction Policies

Learn how caches decide which data to remove when memory becomes full.

📄 **File:** `07-Cache-Eviction-Policies.md`

---

## Cache Invalidation

Understand one of the hardest problems in computer science—keeping cached data synchronized with the source of truth.

📄 **File:** `08-Cache-Invalidation.md`

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

* Explain why caching is important.
* Understand cache hits, misses, and hit ratios.
* Use Redis and Memcached effectively.
* Design distributed caching systems.
* Explain how CDNs improve performance.
* Compare different cache strategies.
* Choose appropriate cache eviction policies.
* Handle cache invalidation correctly.

---

# 📂 Folder Structure

```text
07-Caching/
│
├── README.md
├── 01-Cache-Basics.md
├── 02-Redis.md
├── 03-Memcached.md
├── 04-Distributed-Cache.md
├── 05-CDN.md
├── 06-Cache-Strategies.md
├── 07-Cache-Eviction-Policies.md
└── 08-Cache-Invalidation.md
```

---

# 🌍 Why This Section Matters

Databases are relatively slow compared to memory. If every request reaches the database, applications become slower and more expensive to scale.

Caching solves this by storing frequently accessed data in memory, allowing applications to respond in milliseconds instead of querying the database repeatedly.

Benefits include:

* Lower Latency
* Higher Throughput
* Reduced Database Load
* Better Scalability
* Improved User Experience

Caching is a fundamental component of nearly every large-scale distributed system.

---

#  What's Next?

 **01-Cache-Basics.md**

You'll learn:

* What is Caching?
* Why Do We Need Caching?
* Cache Hit & Cache Miss
* Cache Hit Ratio
* Types of Caches
* Benefits of Caching
* Challenges of Caching
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways
