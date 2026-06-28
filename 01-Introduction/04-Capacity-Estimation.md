# Capacity Estimation

> *"Before designing a system, estimate its scale. Capacity estimation helps determine how much infrastructure, storage, bandwidth, and compute resources your system will need."*

---

# Table of Contents

* What is Capacity Estimation?
* Why is Capacity Estimation Important?
* Key Terminologies
* Steps in Capacity Estimation
* Estimating Traffic
* Estimating Storage
* Estimating Bandwidth
* Estimating Compute Resources
* Example: URL Shortener
* Example: Instagram
* Best Practices
* Common Mistakes
* Interview Perspective
* Quick Revision
* Key Takeaways

---

# What is Capacity Estimation?

Capacity Estimation is the process of estimating the **resources required** for a system before designing its architecture.

These resources include:

* Number of Users
* Requests Per Second (RPS)
* Queries Per Second (QPS)
* Storage
* Bandwidth
* CPU
* Memory
* Network Throughput

Instead of guessing, engineers use rough calculations to ensure the system can handle expected traffic and future growth.

> **Capacity estimation is about making informed assumptions, not exact predictions.**

---

# Why is Capacity Estimation Important?

Without estimating the expected scale, you may:

* Under-provision infrastructure, causing outages.
* Over-provision resources, increasing costs.
* Choose the wrong database or architecture.
* Create bottlenecks that are difficult to fix later.

Capacity estimation helps answer questions like:

* How many servers are needed?
* Will a single database be enough?
* Should we introduce caching?
* How much storage will we need in one year?
* What internet bandwidth is required?

---

# Key Terminologies

## Daily Active Users (DAU)

The number of unique users who use the application in a single day.

Example:

```text
1,000,000 users/day
```

---

## Monthly Active Users (MAU)

The number of unique users who use the application in a month.

Example:

```text
20,000,000 users/month
```

---

## Requests Per Second (RPS)

The average number of requests the system receives every second.

### Formula

```text
RPS = Total Requests Per Day / 86,400
```

Example:

```text
5,000,000 Requests / Day

RPS

= 5,000,000 / 86,400

≈ 58 Requests/Second
```

---

## Queries Per Second (QPS)

The number of database queries executed every second.

Not every API request results in a database query. Some requests may be served from a cache.

---

## Read-to-Write Ratio

Shows how often data is read compared to how often it is written.

Examples:

```text
Instagram Feed

Reads : Writes

100 : 1
```

```text
Banking System

Reads : Writes

3 : 1
```

A read-heavy system benefits significantly from caching.

---

# Steps in Capacity Estimation

```text
Gather Requirements
        │
        ▼
Estimate Users
        │
        ▼
Estimate Requests
        │
        ▼
Estimate Storage
        │
        ▼
Estimate Bandwidth
        │
        ▼
Estimate Compute
        │
        ▼
Choose Architecture
```

---

# Estimating Traffic

Suppose we are designing a social media platform.

### Assumptions

* 10 Million Registered Users
* 1 Million Daily Active Users
* Each user makes 20 requests/day

### Total Requests

```text
1,000,000 × 20

=

20,000,000 Requests/Day
```

### Requests Per Second

```text
20,000,000

÷

86,400

≈

231 RPS
```

For production systems, add a safety margin (often 2–5×) to account for traffic spikes.

---

# Peak Traffic

Traffic is rarely uniform throughout the day.

Example:

```text
Average RPS

230

Peak RPS

≈ 3 × Average

≈ 690 RPS
```

Always design for **peak load**, not just the average.

---

# Estimating Storage

Suppose:

* 1 Million users
* Each uploads 2 photos/day
* Average image size = 5 MB

### Daily Storage

```text
1,000,000

×

2

×

5 MB

=

10 TB/day
```

### Yearly Storage

```text
10 TB

×

365

≈

3.65 PB/year
```

Storage estimates influence the choice of databases and object storage systems.

---

# Estimating Bandwidth

Bandwidth depends on the amount of data transferred.

Example:

* Average response size = 200 KB
* 700 Peak RPS

```text
700 × 200 KB

=

140,000 KB/s

≈

137 MB/s
```

This helps estimate network requirements and CDN usage.

---

# Estimating Compute Resources

Suppose:

* One server handles 500 RPS.

Peak traffic:

```text
2,000 RPS
```

Servers required:

```text
2,000

÷

500

=

4 Servers
```

To improve reliability:

```text
4 Servers

+

1 Backup

=

5 Servers
```

In practice, autoscaling and redundancy are also considered.

---

# Example 1: URL Shortener

### Assumptions

* 50 Million Users
* 5 Million DAU
* 4 Short URLs/User/Day

### Total Requests

```text
5M × 4

=

20 Million Requests/Day
```

### RPS

```text
20M

÷

86,400

≈

231 RPS
```

### Storage

Assume each URL record occupies 500 bytes.

```text
20M × 500 Bytes

=

10 GB/day
```

Yearly:

```text
10 GB × 365

≈

3.65 TB
```

This estimate helps determine database sizing.

---

# Example 2: Instagram

### Assumptions

* 100 Million DAU
* 30 Photos Uploaded/User/Month
* Average Photo = 4 MB

Daily uploads:

```text
100M

×

1 Photo/Day

×

4 MB

=

400 TB/day
```

This demonstrates why systems like Instagram rely on distributed object storage and CDNs.

---

# Capacity Estimation Checklist

Before finalizing a design, estimate:

* Daily Active Users (DAU)
* Monthly Active Users (MAU)
* Peak Concurrent Users
* Read-to-Write Ratio
* Requests Per Second (RPS)
* Queries Per Second (QPS)
* Storage Growth
* Network Bandwidth
* CPU Requirements
* Memory Requirements
* Cache Size
* Number of Servers
* Backup & Redundancy

---

# Best Practices

* Clearly state all assumptions.
* Round numbers for quick calculations.
* Design for peak traffic.
* Plan for future growth.
* Include redundancy and failover.
* Revisit estimates as requirements evolve.

---

# Common Mistakes

* Ignoring peak traffic.
* Forgetting storage growth.
* Underestimating bandwidth.
* Assuming one server is enough.
* Ignoring backups and redundancy.
* Treating estimates as exact values.

---

# Interview Perspective

In system design interviews, capacity estimation demonstrates that you can reason quantitatively.

A common flow is:

1. State assumptions.
2. Estimate users and requests.
3. Calculate RPS and peak RPS.
4. Estimate storage and bandwidth.
5. Use the estimates to justify architectural choices.

You are **not** expected to produce perfect numbers. Interviewers value logical assumptions and clear reasoning.

---

# Quick Revision

```text
Capacity Estimation

Users
│
├── DAU
├── MAU
└── Concurrent Users

Traffic
│
├── Requests/Day
├── RPS
├── QPS
└── Peak RPS

Storage
│
├── Daily Growth
├── Monthly Growth
└── Yearly Growth

Resources
│
├── CPU
├── Memory
├── Bandwidth
├── Cache
└── Servers
```

### Important Formulas

```text
RPS = Requests Per Day ÷ 86,400

Storage = Number of Objects × Size of Each Object

Bandwidth = RPS × Response Size

Servers Required = Peak RPS ÷ Capacity per Server
```

---

# Key Takeaways

* Capacity estimation is the foundation of scalable system design.
* Estimate users, requests, storage, bandwidth, and compute resources before choosing an architecture.
* Design for **peak traffic**, not average traffic.
* Make reasonable assumptions and communicate them clearly.
* Use capacity estimates to justify choices such as caching, load balancing, replication, and database selection.

---

> **Next Topic:** `05-Functional-vs-NonFunctional-Requirements.md`
