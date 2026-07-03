# Availability

> *"Availability is the ability of a system to remain operational and accessible to users, even in the presence of failures."*

---

# Table of Contents

* What is Availability?
* Why is Availability Important?
* Availability Percentage
* Measuring Availability
* High Availability (HA)
* Causes of Downtime
* Improving Availability
* Availability vs Reliability
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Availability?

**Availability** measures the percentage of time a system is **up, running, and accessible** to users.

If users can successfully access the application whenever they need it, the system is considered highly available.

Example:

```text id="av1"
Users

↓

Application

↓

Available

✔
```

---

# Why is Availability Important?

Imagine an online banking application.

```text id="av2"
Customer

↓

Transfer Money

↓

Server Down
```

The transaction cannot be completed.

For critical systems, even a few minutes of downtime can result in:

* Revenue loss
* Poor user experience
* Customer dissatisfaction
* Damage to brand reputation

---

# Availability Percentage

Availability is usually expressed as a percentage.

Formula:

```text id="av3"
Availability

=

Uptime

÷

(Uptime + Downtime)

× 100%
```

Example:

```text id="av4"
Uptime

364 Days

Downtime

1 Day

↓

Availability

99.73%
```

---

# The "Nines" of Availability

Higher availability is commonly described using the number of **"9s"**.

| Availability | Approximate Downtime per Year |
| ------------ | ----------------------------- |
| 99%          | ~3.65 Days                    |
| 99.9%        | ~8.76 Hours                   |
| 99.99%       | ~52.6 Minutes                 |
| 99.999%      | ~5.26 Minutes                 |

The more **9s**, the less downtime users experience.

---

# High Availability (HA)

A **High Availability (HA)** system continues serving users even if some components fail.

Example:

```text id="av5"
          Load Balancer
               │
      ┌────────┴────────┐
      ▼                 ▼
   Server A         Server B
```

If **Server A** fails, traffic is automatically routed to **Server B**.

---

# Causes of Downtime

Common reasons for system unavailability include:

* Hardware failures
* Software bugs
* Database failures
* Network outages
* Power failures
* Human errors
* Cyberattacks

Designing for these failures improves availability.

---

# Improving Availability

### Redundancy

Deploy multiple servers instead of relying on a single server.

---

### Load Balancing

Distribute requests across multiple servers.

---

### Replication

Maintain multiple copies of data across different servers or regions.

---

### Automatic Failover

When one server fails, another server automatically takes over.

```text id="av6"
Primary Server

↓

Failure

↓

Secondary Server Takes Over
```

---

### Health Checks

Continuously monitor servers and remove unhealthy instances from service.

---

### Geographic Distribution

Deploy services across multiple regions or data centers.

```text id="av7"
India

↓

USA

↓

Europe
```

If one region becomes unavailable, another can continue serving users.

---

# Availability vs Reliability

| Availability                 | Reliability                    |
| ---------------------------- | ------------------------------ |
| System is accessible         | System performs correctly      |
| Measures uptime              | Measures correctness over time |
| Focus on minimizing downtime | Focus on minimizing failures   |

A system can be highly available but not reliable if it frequently returns incorrect results.

---

# Real-World Examples

## Netflix

Streaming services continue operating even if individual servers fail.

---

## Amazon

During major sales events, traffic is routed to healthy servers to ensure continuous service.

---

## Google

Services are distributed across multiple data centers to maximize availability.

---

## Banking Systems

Critical components are replicated to minimize downtime.

---

# Best Practices

* Eliminate single points of failure.
* Use redundant infrastructure.
* Deploy automatic failover mechanisms.
* Monitor system health continuously.
* Perform regular backups.
* Test disaster recovery plans.

---

# Interview Questions

* What is Availability?
* How is Availability calculated?
* What is High Availability?
* What do "Five Nines" mean?
* Difference between Availability and Reliability?
* How do Load Balancers improve Availability?
* What is Failover?
* How can Availability be improved in distributed systems?

---

# Quick Revision

```text id="av8"
Availability

↓

System Uptime

↓

Availability %

↓

High Availability

Improve Using

✔ Load Balancer

✔ Replication

✔ Redundancy

✔ Failover

✔ Health Checks

Goal

↓

Minimal Downtime
```

---

# Key Takeaways

* **Availability** measures how often a system is operational and accessible to users.
* High Availability is achieved through **redundancy, replication, load balancing, and automatic failover**.
* Availability is commonly expressed using percentages such as **99.9% (Three Nines)** or **99.999% (Five Nines)**.
* Eliminating single points of failure is essential for building resilient distributed systems.
* Availability is a critical design consideration for cloud services, financial systems, streaming platforms, and other mission-critical applications.

---

> **Next Topic:** `07-Reliability.md`
