# Vertical Scaling

> *"Vertical Scaling is the process of increasing a system's capacity by upgrading the hardware resources of a single server, such as CPU, RAM, storage, or network bandwidth."*

---

# Table of Contents

* What is Vertical Scaling?
* Why Do We Need Vertical Scaling?
* How Vertical Scaling Works
* Vertical vs Horizontal Scaling
* Advantages
* Disadvantages
* Real-World Examples
* When to Use Vertical Scaling
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Vertical Scaling?

**Vertical Scaling (Scale-Up)** means improving the performance of a **single server** by increasing its hardware resources.

Resources that can be upgraded include:

* CPU
* RAM
* SSD/HDD Storage
* Network Bandwidth

Example:

```text id="vs1"
Before

4 CPU Cores

8 GB RAM

↓

After

16 CPU Cores

64 GB RAM
```

Unlike horizontal scaling, no additional servers are added.

---

# Why Do We Need Vertical Scaling?

Suppose an application initially serves:

```text id="vs2"
2,000 Requests/Second
```

As traffic increases:

```text id="vs3"
8,000 Requests/Second
```

Instead of adding more servers, the existing server is upgraded with better hardware.

This allows it to process more requests.

---

# How Vertical Scaling Works

Initially:

```text id="vs4"
Client

↓

Server

4 CPU

8 GB RAM
```

After scaling:

```text id="vs5"
Client

↓

Server

16 CPU

64 GB RAM
```

The application continues running on the same server with increased capacity.

---

# Vertical vs Horizontal Scaling

| Vertical Scaling          | Horizontal Scaling            |
| ------------------------- | ----------------------------- |
| Upgrade one server        | Add more servers              |
| Simple to implement       | More complex                  |
| No load balancer required | Requires load balancer        |
| Hardware limit exists     | Can scale almost indefinitely |
| Single point of failure   | Better fault tolerance        |

---

# Advantages

* Easy to implement.
* No application redesign required.
* Simpler deployment.
* Lower operational complexity.
* Suitable for monolithic applications.

---

# Disadvantages

* Hardware has physical limits.
* Expensive high-end servers.
* Downtime may be required during upgrades.
* Single point of failure.
* Limited scalability.

---

# Vertical Scaling Limits

Every server has a maximum capacity.

Example:

```text id="vs6"
CPU

64 Cores

RAM

1 TB

Storage

Maximum Hardware Supported
```

Once the server reaches its hardware limit, further scaling requires **horizontal scaling**.

---

# Real-World Examples

## Small Business Website

A single web server upgraded from:

* 4 GB RAM
* 2 CPU cores

to

* 16 GB RAM
* 8 CPU cores

to handle more visitors.

---

## Database Server

Many relational databases (e.g., PostgreSQL, MySQL) are initially scaled vertically by increasing CPU and memory.

---

## Development Environment

Developers often increase RAM or CPU in local virtual machines to improve performance.

---

# When to Use Vertical Scaling

Choose vertical scaling when:

* The application is relatively small.
* Traffic is moderate.
* Simplicity is preferred.
* A monolithic architecture is used.
* Budget allows hardware upgrades.

For large-scale distributed systems, horizontal scaling is generally preferred.

---

# Vertical Scaling in Cloud Platforms

Cloud providers allow vertical scaling by changing the instance type.

Example:

```text id="vs7"
Small VM

↓

Medium VM

↓

Large VM

↓

Extra Large VM
```

This is often called **resizing** an instance.

---

# Quick Revision

```text id="vs8"
Vertical Scaling

↓

Upgrade Server

↓

More CPU

↓

More RAM

↓

More Storage

Benefits

✔ Simple

✔ Easy

✔ No Load Balancer

Limitations

✖ Hardware Limit

✖ Single Point of Failure

✖ Downtime
```

---

# Key Takeaways

* **Vertical Scaling** increases the capacity of a system by upgrading the hardware of a single server.
* It is simple to implement and works well for small to medium-sized applications.
* Vertical scaling is constrained by hardware limits and introduces a single point of failure.
* It is commonly used for standalone applications, monolithic systems, and database servers during early stages of growth.
* As applications continue to grow, organizations often transition from vertical scaling to **horizontal scaling** for better scalability and fault tolerance.

---

> **Next Topic:** `03-Capacity-Planning.md`
