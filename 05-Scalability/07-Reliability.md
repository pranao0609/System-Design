# Reliability

> *"Reliability is the ability of a system to consistently perform its intended function correctly over time, even under varying workloads and failure conditions."*

---

# Table of Contents

* What is Reliability?
* Why is Reliability Important?
* Reliability vs Availability
* Characteristics of a Reliable System
* Measuring Reliability
* Improving Reliability
* Reliability in Distributed Systems
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Reliability?

**Reliability** measures whether a system performs **correctly and consistently** over time.

A reliable system:

* Produces correct results.
* Handles failures gracefully.
* Maintains data integrity.
* Recovers from unexpected errors.

Example:

```text id="rel1"
User

↓

Payment Request

↓

Correct Payment Processed

↓

Success
```

Even under heavy traffic or partial failures, the system should continue producing correct outcomes.

---

# Why is Reliability Important?

Imagine an online banking application.

```text id="rel2"
Transfer ₹1000

↓

Money Deducted

↓

Money Not Credited
```

The system is available, but it is **not reliable** because it produced an incorrect result.

Reliability is essential wherever correctness matters.

---

# Reliability vs Availability

| Reliability                 | Availability             |
| --------------------------- | ------------------------ |
| Correct operation           | System uptime            |
| Focuses on accuracy         | Focuses on accessibility |
| Produces valid results      | Accepts requests         |
| Prevents incorrect behavior | Prevents downtime        |

Example:

```text id="rel3"
System Running

↓

Returns Wrong Data

↓

Available

✖ Reliable
```

A system should ideally be both available and reliable.

---

# Characteristics of a Reliable System

A reliable system should have:

* Correctness
* Consistency
* Fault Recovery
* Data Integrity
* Predictable Behavior
* Error Handling

These properties help ensure that users receive accurate results.

---

# Measuring Reliability

Reliability is often evaluated using metrics such as:

* Failure Rate
* Error Rate
* Mean Time Between Failures (MTBF)
* Mean Time To Recovery (MTTR)
* Success Rate

Higher MTBF and lower MTTR generally indicate better reliability.

---

# Improving Reliability

## Redundancy

Deploy multiple servers so that failures do not interrupt service.

---

## Data Replication

Maintain multiple copies of important data.

---

## Backups

Regular backups enable recovery from accidental deletion or corruption.

---

## Monitoring

Continuously monitor:

* CPU
* Memory
* Network
* Errors
* Logs

to detect issues early.

---

## Automated Testing

Use:

* Unit Tests
* Integration Tests
* End-to-End Tests

to reduce software defects before deployment.

---

## Graceful Error Handling

Applications should handle failures without crashing.

Example:

```text id="rel4"
Database Failure

↓

Retry

↓

Fallback

↓

Error Message
```

instead of terminating unexpectedly.

---

# Reliability in Distributed Systems

Distributed systems improve reliability using:

* Replication
* Failover
* Consensus Algorithms
* Health Checks
* Automatic Recovery

Example:

```text id="rel5"
Client

↓

Load Balancer

↓

Server A

Server B

Server C

↓

Database Cluster
```

If one component fails, another continues processing requests.

---

# Real-World Examples

## Banking

Transactions must always produce correct balances.

Reliability is critical.

---

## Airline Reservation

Seat allocation must avoid duplicate bookings.

---

## E-Commerce

Orders should never be lost even if servers restart.

---

## Cloud Storage

Files should remain accessible and uncorrupted despite hardware failures.

---

# Best Practices

* Remove single points of failure.
* Validate all user input.
* Implement retries carefully.
* Use monitoring and alerting.
* Perform regular backups.
* Test disaster recovery procedures.
* Design for graceful degradation.

---

# Quick Revision

```text id="rel6"
Reliability

↓

Correct Results

↓

Consistent Operation

Improve Using

✔ Replication

✔ Backups

✔ Monitoring

✔ Testing

✔ Failover

Metrics

MTBF

↓

MTTR

↓

Failure Rate
```

---

# Key Takeaways

* **Reliability** measures a system's ability to consistently perform correctly over time.
* A reliable system produces accurate results, maintains data integrity, and recovers gracefully from failures.
* Reliability differs from availability: a system can be online yet still produce incorrect results.
* Techniques such as **replication, backups, monitoring, testing, and failover** significantly improve reliability.
* Reliability is essential for mission-critical systems such as banking, healthcare, aviation, cloud storage, and e-commerce.

---

> **Next Topic:** `08-Fault-Tolerance.md`
