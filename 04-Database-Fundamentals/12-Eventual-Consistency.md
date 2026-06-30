# Eventual Consistency

> *"Eventual Consistency is a consistency model used in distributed systems where all replicas eventually converge to the same data if no new updates occur."*

---

# Table of Contents

* What is Eventual Consistency?
* Why Do We Need Eventual Consistency?
* Strong Consistency vs Eventual Consistency
* How Eventual Consistency Works
* Replication Process
* Conflict Resolution
* Real-World Examples
* Advantages & Disadvantages
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Eventual Consistency?

**Eventual Consistency** is a consistency model used in distributed databases where updates are **not immediately visible** to every replica.

Instead:

* One replica is updated first.
* The update propagates to other replicas asynchronously.
* After some time, all replicas contain the same data.

If no new updates occur, every replica eventually becomes consistent.

---

# Why Do We Need Eventual Consistency?

Modern applications run across multiple servers distributed around the world.

Example:

```text id="ec1"
India Server

||

USA Server

||

Europe Server
```

Updating every server simultaneously would:

* Increase latency
* Reduce availability
* Increase network overhead

Instead, systems update replicas gradually.

---

# Strong Consistency vs Eventual Consistency

## Strong Consistency

Every client immediately sees the latest data.

```text id="ec2"
Write

↓

All Servers Updated

↓

Read Latest Value
```

Advantages:

* Always correct
* No stale data

Disadvantages:

* Higher latency
* Lower availability during failures

---

## Eventual Consistency

Updates propagate asynchronously.

```text id="ec3"
Write

↓

Primary Replica Updated

↓

Replication

↓

Other Replicas Updated

↓

Eventually Consistent
```

Advantages:

* High availability
* Better scalability

---

# How Eventual Consistency Works

Suppose a user updates their profile picture.

```text id="ec4"
Client

↓

Primary Server Updated

↓

Replication Begins

↓

Replica A Updated

↓

Replica B Updated

↓

Replica C Updated
```

For a short period, some users may still see the old profile picture.

Eventually, all users see the updated version.

---

# Replication Process

```text id="ec5"
Client

↓

Primary Node

↓

Replica 1

↓

Replica 2

↓

Replica 3
```

Replication usually occurs asynchronously.

---

# Conflict Resolution

Sometimes two users update the same data simultaneously.

Distributed databases use various strategies to resolve conflicts.

### Last Write Wins (LWW)

The most recent update replaces earlier updates.

Example:

```text id="ec6"
10:00

Alice Updates Profile

↓

10:01

Bob Updates Profile

↓

Bob's Update Wins
```

---

### Version Numbers

Each update increases a version number.

The database uses version information to determine the latest record.

---

### Vector Clocks

Some distributed databases track update history using vector clocks.

This helps detect conflicting updates before resolving them.

---

# Real-World Examples

## Social Media

You change your profile picture.

Your friend in another country may continue seeing the old picture for a few seconds.

Eventually, everyone sees the new picture.

---

## DNS

When a domain's IP address changes:

```text id="ec7"
Old IP

↓

DNS Propagation

↓

New IP
```

Different DNS servers update at different times.

---

## Amazon Shopping Cart

Items added on one device may take a short time to appear on another device.

---

## Cassandra

Apache Cassandra uses eventual consistency to achieve high availability and scalability.

---

# Advantages

* High availability.
* Excellent scalability.
* Better fault tolerance.
* Faster write operations.
* Supports geographically distributed systems.

---

# Disadvantages

* Temporary stale data.
* More complex application logic.
* Conflict resolution required.
* Not suitable for financial transactions.

---

# Best Practices

* Use eventual consistency only where temporary inconsistency is acceptable.
* Design applications to tolerate stale reads.
* Implement conflict resolution strategies.
* Clearly define consistency requirements before choosing a database.

---

# Interview Questions

* What is Eventual Consistency?
* Difference between Strong Consistency and Eventual Consistency?
* Why do distributed databases use Eventual Consistency?
* What is asynchronous replication?
* What is Last Write Wins?
* Give examples of systems using Eventual Consistency.
* Why isn't Eventual Consistency suitable for banking?
* How does Eventual Consistency improve scalability?

---

# Quick Revision

```text id="ec8"
Eventual Consistency

↓

Write Data

↓

Primary Updated

↓

Asynchronous Replication

↓

Replicas Updated

↓

All Nodes Eventually Consistent

Benefits

✔ High Availability

✔ Horizontal Scaling

✔ Fault Tolerance

Challenges

✖ Temporary Stale Data

✖ Conflict Resolution
```

---

# Key Takeaways

* **Eventual Consistency** allows distributed databases to remain highly available while synchronizing data over time.
* Updates are propagated **asynchronously**, meaning different replicas may temporarily hold different values.
* Once replication completes and no further updates occur, all replicas converge to the same state.
* Eventual consistency is ideal for **social media, content delivery, IoT, recommendation systems, and globally distributed applications**, where slight delays in data synchronization are acceptable.
* Understanding eventual consistency is fundamental for designing scalable distributed systems and choosing the right database architecture.

---

# 🎉 Database Fundamentals Complete

You have now completed **04 - Database Fundamentals**.

## Topics Covered

* ✅ SQL Fundamentals
* ✅ ACID Properties
* ✅ Transactions
* ✅ Normalization
* ✅ Indexes
* ✅ Joins
* ✅ Query Optimization
* ✅ Isolation Levels
* ✅ NoSQL Databases
* ✅ CAP Theorem
* ✅ BASE
* ✅ Eventual Consistency

These topics form the foundation for designing efficient, reliable, and scalable data storage systems. You now understand how databases ensure correctness, optimize performance, and scale across distributed environments.

---



This section introduces the core concepts required to build systems that can handle millions of users while remaining fast, reliable, and resilient.
