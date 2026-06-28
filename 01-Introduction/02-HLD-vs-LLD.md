# High-Level Design (HLD) vs Low-Level Design (LLD)

> *"Software architecture is built in layers. High-Level Design (HLD) defines **what the system looks like**, while Low-Level Design (LLD) defines **how each component is implemented**."*

---

# Table of Contents

* What is High-Level Design (HLD)?
* What is Low-Level Design (LLD)?
* HLD vs LLD
* Why Both Are Important
* Real-World Example
* HLD Components
* LLD Components
* Design Process
* Interview Perspective
* Common Mistakes
* Quick Revision
* Key Takeaways

---

# Introduction

When building any software system, engineers design it at different levels of abstraction.

Imagine constructing a shopping mall:

* **High-Level Design** is the architectural blueprint showing floors, elevators, parking, and entrances.
* **Low-Level Design** is the engineering drawing specifying wall thickness, electrical wiring, plumbing, and structural details.

Software design follows the same approach.

---

# What is High-Level Design (HLD)?

High-Level Design defines the **overall architecture** of a system.

It answers questions such as:

* What services are needed?
* How will components communicate?
* Which database should be used?
* Where should caching be introduced?
* How will requests flow?
* How will the system scale?

HLD focuses on the **big picture**, not implementation details.

---

## Example

For an online shopping application:

```text
Users
   │
   ▼
Load Balancer
   │
   ▼
API Gateway
   │
 ┌─┴───────────────┐
 │                 │
User Service   Product Service
 │                 │
 └──────┬──────────┘
        ▼
     Database
```

At this stage, we are **not** discussing classes, methods, or algorithms.

---

# What is Low-Level Design (LLD)?

Low-Level Design defines **how individual components are implemented**.

It includes:

* Classes
* Interfaces
* Objects
* Design Patterns
* Database Models
* Algorithms
* Error Handling
* Method Signatures

LLD transforms architectural ideas into implementable code.

---

## Example

Inside the **Product Service**:

```text
ProductController
        │
        ▼
ProductService
        │
        ▼
ProductRepository
        │
        ▼
MySQL
```

Further breaking it down:

```java
Product
├── id
├── name
├── price
├── quantity
└── category

ProductService
├── createProduct()
├── updateProduct()
├── deleteProduct()
└── getProduct()
```

This level of detail belongs to LLD.

---

# HLD vs LLD

| Feature    | High-Level Design (HLD)      | Low-Level Design (LLD)    |
| ---------- | ---------------------------- | ------------------------- |
| Focus      | Overall architecture         | Internal implementation   |
| Level      | Abstract                     | Detailed                  |
| Audience   | Architects, Senior Engineers | Developers                |
| Components | Services, Databases, APIs    | Classes, Objects, Methods |
| Goal       | Design the system            | Implement the system      |
| Diagram    | Architecture Diagram         | Class Diagram             |
| Changes    | Less frequent                | More frequent             |

---

# Why Both Are Important

A successful software system requires both HLD and LLD.

### Without HLD

* Poor scalability
* Difficult integration
* Inefficient communication
* Hard to expand

### Without LLD

* Poor code quality
* Difficult maintenance
* Tight coupling
* High bug count

Think of HLD as the city map and LLD as the construction plan for each building.

---

# Real-World Example: Food Delivery App

Suppose we are designing a food delivery platform.

## High-Level Design

```text
Customer
     │
     ▼
API Gateway
     │
 ┌───┼───────────────┐
 │   │               │
User Restaurant Order
Service Service   Service
 │      │          │
 └──────┼──────────┘
        ▼
     Database
        │
        ▼
     Notification Service
```

This diagram shows the overall system architecture.

---

## Low-Level Design (Order Service)

```text
OrderController
        │
        ▼
OrderService
        │
        ▼
OrderRepository
```

### Classes

```text
Order
├── orderId
├── userId
├── restaurantId
├── items
├── totalAmount
└── status

OrderService
├── placeOrder()
├── cancelOrder()
├── updateStatus()
└── getOrder()
```

This is the implementation-level design.

---

# HLD Components

A typical High-Level Design includes:

* Client Applications
* Load Balancer
* API Gateway
* Microservices
* Databases
* Cache
* Message Queue
* Object Storage
* CDN
* Monitoring
* Authentication Service

These components describe **how the system is organized**.

---

# LLD Components

A typical Low-Level Design includes:

* Classes
* Interfaces
* Objects
* Design Patterns
* Packages
* Modules
* Data Models
* Algorithms
* Exception Handling
* Database Schema
* API Contracts

These components describe **how each service works internally**.

---

# Design Process

Software projects generally follow this sequence:

```text
Requirements
      │
      ▼
High-Level Design (Architecture)
      │
      ▼
Low-Level Design (Implementation)
      │
      ▼
Coding
      │
      ▼
Testing
      │
      ▼
Deployment
      │
      ▼
Monitoring
```

Each phase builds upon the previous one.

---

# Interview Perspective

## HLD Interviews

Typical questions:

* Design WhatsApp
* Design Instagram
* Design Netflix
* Design Uber
* Design URL Shortener

Interviewers evaluate:

* Architecture
* Scalability
* Trade-offs
* Bottleneck identification
* Communication

---

## LLD Interviews

Typical questions:

* Design a Parking Lot
* Design a Library Management System
* Design an ATM
* Design a Vending Machine
* Design a Hotel Booking System

Interviewers evaluate:

* Object-Oriented Design
* SOLID Principles
* Design Patterns
* Clean Code
* Extensibility

---

# Common Mistakes

### During HLD

* Choosing technologies before understanding requirements.
* Ignoring scalability.
* Missing failure scenarios.
* Forgetting caching or load balancing.
* Designing everything as a single service.

---

### During LLD

* Violating SOLID principles.
* Tight coupling between classes.
* Large "God" classes with too many responsibilities.
* Missing interfaces and abstractions.
* Ignoring testability.

---

# When to Focus on HLD vs LLD

| Scenario                         | Focus |
| -------------------------------- | ----- |
| Designing a new platform         | HLD   |
| Scaling an existing system       | HLD   |
| Building a service               | LLD   |
| Writing production code          | LLD   |
| Software Architecture Interview  | HLD   |
| Object-Oriented Design Interview | LLD   |

---

# Quick Revision

```text
HLD
│
├── Big Picture
├── Architecture
├── Services
├── Databases
├── APIs
├── Scaling
├── Load Balancers
└── Communication

LLD
│
├── Classes
├── Objects
├── Interfaces
├── Methods
├── Algorithms
├── Design Patterns
├── Database Models
└── Implementation
```

---

# Key Takeaways

* **High-Level Design (HLD)** focuses on the overall architecture, components, and communication between services.
* **Low-Level Design (LLD)** focuses on the internal implementation of each component using object-oriented principles and design patterns.
* HLD answers **"What should the system look like?"**
* LLD answers **"How will each part be built?"**
* Strong software systems require both HLD and LLD working together.
* In interviews, HLD evaluates architectural thinking, while LLD evaluates implementation and code design skills.

---

> **Next Topic:** `03-System-Design-Process.md`
