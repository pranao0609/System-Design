# Global Load Balancing

> *"Global Load Balancing distributes user traffic across multiple geographic regions or data centers to improve availability, reduce latency, and provide disaster recovery."*

---

# Table of Contents

* What is Global Load Balancing?
* Why Do We Need Global Load Balancing?
* How Global Load Balancing Works
* Routing Strategies
* Health Checks
* Disaster Recovery
* Global Load Balancing vs Local Load Balancing
* Real-World Examples
* Advantages
* Disadvantages
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Global Load Balancing?

**Global Load Balancing (GLB)** is the process of distributing incoming traffic across **multiple regions, data centers, or cloud locations** around the world.

Unlike a local load balancer that distributes traffic within a single data center, a Global Load Balancer decides **which region** should serve a user's request.

Example:

```text id="glb1"
Users

↓

Global Load Balancer

↓

India

USA

Europe
```

Each user is routed to the most appropriate region.

---

# Why Do We Need Global Load Balancing?

Imagine users from different parts of the world accessing the same application.

Without GLB:

```text id="glb2"
India User

↓

USA Server
```

Problems:

* High latency
* Slow response
* Long network distance

With GLB:

```text id="glb3"
India User

↓

India Data Center
```

The user experiences much lower latency.

---

# How Global Load Balancing Works

```text id="glb4"
Client

↓

DNS / Global Load Balancer

↓

Nearest Healthy Region

↓

Regional Load Balancer

↓

Application Servers
```

The Global Load Balancer first selects the best region.

A regional load balancer then distributes traffic among servers in that region.

---

# Routing Strategies

## 1. Geographic Routing

Users are routed to the nearest geographic region.

Example:

```text id="glb5"
India

↓

Mumbai

USA

↓

Virginia

Europe

↓

Frankfurt
```

---

## 2. Latency-Based Routing

Traffic is routed to the region with the lowest network latency.

The closest region is not always the fastest.

---

## 3. Weighted Routing

Traffic is distributed according to predefined weights.

Example:

```text id="glb6"
Region A

70%

Region B

30%
```

Useful during migrations or gradual rollouts.

---

## 4. Failover Routing

If one region becomes unavailable:

```text id="glb7"
Primary Region

↓

Failure

↓

Secondary Region
```

Users are automatically redirected.

---

# Health Checks

Global Load Balancers continuously monitor each region.

Checks include:

* Server health
* Network availability
* Response time
* Application status

Unhealthy regions are removed from routing automatically.

---

# Disaster Recovery

If an entire data center fails:

```text id="glb8"
Region A

↓

Power Failure

↓

Traffic Redirected

↓

Region B
```

This ensures business continuity.

---

# Global Load Balancing vs Local Load Balancing

| Global Load Balancing      | Local Load Balancing        |
| -------------------------- | --------------------------- |
| Multiple regions           | Single region               |
| Uses DNS or Global Routing | Uses local load balancer    |
| Reduces global latency     | Balances local traffic      |
| Supports disaster recovery | Improves server utilization |

---

# Real-World Examples

## Google

Routes users to the nearest available data center worldwide.

---

## Netflix

Directs viewers to the closest CDN edge server for faster video streaming.

---

## Amazon

Distributes customer traffic across multiple AWS Regions and Availability Zones.

---

## Cloudflare

Uses a global Anycast network to route requests to the nearest healthy edge location.

---

# Popular Global Load Balancing Services

* AWS Route 53
* Google Cloud Load Balancing
* Azure Traffic Manager
* Cloudflare Load Balancing
* F5 Global Traffic Manager (GTM)

---

# Advantages

* Lower latency.
* High availability.
* Disaster recovery.
* Better fault tolerance.
* Improved global user experience.
* Traffic distribution across regions.

---

# Disadvantages

* More complex architecture.
* Higher operational cost.
* DNS propagation delays in some scenarios.
* Cross-region data synchronization challenges.

---

# Best Practices

* Deploy applications across multiple regions.
* Continuously monitor health checks.
* Use automatic failover.
* Replicate data across regions.
* Minimize cross-region latency.
* Regularly test disaster recovery plans.

---

# Quick Revision

```text id="glb9"
Global Load Balancing

↓

Multiple Regions

↓

Nearest Healthy Region

Routing

✔ Geographic

✔ Latency-Based

✔ Weighted

✔ Failover

Benefits

✔ Low Latency

✔ High Availability

✔ Disaster Recovery

Popular

AWS Route 53

Cloudflare

Azure Traffic Manager
```

---

# Key Takeaways

* **Global Load Balancing** distributes traffic across multiple geographic regions to improve performance and resilience.
* It reduces latency by routing users to the **nearest or fastest healthy region**.
* Common routing strategies include **geographic, latency-based, weighted, and failover routing**.
* Continuous **health checks** and **automatic failover** help maintain high availability during regional outages.
* Global Load Balancing is a core component of large-scale cloud architectures used by companies like **Google, Netflix, Amazon, and Cloudflare**.

---

# 🎉 Load Balancing Complete

You have now completed **06 - Load Balancing**.

## Topics Covered

* ✅ Reverse Proxy
* ✅ Forward Proxy
* ✅ Layer 4 (L4) Load Balancing
* ✅ Layer 7 (L7) Load Balancing
* ✅ Consistent Hashing
* ✅ Sticky Sessions
* ✅ Global Load Balancing

These concepts explain how modern distributed systems efficiently distribute traffic, improve availability, reduce latency, and handle failures while serving millions of users.

---
rinciples behind how large-scale distributed systems coordinate data, maintain consistency, and operate reliably across multiple machines.
