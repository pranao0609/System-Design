# Consistent Hashing

> *"Consistent Hashing is a hashing technique used in distributed systems to distribute data across multiple servers while minimizing data movement when servers are added or removed."*

---

# Table of Contents

* What is Consistent Hashing?
* Why Do We Need Consistent Hashing?
* Traditional Hashing
* Problems with Traditional Hashing
* How Consistent Hashing Works
* Virtual Nodes
* Advantages
* Disadvantages
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Consistent Hashing?

**Consistent Hashing** is a technique for distributing data or requests across multiple servers.

Unlike traditional hashing, it minimizes the amount of data that needs to be redistributed when servers are added or removed.

It is commonly used in:

* Distributed Databases
* Caching Systems
* Load Balancers
* Distributed Storage Systems

---

# Why Do We Need Consistent Hashing?

Suppose we have 4 servers.

Traditional hashing:

```text id="ch1"
Hash(Key) % 4
```

Example:

```text id="ch2"
User123

↓

Hash

↓

Server 2
```

Now add another server.

```text id="ch3"
Hash(Key) % 5
```

Almost every key is assigned to a different server.

This results in massive data movement.

---

# Problems with Traditional Hashing

Example:

Initially:

```text id="ch4"
Server 1

Server 2

Server 3

Server 4
```

After adding Server 5:

```text id="ch5"
Almost Every Key

↓

Moves

↓

New Server Mapping
```

This causes:

* Cache misses
* Heavy network traffic
* Long rebalancing times

---

# How Consistent Hashing Works

Instead of hashing servers into a list, Consistent Hashing maps both **servers** and **data keys** onto a circular hash ring.

```text id="ch6"
          Server A
             ●
      /             \
 Key 1               Server B
   ●                   ●
      \             /
         Server C
            ●
```

Each key is stored on the **first server encountered while moving clockwise** around the ring.

---

# Adding a New Server

Suppose a new server is added.

```text id="ch7"
Before

A ---- B ---- C

↓

After

A ---- D ---- B ---- C
```

Only the keys between **A** and **D** move to the new server.

All other keys remain unchanged.

---

# Removing a Server

If a server fails:

```text id="ch8"
A ---- B ---- C

↓

B Fails

↓

A ---- C
```

Only the keys stored on **B** are reassigned.

The remaining keys are unaffected.

---

# Virtual Nodes (VNodes)

In practice, each physical server is represented by multiple **Virtual Nodes** on the hash ring.

Example:

```text id="ch9"
Server A

↓

A1

A2

A3

Server B

↓

B1

B2

B3
```

Benefits:

* Better load distribution.
* Reduced hotspots.
* Easier scaling.
* Improved fault tolerance.

Most modern distributed systems use virtual nodes.

---

# Advantages

* Minimal data movement.
* Better scalability.
* Balanced load distribution.
* High availability.
* Efficient server addition and removal.

---

# Disadvantages

* More complex implementation.
* Uneven distribution without virtual nodes.
* Additional memory for maintaining the hash ring.

---

# Real-World Examples

## Redis Cluster

Uses consistent hashing to distribute keys across nodes.

---

## Apache Cassandra

Distributes data using a hash ring with virtual nodes.

---

## Amazon DynamoDB

Uses partitioning techniques based on consistent hashing concepts.

---

## Memcached

Clients often use consistent hashing so cached data remains stable when cache servers are added or removed.

---

# Where is Consistent Hashing Used?

* Distributed Caches
* Distributed Databases
* Content Delivery Networks (CDNs)
* Object Storage Systems
* Load Balancers
* Peer-to-Peer Networks

---

# Quick Revision

```text id="ch10"
Consistent Hashing

↓

Hash Ring

↓

Servers + Keys

↓

Clockwise Mapping

↓

Minimal Data Movement

Features

✔ Scalable

✔ Balanced

✔ Fault Tolerant

Uses

Redis

Cassandra

Memcached
```

---

# Key Takeaways

* **Consistent Hashing** distributes data across multiple servers while minimizing data movement during scaling events.
* Unlike traditional hashing, adding or removing a server affects only a small subset of keys.
* **Virtual Nodes (VNodes)** improve load balancing and reduce uneven data distribution.
* Consistent hashing is widely used in **distributed caches, NoSQL databases, CDNs, and large-scale storage systems**.
* It is a fundamental concept in distributed system design and frequently appears in system design interviews.

---

> **Next Topic:** `06-Sticky-Sessions.md`
