# Horizontal Scaling

> *"Horizontal Scaling is the process of increasing a system's capacity by adding more servers instead of upgrading a single server."*

---

# Table of Contents

* What is Scaling?
* What is Horizontal Scaling?
* Why Do We Need Horizontal Scaling?
* How Horizontal Scaling Works
* Horizontal vs Vertical Scaling
* Load Distribution
* Advantages
* Disadvantages
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Scaling?

**Scaling** is the process of increasing a system's ability to handle:

* More users
* More requests
* More data
* More traffic

Example:

```text id="hs1"
1,000 Users

↓

100,000 Users

↓

10 Million Users
```

As demand grows, the system must scale to maintain performance.

---

# What is Horizontal Scaling?

**Horizontal Scaling (Scale-Out)** means adding **more servers** to distribute the workload.

Instead of making one server more powerful, multiple servers work together.

Example:

```text id="hs2"
Before

Client

↓

Server
```

After scaling:

```text id="hs3"
           Load Balancer
                │
      ┌─────────┼─────────┐
      ▼         ▼         ▼
   Server 1  Server 2  Server 3
```

Each server handles a portion of incoming requests.

---

# Why Do We Need Horizontal Scaling?

Suppose one server can process:

```text id="hs4"
10,000 Requests/Second
```

Traffic increases to:

```text id="hs5"
50,000 Requests/Second
```

One server becomes overloaded.

Instead of replacing it with a larger machine, we can add more servers.

Example:

```text id="hs6"
5 Servers

×

10,000 Requests/Second

=

50,000 Requests/Second
```

---

# How Horizontal Scaling Works

A **Load Balancer** receives incoming requests and distributes them across multiple servers.

```text id="hs7"
Users

↓

Load Balancer

↓

Server 1

Server 2

Server 3

↓

Database
```

This prevents any single server from becoming a bottleneck.

---

# Horizontal vs Vertical Scaling

| Horizontal Scaling           | Vertical Scaling             |
| ---------------------------- | ---------------------------- |
| Add more servers             | Upgrade existing server      |
| Better fault tolerance       | Single point of failure      |
| Easier to scale indefinitely | Limited by hardware          |
| Requires load balancing      | Simpler to implement         |
| Common in cloud environments | Common in small applications |

---

# Load Distribution

The load balancer distributes requests using algorithms such as:

* Round Robin
* Least Connections
* IP Hash
* Weighted Round Robin

Example:

```text id="hs8"
Request 1 → Server 1

Request 2 → Server 2

Request 3 → Server 3

Request 4 → Server 1
```

---

# Advantages

* High scalability.
* Improved availability.
* Better fault tolerance.
* Easier maintenance.
* Supports cloud-native architectures.

---

# Disadvantages

* More infrastructure.
* Higher operational complexity.
* Requires load balancing.
* Data synchronization challenges.
* Session management becomes more complex.

---

# Real-World Examples

## Netflix

Thousands of servers handle streaming requests across different regions.

---

## Amazon

Traffic during major sales events is distributed across numerous servers.

---

## Google Search

Search requests are processed by thousands of distributed servers worldwide.

---

## Kubernetes

Applications are scaled horizontally by increasing the number of running pods.

---

# When to Use Horizontal Scaling

Choose horizontal scaling when:

* Traffic grows rapidly.
* High availability is required.
* Downtime must be minimized.
* Cloud infrastructure is available.
* Distributed systems are being built.

---


# Quick Revision

```text id="hs9"
Horizontal Scaling

↓

Add More Servers

↓

Load Balancer

↓

Distribute Requests

Benefits

✔ Scalability

✔ High Availability

✔ Fault Tolerance

Challenges

✖ More Complexity

✖ Data Synchronization

✖ Load Balancing
```

---

# Key Takeaways

* **Horizontal Scaling** increases system capacity by adding more servers rather than upgrading existing hardware.
* A **Load Balancer** distributes incoming traffic across multiple servers to improve performance and availability.
* Horizontal scaling provides excellent scalability and fault tolerance, making it the preferred approach for modern cloud-native applications.
* It introduces additional challenges such as load balancing, distributed data management, and session handling.
* Most large-scale platforms, including **Google, Netflix, Amazon, and Kubernetes**, rely heavily on horizontal scaling to support millions of users.

---

> **Next Topic:** `02-Vertical-Scaling.md`
