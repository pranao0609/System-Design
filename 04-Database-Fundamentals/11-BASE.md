# BASE

> *"BASE is a consistency model used in many distributed NoSQL databases. It prioritizes high availability and scalability over immediate consistency, allowing data to become consistent over time."*

---

# Table of Contents

* What is BASE?
* Why Do We Need BASE?
* BASE vs ACID
* Basically Available
* Soft State
* Eventual Consistency
* How BASE Works
* Real-World Examples
* Advantages & Disadvantages
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is BASE?

**BASE** is a consistency model commonly used in distributed NoSQL databases.

BASE stands for:

* **B** → Basically Available
* **A** → Soft State
* **S** → Eventual Consistency

Unlike **ACID**, which prioritizes strong consistency, BASE prioritizes:

* High Availability
* Horizontal Scalability
* Fault Tolerance

BASE is commonly used in large-scale distributed systems where temporary inconsistencies are acceptable.

---

# Why Do We Need BASE?

Imagine a social media platform with millions of users.

If one server becomes temporarily unavailable, should the entire platform stop working?

Most users would prefer:

* Slightly outdated data
* Instead of complete downtime

BASE enables systems to remain available even during failures.

---

# BASE vs ACID

| ACID                       | BASE                                   |
| -------------------------- | -------------------------------------- |
| Strong Consistency         | Eventual Consistency                   |
| Immediate Correctness      | Temporary Inconsistency Allowed        |
| Best for SQL Databases     | Best for NoSQL Databases               |
| Prioritizes Data Integrity | Prioritizes Availability & Scalability |

---

# B – Basically Available

The system remains available even if some nodes fail.

Example:

```text id="base1"
Server A

Down

↓

Server B

Still Responds
```

Users continue receiving responses, though the data may not always be the most recent.

---

# A – Soft State

The system's state may change over time even without new user input.

Why?

Because replicas are continuously synchronizing in the background.

Example:

```text id="base2"
Node A

Updated

↓

Node B

Updating...

↓

Node C

Updating...
```

The system is temporarily in an intermediate state.

---

# S – Eventual Consistency

If no new updates occur, all replicas will eventually converge to the same value.

Example:

```text id="base3"
Time T0

Server A = 100

Server B = 90

↓

Replication

↓

Time T1

Server A = 100

Server B = 100
```

Consistency is achieved over time rather than immediately.

---

# How BASE Works

Consider three distributed database replicas.

```text id="base4"
Client

↓

Node A

↓

Replicate

↓

Node B

↓

Replicate

↓

Node C
```

When the client writes data:

* One node is updated first.
* Other nodes synchronize asynchronously.

This approach improves availability and write performance.

---

# Real-World Examples

## Social Media

A newly uploaded post may appear immediately for the author but take a few seconds to appear for other users.

Temporary inconsistency is acceptable.

---

## Amazon Shopping Cart

Items added to a shopping cart may briefly appear out of sync across devices but eventually synchronize.

---

## DNS

When a DNS record changes:

```text id="base5"
Old IP

↓

DNS Propagation

↓

New IP
```

Different DNS servers update at different times, eventually converging.

---

## Distributed Cache

Caches such as Redis replicas may temporarily contain different values before synchronization.

---

# Advantages

* High availability.
* Excellent horizontal scalability.
* Better fault tolerance.
* Fast write performance.
* Well-suited for distributed systems.

---

# Disadvantages

* Temporary data inconsistency.
* Complex conflict resolution.
* Not suitable for financial transactions.
* Applications must handle stale data.

---

# When to Use BASE

Use BASE when:

* High availability is critical.
* Large-scale distributed systems are required.
* Temporary inconsistencies are acceptable.
* Horizontal scaling is a priority.

Examples:

* Social Networks
* Streaming Platforms
* Recommendation Systems
* Messaging Systems
* IoT Platforms

---

# Interview Questions

* What does BASE stand for?
* Difference between ACID and BASE?
* What is Soft State?
* What is Eventual Consistency?
* Why do NoSQL databases use BASE?
* Give examples of BASE systems.
* Why isn't BASE suitable for banking?
* How does BASE improve availability?

---

# Quick Revision

```text id="base6"
BASE

↓

Basically Available

↓

Soft State

↓

Eventual Consistency

Focus

✔ High Availability

✔ Scalability

✔ Fault Tolerance

Common In

MongoDB

Cassandra

DynamoDB

CouchDB
```

---

# Key Takeaways

* **BASE** is a consistency model designed for distributed systems that prioritize **availability** and **scalability** over immediate consistency.
* It consists of **Basically Available**, **Soft State**, and **Eventual Consistency**.
* BASE allows temporary inconsistencies while ensuring that replicas eventually synchronize.
* It is widely used in **NoSQL databases** and large-scale distributed applications where continuous service is more important than immediate consistency.
* Understanding BASE is essential for designing modern cloud-native and distributed systems.

---

> **Next Topic:** `12-Eventual-Consistency.md`
