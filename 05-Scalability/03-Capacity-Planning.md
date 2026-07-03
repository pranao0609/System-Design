# Capacity Planning

> *"Capacity Planning is the process of estimating the resources required—such as CPU, memory, storage, bandwidth, and servers—to ensure a system can handle current and future workloads efficiently."*

---

# Table of Contents

* What is Capacity Planning?
* Why is Capacity Planning Important?
* Key Metrics
* Capacity Estimation
* Storage Estimation
* Bandwidth Estimation
* Memory Estimation
* CPU Estimation
* Real-World Example
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Capacity Planning?

**Capacity Planning** is the process of estimating how much infrastructure a system needs to support its expected workload.

Resources include:

* CPU
* Memory (RAM)
* Storage
* Network Bandwidth
* Number of Servers

It helps ensure that the system remains fast, reliable, and scalable as user demand grows.

---

# Why is Capacity Planning Important?

Suppose an application expects:

```text id="cp1"
10 Million Users
```

Without proper planning:

* Servers may crash.
* Databases become overloaded.
* High response times.
* Poor user experience.

Capacity planning helps prevent these issues before deployment.

---

# Key Metrics

Before designing a system, estimate:

* Number of users
* Daily Active Users (DAU)
* Requests Per Second (RPS)
* Read-to-Write Ratio
* Storage Requirements
* Network Bandwidth
* Peak Traffic

These values guide infrastructure decisions.

---

# Capacity Estimation

Example:

Daily Active Users:

```text id="cp2"
1 Million Users
```

Each user sends:

```text id="cp3"
10 Requests/Day
```

Total Requests:

```text id="cp4"
1,000,000 × 10

=

10,000,000 Requests/Day
```

Average Requests Per Second (RPS):

```text id="cp5"
10,000,000

÷

86,400

≈

116 RPS
```

Peak traffic is usually several times higher than the average, so systems should be designed to handle peak RPS rather than average RPS.

---

# Storage Estimation

Suppose:

Each uploaded image:

```text id="cp6"
2 MB
```

Daily uploads:

```text id="cp7"
100,000 Images
```

Storage needed per day:

```text id="cp8"
2 MB × 100,000

=

200 GB/Day
```

Annual storage:

```text id="cp9"
200 GB × 365

≈

73 TB
```

Always include additional storage for:

* Backups
* Replication
* Logs

---

# Bandwidth Estimation

Suppose:

Average response size:

```text id="cp10"
500 KB
```

Peak traffic:

```text id="cp11"
1000 Requests/Second
```

Bandwidth:

```text id="cp12"
500 KB × 1000

=

500 MB/s
```

This helps determine required network capacity.

---

# Memory Estimation

Estimate RAM requirements for:

* Running applications
* Database caching
* Session storage
* In-memory caches (e.g., Redis)

Example:

```text id="cp13"
Application

4 GB

+

Cache

8 GB

+

OS

2 GB

=

14 GB RAM
```

Provision additional headroom for traffic spikes.

---

# CPU Estimation

CPU requirements depend on:

* Number of requests
* Complexity of operations
* Background jobs
* Data processing

Example:

```text id="cp14"
Server Capacity

500 Requests/Second

Need

2000 Requests/Second

↓

4 Servers Required
```

---

# Real-World Example

Suppose you're designing a photo-sharing application.

Expected workload:

```text id="cp15"
Users

10 Million

↓

Uploads

500,000 Photos/Day

↓

Average Photo

5 MB

↓

Daily Storage

2.5 TB
```

Infrastructure planning would include:

* Object Storage
* CDN
* Database
* Cache
* Load Balancers
* Multiple Application Servers

---

# Capacity Planning Checklist

Before building a large-scale system, estimate:

✔ Number of Users

✔ Peak Concurrent Users

✔ Read/Write Ratio

✔ Requests Per Second

✔ Storage Growth

✔ Memory Requirements

✔ CPU Requirements

✔ Network Bandwidth

✔ Backup Strategy

✔ Future Growth

---

# Best Practices

* Design for peak traffic, not average traffic.
* Plan for future growth.
* Include redundancy and backups.
* Monitor resource utilization continuously.
* Add safety margins (20–50%) to estimates.
* Revisit estimates as application usage changes.

---

# Quick Revision

```text id="cp16"
Capacity Planning

↓

Estimate Resources

Resources

✔ CPU

✔ RAM

✔ Storage

✔ Bandwidth

Metrics

Users

↓

RPS

↓

Storage

↓

Network

Goal

↓

Scalable

Reliable

High Performance
```

---

# Key Takeaways

* **Capacity Planning** estimates the infrastructure required to support current and future workloads.
* Key metrics include **Users, RPS, Storage, CPU, Memory, and Bandwidth**.
* Systems should always be designed for **peak traffic**, not average traffic.
* Proper planning reduces downtime, improves performance, and simplifies scaling.
* Capacity Planning is one of the first steps in designing any large-scale distributed system and is frequently discussed in system design interviews.

---

> **Next Topic:** `04-Throughput.md`
