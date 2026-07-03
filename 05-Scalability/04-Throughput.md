# Throughput

> *"Throughput is the amount of work a system can perform in a given period of time. It measures how many requests, transactions, or operations a system can process successfully."*

---

# Table of Contents

* What is Throughput?
* Why is Throughput Important?
* Throughput vs Latency
* How Throughput is Measured
* Factors Affecting Throughput
* Improving Throughput
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Throughput?

**Throughput** is the number of requests or operations that a system can process in a specific amount of time.

It is commonly measured as:

* Requests Per Second (RPS)
* Transactions Per Second (TPS)
* Queries Per Second (QPS)
* Messages Per Second (MPS)

Example:

```text id="tp1"
1000 Requests

↓

1 Second

↓

Throughput = 1000 RPS
```

Higher throughput means the system can handle more work.

---

# Why is Throughput Important?

Imagine an online shopping website during a festival sale.

```text id="tp2"
Users

↓

100,000 Requests

↓

Application
```

If the application can process only:

```text id="tp3"
5,000 Requests/Second
```

remaining requests must wait, causing slow response times or failures.

A higher throughput enables the application to serve more users simultaneously.

---

# Throughput vs Latency

These two concepts are closely related but different.

| Throughput          | Latency                    |
| ------------------- | -------------------------- |
| Amount of work done | Time taken for one request |
| Higher is better    | Lower is better            |
| Measured in RPS/TPS | Measured in ms/sec         |

Example:

```text id="tp4"
Server A

1000 RPS

100 ms

Server B

5000 RPS

150 ms
```

Server B handles more requests but each request takes slightly longer.

---

# How Throughput is Measured

Throughput can be calculated as:

```text id="tp5"
Throughput

=

Completed Requests

÷

Time
```

Example:

```text id="tp6"
20,000 Requests

↓

10 Seconds

↓

2000 Requests/Second
```

---

# Factors Affecting Throughput

Several factors influence throughput.

### CPU

More CPU cores allow more concurrent processing.

---

### Memory (RAM)

More memory reduces disk access and improves caching.

---

### Database Performance

Slow database queries reduce throughput.

Indexes and query optimization help improve it.

---

### Network Bandwidth

Limited bandwidth restricts the number of requests that can be handled.

---

### Application Design

Efficient algorithms and asynchronous processing improve throughput.

---

### Load Balancing

Distributing requests across multiple servers increases overall throughput.

---

# Improving Throughput

Common techniques include:

* Horizontal Scaling
* Load Balancing
* Caching
* Database Indexing
* Asynchronous Processing
* Connection Pooling
* Efficient Query Design

Example:

```text id="tp7"
Users

↓

Load Balancer

↓

Server 1

Server 2

Server 3
```

Each server contributes to the total throughput.

---

# Real-World Example

## YouTube

Millions of users stream videos simultaneously.

To achieve high throughput:

* CDN caches videos.
* Requests are distributed globally.
* Multiple servers process requests in parallel.

---

## Payment Gateway

A payment platform may need to process:

```text id="tp8"
50,000 Transactions

↓

1 Second
```

High throughput ensures payments are processed without delays.

---

## Search Engine

Google processes billions of search queries every day.

Distributed infrastructure enables extremely high throughput.

---

# Best Practices

* Use caching to reduce repeated work.
* Optimize database queries.
* Scale horizontally.
* Reduce unnecessary network calls.
* Use asynchronous processing where possible.
* Continuously monitor throughput metrics.

---

# Quick Revision

```text id="tp9"
Throughput

↓

Work Done

↓

Requests/Second

Measures

✔ RPS

✔ TPS

✔ QPS

Improve Using

✔ Load Balancer

✔ Cache

✔ Indexes

✔ Horizontal Scaling

Goal

↓

Handle More Users
```

---

# Key Takeaways

* **Throughput** measures the number of requests or operations a system can process in a given time.
* It is commonly expressed as **RPS, TPS, or QPS**.
* Higher throughput allows systems to serve more users and process more work simultaneously.
* Factors such as CPU, memory, database performance, network bandwidth, and application design directly impact throughput.
* Techniques like **horizontal scaling, load balancing, caching, and query optimization** are commonly used to improve throughput.
* Throughput is one of the most important performance metrics considered during system design and capacity planning.

---

> **Next Topic:** `05-Latency.md`
