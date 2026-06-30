# CAP Theorem

> *"The CAP Theorem states that a distributed system can guarantee at most two out of three properties: Consistency, Availability, and Partition Tolerance."*

---

# Table of Contents

* What is CAP Theorem?
* Why Do We Need CAP Theorem?
* The Three Properties
* Consistency (C)
* Availability (A)
* Partition Tolerance (P)
* CAP Trade-offs
* CA, CP, and AP Systems
* Real-World Examples
* CAP vs ACID
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is CAP Theorem?

The **CAP Theorem**, proposed by **Eric Brewer** in 2000 and formally proven by **Seth Gilbert** and **Nancy Lynch**, describes the trade-offs faced by **distributed systems**.

It states that during a **network partition**, a distributed system can provide **either Consistency or Availability, but not both**.

In practice:

```text id="cap1"
Consistency

Availability

Partition Tolerance

Choose Any Two

(CA)

(CP)

(AP)
```

---

# Why Do We Need CAP Theorem?

Modern applications run on multiple servers.

Example:

```text id="cap2"
Server A

||

Server B

||

Server C
```

If communication between servers fails, the system must decide:

* Should it continue serving requests?
* Or should it stop serving requests to avoid inconsistent data?

CAP helps answer this question.

---

# The Three Properties

```text id="cap3"
CAP

├── Consistency

├── Availability

└── Partition Tolerance
```

---

# Consistency (C)

Every client sees the **same data** at the same time.

Example:

```text id="cap4"
User A

Updates Balance

↓

User B

Immediately Sees Updated Balance
```

No stale or outdated data is returned.

---

# Availability (A)

Every request receives a response, even if some servers are unavailable.

Example:

```text id="cap5"
Server A

Down

↓

Server B

Still Responds
```

The response may not always contain the latest data.

---

# Partition Tolerance (P)

The system continues to operate even when communication between servers is interrupted.

Example:

```text id="cap6"
Server A

X

Network Failure

X

Server B
```

Even though the network is partitioned, the system remains operational.

---

# Understanding Network Partition

A **Network Partition** occurs when servers cannot communicate due to:

* Network failures
* Hardware failures
* Cable issues
* Router failures
* Data center outages

In distributed systems, partitions are inevitable.

---

# CAP Trade-offs

## CA (Consistency + Availability)

Provides:

* Strong consistency
* High availability

Cannot tolerate network partitions.

Suitable only for systems where partitions are extremely unlikely (e.g., a single-node database).

---

## CP (Consistency + Partition Tolerance)

Prioritizes:

* Consistency
* Partition tolerance

During a partition:

* Some requests may be rejected.
* Availability is sacrificed to maintain consistent data.

Examples:

* HBase
* ZooKeeper
* etcd

Suitable for:

* Banking
* Financial Systems
* Distributed Coordination

---

## AP (Availability + Partition Tolerance)

Prioritizes:

* Availability
* Partition tolerance

During a partition:

* The system continues serving requests.
* Data may be temporarily inconsistent.

Eventually, all replicas synchronize.

Examples:

* Cassandra
* DynamoDB
* CouchDB
* Riak

Suitable for:

* Social Media
* Streaming
* Recommendation Systems

---

# CAP Triangle

```text id="cap7"
          Consistency
              ▲
             / \
            /   \
           /     \
          /       \
         /         \
Availability ------- Partition Tolerance
```

In a partitioned network, you must choose between **Consistency** and **Availability**.

---

# Real-World Examples

## Banking System

```text id="cap8"
CP
```

Incorrect balances are unacceptable.

Consistency is more important than availability.

---

## WhatsApp

```text id="cap9"
AP
```

A message may arrive slightly later, but the service should remain available.

---

## Netflix

```text id="cap10"
AP
```

Temporary inconsistencies in recommendations are acceptable.

Keeping the service available is the priority.

---

## Distributed Lock Service

```text id="cap11"
CP
```

Only one client should acquire the lock at a time.

Consistency is essential.

---

# CAP vs ACID

| ACID                          | CAP                                           |
| ----------------------------- | --------------------------------------------- |
| Focuses on Transactions       | Focuses on Distributed Systems                |
| Single Database               | Multiple Distributed Nodes                    |
| Ensures Reliable Transactions | Explains Trade-offs During Network Partitions |
| Common in SQL Databases       | Common in Distributed Databases               |

---

# Common Misconception

Many people think you can always choose any two of the three properties.

In reality:

* **Partition Tolerance is mandatory** in distributed systems because network failures can happen.
* During a partition, the real choice is between:

  * **Consistency (CP)**
  * **Availability (AP)**

---

# Advantages

* Helps design scalable distributed systems.
* Explains trade-offs clearly.
* Guides database selection.
* Improves architecture decisions.

---

# Limitations

* Simplified theoretical model.
* Real systems often provide tunable consistency.
* Modern databases use hybrid approaches that balance CAP trade-offs.

---

# Interview Questions

* What is CAP Theorem?
* What does CAP stand for?
* Can a distributed system guarantee all three properties?
* What is a network partition?
* Difference between CP and AP systems?
* Why is Partition Tolerance unavoidable?
* Give examples of CP databases.
* Give examples of AP databases.
* Difference between CAP and ACID?

---

# Quick Revision

```text id="cap12"
CAP

↓

Consistency

↓

Availability

↓

Partition Tolerance

Choices

CA

CP

AP

Distributed Systems

↓

Network Partition

↓

Choose

Consistency

OR

Availability
```

---

# Key Takeaways

* **CAP Theorem** explains the trade-offs between **Consistency**, **Availability**, and **Partition Tolerance** in distributed systems.
* During a network partition, a distributed system must choose between maintaining **Consistency (CP)** or **Availability (AP)**.
* **CP systems** prioritize correctness and are suitable for banking and distributed coordination.
* **AP systems** prioritize continuous service and are common in social media, streaming, and large-scale web applications.
* CAP is a fundamental concept for designing distributed databases and is frequently discussed in system design interviews.

---

> **Next Topic:** `11-BASE.md`
