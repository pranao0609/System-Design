# Cache Eviction Policies

> *"Cache Eviction Policies define which data should be removed from the cache when it becomes full, ensuring efficient use of limited memory."*

---

# Table of Contents

* What is Cache Eviction?
* Why Do We Need Eviction Policies?
* How Cache Eviction Works
* LRU (Least Recently Used)
* LFU (Least Frequently Used)
* FIFO (First In, First Out)
* Random Replacement
* TTL (Time-To-Live)
* Policy Comparison
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Cache Eviction?

A cache has **limited memory**.

When the cache becomes full, some data must be removed to make space for new data.

This process is called **Cache Eviction**.

```text id="cep1"
Cache Full

↓

Remove Old Data

↓

Store New Data
```

The rule used to decide which data to remove is called the **Eviction Policy**.

---

# Why Do We Need Eviction Policies?

Suppose a cache can store only:

```text id="cep2"
100 Items
```

A new request arrives.

```text id="cep3"
101st Item
```

The cache must decide which existing item to remove.

A good eviction policy improves:

* Cache Hit Ratio
* Performance
* Memory Utilization

---

# How Cache Eviction Works

```text id="cep4"
Cache

↓

Memory Full

↓

Eviction Policy

↓

Remove Item

↓

Insert New Item
```

Different systems choose different policies depending on workload.

---

# 1. LRU (Least Recently Used)

The **least recently accessed** item is removed first.

Example:

```text id="cep5"
Access Order

A

B

C

D

↓

Access A Again

↓

B is Least Recently Used

↓

Remove B
```

### Advantages

* Excellent for applications with temporal locality.
* Most widely used policy.

### Disadvantages

* Requires tracking recent access history.

---

# 2. LFU (Least Frequently Used)

The item with the **fewest accesses** is removed.

Example:

```text id="cep6"
A → 20 Accesses

B → 2 Accesses

C → 15 Accesses

↓

Remove B
```

### Advantages

* Retains frequently accessed data.

### Disadvantages

* Requires maintaining access counters.
* Older frequently accessed data may stay longer than desired.

---

# 3. FIFO (First In, First Out)

The oldest inserted item is removed first.

Example:

```text id="cep7"
Inserted

A

↓

B

↓

C

↓

New Item

↓

Remove A
```

### Advantages

* Very simple.
* Low overhead.

### Disadvantages

* May remove frequently accessed data.

---

# 4. Random Replacement

A random cache item is selected for eviction.

```text id="cep8"
Cache Full

↓

Random Item Removed
```

### Advantages

* Very easy to implement.
* Low computational cost.

### Disadvantages

* Frequently used data may be removed accidentally.

---

# 5. TTL (Time-To-Live)

Each cache entry has an expiration time.

Example:

```text id="cep9"
Product Cache

↓

Expires

↓

30 Minutes
```

Once the TTL expires, the entry is removed automatically.

### Advantages

* Prevents stale data.
* Easy expiration management.

### Disadvantages

* Frequently accessed data may expire unnecessarily.

---

# Policy Comparison

| Policy | Removes                    | Best For                |
| ------ | -------------------------- | ----------------------- |
| LRU    | Least recently used item   | General-purpose caching |
| LFU    | Least frequently used item | Stable access patterns  |
| FIFO   | Oldest inserted item       | Simple systems          |
| Random | Random item                | Lightweight caches      |
| TTL    | Expired item               | Time-sensitive data     |

---

# Real-World Examples

## Redis

Supports:

* LRU
* LFU
* TTL
* Random

---

## Memcached

Primarily uses **LRU**.

---

## Browser Cache

Uses TTL along with other cache management techniques.

---

## CDN

Static assets are commonly removed using TTL-based expiration.

---

# Choosing the Right Policy

| Workload                     | Recommended Policy |
| ---------------------------- | ------------------ |
| General Web Applications     | LRU                |
| Frequently Accessed Hot Data | LFU                |
| Simple Cache Systems         | FIFO               |
| Temporary Data               | TTL                |
| Lightweight Systems          | Random             |

---

# Quick Revision

```text id="cep10"
Cache Full

↓

Eviction Policy

Policies

✔ LRU

✔ LFU

✔ FIFO

✔ Random

✔ TTL

Most Common

↓

LRU

Best for Hot Data

↓

LFU
```

---

# Key Takeaways

* **Cache Eviction Policies** determine which cache entries are removed when memory becomes full.
* **LRU (Least Recently Used)** is the most commonly used policy because recently accessed data is likely to be accessed again.
* **LFU (Least Frequently Used)** is suitable when frequently accessed data should remain in the cache.
* **TTL (Time-To-Live)** helps remove stale data automatically after a specified duration.
* Choosing the right eviction policy improves **cache hit ratio, memory utilization, and overall application performance**.

---

> **Next Topic:** `08-Cache-Invalidation.md`
