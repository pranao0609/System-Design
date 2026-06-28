# What is System Design?

> *"System Design is the process of designing the architecture, components, interfaces, and data flow of a software system to satisfy functional and non-functional requirements while ensuring scalability, reliability, maintainability, and performance."*

---

# Table of Contents

* What is System Design?
* Why Do We Need System Design?
* Goals of System Design
* Components of a Software System
* Characteristics of a Good System
* High-Level View of a System
* Real-World Example
* Types of System Design
* Common Design Constraints
* System Design Workflow
* Common Mistakes
* Interview Perspective
* Quick Revision
* Key Takeaways

---

# What is System Design?

System Design is the process of planning **how different software and hardware components work together** to build an application that can efficiently serve users.

Instead of writing code, system design focuses on answering questions such as:

* How will users interact with the application?
* How will requests reach the server?
* Where will data be stored?
* How will the system scale to millions of users?
* How can failures be handled gracefully?
* How can performance and reliability be maintained?

In simple terms,

> **System Design is the blueprint of a software application before it is built.**

Just as architects create blueprints before constructing a building, software engineers design systems before implementing them.

---

# Why Do We Need System Design?

Small applications may work with a single server and a single database.

However, as the number of users grows, new challenges emerge:

* Millions of concurrent users
* Massive amounts of data
* Low response time requirements
* Hardware failures
* Network failures
* Security concerns
* High availability expectations

Without proper design, systems become:

* Slow
* Difficult to maintain
* Expensive
* Unreliable
* Hard to scale

System design helps solve these problems before they occur.

---

# Goals of System Design

A good system should achieve the following objectives:

## 1. Scalability

The system should support increasing numbers of users without significant performance degradation.

Example:

```text
10 Users
↓

1,000 Users
↓

100,000 Users
↓

10 Million Users
```

---

## 2. Reliability

The system should continue functioning correctly even when components fail.

Example:

If one server crashes, another server should continue serving requests.

---

## 3. Availability

The application should remain accessible whenever users need it.

Example:

Google Search is expected to be available almost all the time.

---

## 4. Performance

The system should process requests quickly.

Example:

A search query should return results within milliseconds.

---

## 5. Maintainability

The software should be easy to modify, debug, and extend.

---

## 6. Security

Protect user data and prevent unauthorized access.

---

## 7. Cost Efficiency

Design the system to deliver high performance without unnecessary infrastructure costs.

---

# Components of a Software System

A modern software system consists of multiple interconnected components.

```text
            User
              │
              ▼
        Load Balancer
              │
      ┌───────┴────────┐
      │                │
 Application Server  Application Server
      │                │
      └───────┬────────┘
              │
          Cache (Redis)
              │
              ▼
          Database
              │
              ▼
       Object Storage
```

Each component has a specific responsibility.

| Component          | Responsibility                  |
| ------------------ | ------------------------------- |
| Client             | Sends requests                  |
| Load Balancer      | Distributes traffic             |
| Application Server | Executes business logic         |
| Cache              | Stores frequently accessed data |
| Database           | Persists data                   |
| Object Storage     | Stores files, images, videos    |

---

# Characteristics of a Good System

A well-designed system should be:

* Scalable
* Reliable
* Highly Available
* Fault Tolerant
* Secure
* Maintainable
* Observable
* Cost Efficient
* Performant

These characteristics often involve trade-offs. Improving one aspect (such as consistency) may impact another (such as availability).

---

# High-Level View of a System

Every web application follows a similar request-response flow.

```text
User
 │
 ▼
Internet
 │
 ▼
DNS
 │
 ▼
Load Balancer
 │
 ▼
Application Server
 │
 ├────────► Cache
 │
 ▼
Database
 │
 ▼
Response
 │
 ▼
User
```

As systems grow, each of these components can be scaled independently.

---

# Real-World Example: Instagram

When a user opens Instagram:

```text
User opens Instagram
          │
          ▼
DNS resolves the domain
          │
          ▼
Load Balancer selects a server
          │
          ▼
Application Server processes request
          │
     ┌────┴────┐
     │         │
 Cache Hit   Cache Miss
     │         │
     ▼         ▼
 Response   Database Query
      \       /
       ▼     ▼
      Response to User
```

Notice how multiple services work together to provide a seamless experience.

---

# Types of System Design

## 1. High-Level Design (HLD)

Focuses on the overall architecture.

Examples:

* Microservices
* Databases
* Load Balancers
* APIs
* Caches
* Message Queues

---

## 2. Low-Level Design (LLD)

Focuses on detailed implementation.

Examples:

* Classes
* Interfaces
* Design Patterns
* Object Relationships
* Algorithms

---

## 3. Database Design

Focuses on:

* Tables
* Relationships
* Indexes
* Constraints
* Query Optimization

---

## 4. Distributed System Design

Focuses on systems running across multiple machines.

Examples:

* Replication
* Sharding
* Consensus
* Fault Tolerance

---

# Common Design Constraints

Every system operates within constraints such as:

* Budget
* Team size
* Development time
* User traffic
* Latency requirements
* Storage capacity
* Compliance and regulations
* Hardware limitations

Good system design balances these constraints rather than optimizing only one aspect.

---

# Typical System Design Workflow

```text
Understand Requirements
          │
          ▼
Estimate Scale
          │
          ▼
Identify Components
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
Add Monitoring
          │
          ▼
Review Bottlenecks
```

This structured process is commonly used in system design interviews and real-world architecture discussions.

---

# Common Mistakes

* Starting with technologies instead of requirements.
* Ignoring scalability and future growth.
* Overengineering simple systems.
* Forgetting non-functional requirements.
* Assuming unlimited resources.
* Neglecting monitoring and observability.
* Failing to identify single points of failure.

---

# Interview Perspective

In system design interviews, interviewers are generally evaluating:

* Requirement gathering
* Architectural thinking
* Scalability considerations
* Trade-off analysis
* Communication skills
* Knowledge of distributed systems
* Ability to justify design decisions

There is rarely a single "correct" design. A strong candidate explains assumptions, evaluates alternatives, and discusses trade-offs clearly.

---

# Quick Revision

```text
System Design
│
├── Purpose
│     ├── Build scalable systems
│     ├── Ensure reliability
│     ├── Improve maintainability
│     └── Optimize performance
│
├── Components
│     ├── Client
│     ├── Load Balancer
│     ├── Server
│     ├── Cache
│     ├── Database
│     └── Storage
│
├── Goals
│     ├── Scalability
│     ├── Availability
│     ├── Reliability
│     ├── Security
│     ├── Performance
│     └── Cost Efficiency
│
└── Types
      ├── HLD
      ├── LLD
      ├── Database Design
      └── Distributed Systems
```

---

# Key Takeaways

* System Design is the process of planning how software components interact to build scalable and reliable applications.
* It focuses on architecture rather than implementation details.
* Good design balances scalability, availability, reliability, performance, security, and cost.
* Every large-scale application follows a structured architecture involving clients, networking, application servers, caching, databases, and storage.
* Successful system design is driven by requirements, thoughtful trade-offs, and continuous improvement.

---

> **Next Topic:** `02-HLD-vs-LLD.md`
