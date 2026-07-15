# Distributed Cache

> *"A Distributed Cache is a caching system where cached data is spread across multiple servers, providing scalability, high availability, and fault tolerance."*

---

# Table of Contents

* What is a Distributed Cache?
* Why Do We Need a Distributed Cache?
* How a Distributed Cache Works
* Components of a Distributed Cache
* Data Distribution
* Replication
* Advantages
* Disadvantages
* Popular Distributed Cache Systems
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is a Distributed Cache?

A **Distributed Cache** stores cached data across **multiple cache servers** instead of a single machine.

Instead of all requests going to one cache server, data is distributed among many cache nodes.

```text id="dc1"
Application

↓

Distributed Cache

↓

Node A

Node B

Node C
```

This improves scalability and eliminates the limitations of a single cache server.

---

# Why Do We Need a Distributed Cache?

Suppose one cache server stores:

```text id="dc2"
10 GB Cache
```

The application now requires:

```text id="dc3"
100 GB Cache
```

A single server cannot handle the increased memory requirement efficiently.

Using multiple cache servers:

```text id="dc4"
Node A

25 GB

+

Node B

25 GB

+

Node C

25 GB

+

Node D

25 GB

=

100 GB
```

The cache scales horizontally.

---

# How a Distributed Cache Works

Request flow:

```text id="dc5"
Client

↓

Application

↓

Distributed Cache

↓

Correct Cache Node

↓

Return Data
```

If the data is not found:

```text id="dc6"
Cache Miss

↓

Database

↓

Store in Cache

↓

Return Data
```

---

# Components of a Distributed Cache

A distributed cache typically consists of:

* Multiple Cache Nodes
* Client/Application
* Hashing Mechanism
* Replication (Optional)
* Monitoring

Together, these components provide high performance and fault tolerance.

---

# Data Distribution

Data must be distributed efficiently across cache nodes.

The most common approach is **Consistent Hashing**.

Example:

```text id="dc7"
User A

↓

Node 1

User B

↓

Node 2

User C

↓

Node 3
```

Consistent hashing minimizes data movement when nodes are added or removed.

---

# Replication

To improve availability, cached data can be copied to multiple nodes.

```text id="dc8"
Primary Node

↓

Replica Node
```

If the primary node fails, the replica can continue serving requests.

---

# Advantages

* Horizontal scalability.
* High throughput.
* Reduced database load.
* Better fault tolerance.
* High availability.
* Large cache capacity.

---

# Disadvantages

* More complex architecture.
* Cache synchronization challenges.
* Additional network communication.
* More difficult debugging.
* Higher operational overhead.

---

# Popular Distributed Cache Systems

* Redis Cluster
* Memcached Cluster
* Hazelcast
* Apache Ignite
* Aerospike
* Couchbase

These systems are widely used in modern distributed applications.

---

# Real-World Examples

## Netflix

Caches movie metadata across multiple Redis clusters.

---

## Amazon

Uses distributed caches to accelerate product lookups and user sessions.

---

## Facebook

Distributes cache across thousands of servers to reduce database traffic.

---

## Uber

Caches driver locations and frequently accessed trip information.

---

# When to Use a Distributed Cache

Use a distributed cache when:

* The cache no longer fits on a single server.
* High availability is required.
* Millions of requests are expected.
* Applications run across multiple servers.
* Horizontal scaling is needed.

---

# Quick Revision

```text id="dc9"
Distributed Cache

↓

Multiple Cache Nodes

↓

Consistent Hashing

↓

Correct Node

↓

Return Data

Features

✔ Scalable

✔ High Availability

✔ Fault Tolerant

Popular

Redis Cluster

Memcached

Hazelcast

Apache Ignite
```

---

# Key Takeaways

* **Distributed Cache** stores cached data across multiple servers to improve scalability and availability.
* Data is commonly distributed using **Consistent Hashing**, which minimizes data movement during scaling.
* **Replication** improves fault tolerance by maintaining backup copies of cached data.
* Distributed caches reduce database load, increase throughput, and support applications handling millions of requests.
* Technologies such as **Redis Cluster, Memcached Cluster, Hazelcast, and Apache Ignite** are widely used for distributed caching in production environments.

---

> **Next Topic:** `05-CDN.md`
