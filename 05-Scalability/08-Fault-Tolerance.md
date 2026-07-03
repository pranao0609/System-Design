# Fault Tolerance

> *"Fault Tolerance is the ability of a system to continue operating correctly even when one or more components fail."*

---

# Table of Contents

* What is Fault Tolerance?
* Why Do We Need Fault Tolerance?
* Fault Tolerance vs High Availability
* Types of Failures
* How Fault Tolerance Works
* Fault Tolerance Techniques
* Fault Tolerance in Distributed Systems
* Real-World Examples
* Advantages & Disadvantages
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Fault Tolerance?

**Fault Tolerance** is the capability of a system to continue functioning despite failures of hardware, software, networks, or individual services.

Instead of stopping completely, the system detects failures and continues operating using redundant components.

Example:

```text id="ft1"
Server A

↓

Fails

↓

Server B

Continues Processing Requests
```

---

# Why Do We Need Fault Tolerance?

Imagine an online shopping application.

```text id="ft2"
Customer

↓

Place Order

↓

Application Server Crashes
```

Without fault tolerance:

```text id="ft3"
Order Failed
```

With fault tolerance:

```text id="ft4"
Traffic

↓

Redirected

↓

Healthy Server

↓

Order Completed
```

Users experience little or no interruption.

---

# Fault Tolerance vs High Availability

| Fault Tolerance                   | High Availability                      |
| --------------------------------- | -------------------------------------- |
| Continues working during failures | Minimizes downtime                     |
| Focus on handling failures        | Focus on keeping the service available |
| Often requires redundancy         | Uses redundancy and failover           |
| Designed to survive failures      | Designed to recover quickly            |

Fault tolerance aims for **continuous operation**, while high availability aims for **minimal interruption**.

---

# Types of Failures

Common failures include:

### Hardware Failure

* Disk failure
* CPU failure
* Memory failure

---

### Software Failure

* Bugs
* Crashes
* Memory leaks

---

### Network Failure

* Packet loss
* Router failure
* Cable failure

---

### Human Error

* Incorrect deployment
* Configuration mistakes
* Accidental data deletion

---

### Data Center Failure

* Power outage
* Fire
* Natural disasters

---

# How Fault Tolerance Works

A fault-tolerant architecture includes redundant components.

```text id="ft5"
Users

↓

Load Balancer

↓

Server A

Server B

Server C

↓

Database Cluster
```

If one server fails:

* Health checks detect the failure.
* Traffic is redirected to healthy servers.
* Service continues without interruption.

---

# Fault Tolerance Techniques

## Redundancy

Maintain multiple copies of servers or services.

---

## Replication

Store multiple copies of data across different nodes.

---

## Automatic Failover

Switch traffic automatically to a healthy component.

```text id="ft6"
Primary

↓

Failure

↓

Secondary

Automatically Activated
```

---

## Health Checks

Continuously verify whether components are functioning correctly.

Unhealthy components are removed from service.

---

## Data Backup

Regular backups protect against permanent data loss.

---

## Retry Mechanisms

Applications retry temporary failures before reporting an error.

---

## Circuit Breakers

Prevent repeated requests to failing services, allowing them time to recover.

---

# Fault Tolerance in Distributed Systems

Modern distributed systems achieve fault tolerance using:

* Replication
* Consensus Algorithms
* Distributed Storage
* Multiple Availability Zones
* Multiple Data Centers

Example:

```text id="ft7"
Region A

↓

Region B

↓

Region C
```

If one region becomes unavailable, traffic is routed to another.

---

# Real-World Examples

## Google

Search services continue operating even when individual servers fail.

---

## Netflix

If one microservice fails, others continue functioning while fallback mechanisms handle failures.

---

## Amazon

Data is replicated across multiple Availability Zones to protect against infrastructure failures.

---

## Banking

Transaction systems use redundant infrastructure to ensure continuous service.

---

# Advantages

* High system resilience.
* Reduced downtime.
* Better user experience.
* Improved business continuity.
* Increased system reliability.

---

# Disadvantages

* Higher infrastructure cost.
* Increased architectural complexity.
* More monitoring required.
* Data synchronization challenges.

---

# Best Practices

* Eliminate single points of failure.
* Use redundant infrastructure.
* Replicate critical data.
* Implement health checks.
* Automate failover.
* Test disaster recovery regularly.
* Monitor system health continuously.

---

# Quick Revision

```text id="ft8"
Fault Tolerance

↓

Failure Occurs

↓

Detect Failure

↓

Failover

↓

Continue Service

Techniques

✔ Redundancy

✔ Replication

✔ Health Checks

✔ Failover

✔ Backups

✔ Retry

✔ Circuit Breaker
```

---

# Key Takeaways

* **Fault Tolerance** enables systems to continue operating despite component failures.
* It relies on **redundancy, replication, health checks, automatic failover, retries, and backups** to minimize service disruption.
* Fault tolerance is a fundamental characteristic of modern distributed systems, cloud platforms, and mission-critical applications.
* While it improves reliability and resilience, it also increases infrastructure costs and architectural complexity.
* Designing for failure is a core principle of system design—assume that components will eventually fail and build systems that can recover gracefully.

---

# 🎉 Scalability Fundamentals Complete

You have now completed **05 - Scalability Fundamentals**.

## Topics Covered

* ✅ Horizontal Scaling
* ✅ Vertical Scaling
* ✅ Capacity Planning
* ✅ Throughput
* ✅ Latency
* ✅ Availability
* ✅ Reliability
* ✅ Fault Tolerance

These concepts form the foundation of building systems that can scale from thousands to millions of users while maintaining high performance, reliability, and resilience.

---
