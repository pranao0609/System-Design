# Latency

> *"Latency is the time taken for a request to travel from the client to the server, be processed, and return a response. It measures how quickly a system responds to a request."*

---

# Table of Contents

* What is Latency?
* Why is Latency Important?
* Latency vs Throughput
* Types of Latency
* Factors Affecting Latency
* How to Reduce Latency
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Latency?

**Latency** is the delay between sending a request and receiving a response.

It is usually measured in:

* Milliseconds (ms)
* Microseconds (µs)

Example:

```text id="lat1"
User Clicks Button

↓

Request Sent

↓

Server Processes

↓

Response Received

↓

150 ms
```

Lower latency means a faster and more responsive system.

---

# Why is Latency Important?

Suppose you search on Google.

```text id="lat2"
Search

↓

Response in

80 ms
```

The search feels instant.

Now imagine:

```text id="lat3"
Search

↓

Response in

5 Seconds
```

The user experience becomes poor.

Even small increases in latency can significantly impact user satisfaction.

---

# Latency vs Throughput

| Latency                     | Throughput                   |
| --------------------------- | ---------------------------- |
| Time to process one request | Number of requests processed |
| Lower is better             | Higher is better             |
| Measured in ms              | Measured in RPS/TPS          |

Example:

```text id="lat4"
Server

Latency

100 ms

Throughput

5000 RPS
```

A system can have:

* Low latency and low throughput.
* High throughput and higher latency.

The goal is to optimize both.

---

# Types of Latency

## 1. Network Latency

Time taken for data to travel across the network.

Affected by:

* Distance
* Internet speed
* Routing

---

## 2. Processing Latency

Time spent by the server executing business logic.

Example:

* Authentication
* Payment processing
* Recommendation algorithms

---

## 3. Database Latency

Time required to execute database queries.

Factors:

* Missing indexes
* Complex JOINs
* Large tables

---

## 4. Disk Latency

Time required to read or write data from storage.

SSDs provide significantly lower latency than HDDs.

---

# Factors Affecting Latency

Several components contribute to total latency.

```text id="lat5"
Client

↓

Network

↓

Load Balancer

↓

Application Server

↓

Database

↓

Response
```

Total latency is the sum of delays across all components.

---

# How to Reduce Latency

### Caching

Store frequently accessed data closer to users.

Example:

* Redis
* CDN

---

### Load Balancing

Distribute requests evenly across servers.

---

### Database Optimization

* Use indexes.
* Optimize queries.
* Reduce unnecessary JOINs.

---

### Horizontal Scaling

Increase the number of servers to reduce processing delays.

---

### Content Delivery Networks (CDNs)

Serve static content from geographically closer locations.

---

### Asynchronous Processing

Move time-consuming tasks (emails, notifications, image processing) to background workers.

---

# Real-World Examples

## Netflix

Videos are served from nearby CDN servers to reduce latency.

---

## Google Search

Optimized infrastructure returns search results in milliseconds.

---

## Online Gaming

Low latency is essential to ensure smooth gameplay and quick response to player actions.

---

## Video Calls

Applications like Zoom and Google Meet require low latency to maintain natural conversations.

---

# Best Practices

* Keep servers close to users.
* Use caching extensively.
* Optimize database queries.
* Minimize network hops.
* Compress data before transmission.
* Monitor latency continuously.

---

# Quick Revision

```text id="lat6"
Latency

↓

Time Taken

↓

Request

↓

Response

Types

✔ Network

✔ Processing

✔ Database

✔ Disk

Reduce Using

✔ Cache

✔ CDN

✔ Indexes

✔ Load Balancer

✔ Horizontal Scaling
```

---

# Key Takeaways

* **Latency** measures the time taken to complete a single request, from the client to the server and back.
* Lower latency leads to faster, more responsive applications and better user experience.
* Total latency is influenced by **network**, **processing**, **database**, and **storage** delays.
* Techniques such as **caching, CDNs, load balancing, database optimization, and horizontal scaling** are commonly used to reduce latency.
* Optimizing latency is critical for applications such as search engines, streaming platforms, online gaming, and real-time communication systems.

---

> **Next Topic:** `06-Availability.md`
