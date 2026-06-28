# System Design Process

> *"A good system design starts with understanding the problem, not choosing the technology."*

---

# Table of Contents

* What is the System Design Process?
* Why Follow a Design Process?
* The 10-Step System Design Framework
* Step 1: Understand the Requirements
* Step 2: Estimate Scale
* Step 3: Define APIs
* Step 4: High-Level Design
* Step 5: Database Design
* Step 6: Scale the System
* Step 7: Improve Reliability
* Step 8: Security Considerations
* Step 9: Monitoring & Observability
* Step 10: Identify Bottlenecks & Trade-offs
* End-to-End Example
* Common Mistakes
* Interview Perspective
* Quick Revision
* Key Takeaways

---

# What is the System Design Process?

The **System Design Process** is a structured approach used to design scalable, reliable, and maintainable software systems.

Instead of immediately selecting technologies or writing code, engineers first understand the problem, estimate the expected scale, identify system components, and evaluate architectural trade-offs.

This process ensures that the final system satisfies both **functional requirements** (what the system should do) and **non-functional requirements** (how well it should do it).

---

# Why Follow a Design Process?

A structured process helps you:

* Understand the problem completely.
* Avoid making incorrect assumptions.
* Design systems that scale.
* Identify bottlenecks early.
* Justify architectural decisions.
* Communicate ideas clearly during interviews and design reviews.

---

# The 10-Step System Design Framework

```text
                 Start
                   │
                   ▼
      1. Understand Requirements
                   │
                   ▼
          2. Estimate Scale
                   │
                   ▼
            3. Define APIs
                   │
                   ▼
       4. High-Level Architecture
                   │
                   ▼
         5. Database Design
                   │
                   ▼
        6. Scale the System
                   │
                   ▼
      7. Improve Reliability
                   │
                   ▼
     8. Secure the System
                   │
                   ▼
   9. Monitoring & Logging
                   │
                   ▼
10. Bottlenecks & Trade-offs
```

This framework is commonly used in real-world architecture discussions and system design interviews.

---

# Step 1: Understand the Requirements

Before designing anything, gather complete requirements.

## Functional Requirements

These describe **what the system should do**.

Example:

* User registration
* Login
* Upload images
* Search products
* Send messages

## Non-Functional Requirements

These describe **how the system should behave**.

Example:

* High availability
* Low latency
* Scalability
* Security
* Reliability

### Questions to Ask

* Who are the users?
* What are the core features?
* Is real-time communication required?
* What is the expected traffic?
* Are there any regulatory constraints?

> Never start designing until the requirements are clear.

---

# Step 2: Estimate Scale

Estimate the expected workload to make informed architectural decisions.

Common estimations include:

* Daily Active Users (DAU)
* Monthly Active Users (MAU)
* Requests per second (RPS)
* Queries per second (QPS)
* Storage requirements
* Bandwidth
* CPU
* Memory

### Example

Suppose:

* 10 million users
* 1 million daily active users
* 5 requests per user per day

Then:

```text
Total Requests = 5,000,000/day

Requests Per Second (RPS)
≈ 5,000,000 / 86,400
≈ 58 RPS
```

Capacity estimation helps determine the number of servers, database size, cache requirements, and network capacity.

---

# Step 3: Define APIs

Clearly define how clients will interact with the system.

Example:

```http
POST /users
GET /users/{id}
PUT /users/{id}
DELETE /users/{id}
```

For each API, specify:

* Request format
* Response format
* Status codes
* Authentication
* Validation
* Error handling

Good API design simplifies integration and future maintenance.

---

# Step 4: High-Level Design

Design the overall architecture by identifying the major components.

Example architecture:

```text
              Client
                 │
                 ▼
          Load Balancer
                 │
                 ▼
           API Gateway
                 │
       ┌─────────┴─────────┐
       │                   │
 User Service       Product Service
       │                   │
       └─────────┬─────────┘
                 ▼
               Database
```

Typical components include:

* Load Balancer
* API Gateway
* Application Servers
* Cache
* Database
* Message Queue
* Object Storage

---

# Step 5: Database Design

Choose the right database based on the workload.

### SQL

Best for:

* Transactions
* Strong consistency
* Structured data

Examples:

* PostgreSQL
* MySQL

### NoSQL

Best for:

* High scalability
* Flexible schemas
* Large datasets

Examples:

* MongoDB
* Cassandra
* Redis

Also consider:

* Indexes
* Replication
* Sharding
* Backup strategies

---

# Step 6: Scale the System

As traffic grows, a single server becomes insufficient.

Common scaling techniques:

### Horizontal Scaling

```text
Server
   │
▼ ▼ ▼ ▼
Multiple Servers
```

### Vertical Scaling

```text
Small Server
      │
      ▼
Bigger CPU
More RAM
More Storage
```

Additional techniques:

* Load Balancing
* Caching
* CDN
* Database Replication
* Sharding

---

# Step 7: Improve Reliability

Failures are inevitable.

Design systems to recover automatically.

Common techniques:

* Replication
* Failover
* Circuit Breaker
* Retry Mechanisms
* Health Checks
* Heartbeats
* Disaster Recovery

Goal:

> Eliminate single points of failure.

---

# Step 8: Security Considerations

Every production system must address security.

Typical measures include:

* HTTPS
* Authentication
* Authorization
* JWT
* OAuth 2.0
* Encryption
* Secrets Management
* Input Validation
* Rate Limiting

Security should be considered throughout the design process, not added as an afterthought.

---

# Step 9: Monitoring & Observability

After deployment, monitor system health continuously.

Key components:

* Logging
* Metrics
* Distributed Tracing
* Dashboards
* Alerts

Popular tools:

* Prometheus
* Grafana
* OpenTelemetry
* ELK Stack

Monitoring helps detect and resolve issues before they affect users.

---

# Step 10: Identify Bottlenecks & Trade-offs

Finally, review the design to identify limitations.

Ask questions such as:

* Can the database become a bottleneck?
* Is there a single point of failure?
* What happens if a server crashes?
* How will the cache behave during failures?
* Is the system over-engineered?

Discuss trade-offs:

| Choice      | Benefit            | Drawback                                       |
| ----------- | ------------------ | ---------------------------------------------- |
| SQL         | Strong consistency | Harder to scale horizontally                   |
| NoSQL       | High scalability   | Weaker consistency                             |
| Cache       | Faster reads       | Cache invalidation complexity                  |
| Replication | High availability  | Increased storage and synchronization overhead |

Interviewers value thoughtful trade-off discussions more than "perfect" architectures.

---

# End-to-End Example

Imagine designing a URL Shortener.

```text
Requirements
      │
      ▼
Estimate Users
      │
      ▼
Design APIs
      │
      ▼
Choose Database
      │
      ▼
Add Cache
      │
      ▼
Add Load Balancer
      │
      ▼
Improve Reliability
      │
      ▼
Monitoring
      │
      ▼
Review Bottlenecks
```

This same process can be applied to systems like WhatsApp, YouTube, Netflix, or Uber.

---

# Common Mistakes

* Jumping directly to technology choices.
* Ignoring non-functional requirements.
* Skipping capacity estimation.
* Not discussing failure scenarios.
* Designing without considering future growth.
* Forgetting monitoring and logging.
* Ignoring security.
* Failing to explain trade-offs.

---

# Interview Perspective

A common approach in system design interviews is:

1. Clarify requirements.
2. Estimate scale.
3. Design a high-level architecture.
4. Dive deeper into databases, caching, and communication.
5. Address scalability and reliability.
6. Discuss trade-offs and potential bottlenecks.

Remember:

> Interviewers assess your reasoning process more than the final architecture.

---

# Quick Revision

```text
System Design Process

1. Understand Requirements
          │
2. Estimate Scale
          │
3. Define APIs
          │
4. High-Level Design
          │
5. Database Design
          │
6. Scale the System
          │
7. Improve Reliability
          │
8. Secure the System
          │
9. Monitor the System
          │
10. Review Bottlenecks & Trade-offs
```

---

# Key Takeaways

* A structured design process leads to scalable and maintainable systems.
* Always begin with requirements before selecting technologies.
* Capacity estimation guides architectural decisions.
* Design APIs and high-level architecture before implementation.
* Plan for scalability, reliability, security, and observability from the beginning.
* Every design involves trade-offs; explaining them is a crucial part of system design.

---

> **Next Topic:** `04-Capacity-Estimation.md`
