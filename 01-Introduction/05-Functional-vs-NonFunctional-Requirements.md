# Functional vs Non-Functional Requirements

> *"Before designing a system, you must understand **what the system should do** and **how well it should do it**. Functional requirements define the features, while non-functional requirements define the quality attributes."*

---

# Table of Contents

* What are Requirements?
* Types of Requirements
* Functional Requirements
* Non-Functional Requirements
* Functional vs Non-Functional Requirements
* Gathering Requirements
* Real-World Example
* Prioritizing Requirements
* Trade-offs
* Common Mistakes
* Interview Perspective
* Quick Revision
* Key Takeaways

---

# What are Requirements?

Requirements describe the expectations and objectives of a software system.

They answer two fundamental questions:

1. **What should the system do?**
2. **How should the system perform?**

Requirements are the starting point of every software project. They guide architectural decisions, technology choices, and implementation.

---

# Types of Requirements

Software requirements are broadly classified into two categories:

```text
                     Requirements
                          │
          ┌───────────────┴───────────────┐
          │                               │
          ▼                               ▼
 Functional Requirements      Non-Functional Requirements
   (Features)                  (Quality Attributes)
```

Both are equally important for building successful software.

---

# Functional Requirements

Functional requirements define the **features and capabilities** of a system.

They specify **what the system should do**.

These requirements are usually derived from business needs or user stories.

## Examples

For an E-Commerce Website:

* User Registration
* Login & Logout
* Search Products
* Add to Cart
* Place Order
* Make Payment
* Track Order
* Cancel Order
* View Order History

These describe the actual functionality expected by users.

---

## Characteristics

Functional requirements are:

* Feature-oriented
* User-facing
* Testable
* Business-driven
* Usually documented as user stories or use cases

---

## Example User Story

```text
As a customer,

I should be able to add products to my cart,

so that I can purchase them later.
```

This is a functional requirement.

---

# Non-Functional Requirements

Non-functional requirements define **how well the system performs its functions**.

They describe the quality attributes of the system.

## Examples

A shopping application should:

* Respond within 200 milliseconds.
* Support 10 million users.
* Be available 99.99% of the time.
* Protect user data.
* Recover from failures.
* Handle traffic spikes.
* Be easy to maintain.

These do not introduce new features but define performance expectations.

---

## Common Non-Functional Requirements

### Scalability

The system should handle increasing numbers of users without significant performance degradation.

---

### Availability

The application should remain operational and accessible whenever users need it.

Example:

```text
Availability

99.99%

Downtime

≈ 52 minutes/year
```

---

### Reliability

The system should consistently perform its intended functions without failures.

---

### Performance

The application should process requests quickly.

Example:

```text
Average Response Time

< 200 ms
```

---

### Fault Tolerance

The system should continue operating even if some components fail.

---

### Security

Protect data using:

* Authentication
* Authorization
* Encryption
* Secure communication

---

### Maintainability

The codebase should be easy to modify, debug, and extend.

---

### Observability

The system should provide sufficient logs, metrics, and traces for monitoring and debugging.

---

### Cost Efficiency

The system should meet performance goals without unnecessary infrastructure costs.

---

# Functional vs Non-Functional Requirements

| Functional Requirements          | Non-Functional Requirements                   |
| -------------------------------- | --------------------------------------------- |
| Describe what the system does    | Describe how the system performs              |
| Feature-focused                  | Quality-focused                               |
| Based on business needs          | Based on technical constraints                |
| Visible to users                 | Often invisible to users                      |
| Examples: Login, Search, Payment | Examples: Scalability, Security, Availability |

---

# Gathering Requirements

A structured approach to requirement gathering:

```text
Stakeholders
      │
      ▼
Business Goals
      │
      ▼
Functional Requirements
      │
      ▼
Non-Functional Requirements
      │
      ▼
Constraints
      │
      ▼
System Design
```

Questions to ask:

### Functional

* What are the core features?
* Who are the users?
* What workflows should the system support?
* Which APIs are required?

### Non-Functional

* Expected Daily Active Users (DAU)?
* Required response time?
* Availability target?
* Data retention policy?
* Security requirements?
* Compliance requirements?
* Expected future growth?

---

# Real-World Example: WhatsApp

## Functional Requirements

* User Registration
* Login
* One-to-One Chat
* Group Chat
* Send Images
* Send Videos
* Voice Notes
* Read Receipts
* Online Status
* Push Notifications

---

## Non-Functional Requirements

* Message Delivery < 1 second
* End-to-End Encryption
* High Availability
* Support Millions of Concurrent Users
* Reliable Message Delivery
* Fault Tolerance
* Horizontal Scalability
* Low Network Usage

Notice that these describe the expected quality of the system rather than its features.

---

# Prioritizing Requirements

Not all requirements have equal importance.

A common approach:

```text
Must Have
│
├── Login
├── Authentication
├── Database
└── APIs

Should Have
│
├── Notifications
├── Search
└── Analytics

Could Have
│
├── Dark Mode
├── Themes
└── Recommendations
```

Prioritization helps deliver value incrementally.

---

# Trade-offs

System design often involves balancing competing requirements.

Examples:

| Goal                | Possible Trade-off                   |
| ------------------- | ------------------------------------ |
| Higher Availability | May reduce consistency (CAP Theorem) |
| Strong Security     | Slightly higher latency              |
| Better Performance  | Increased infrastructure cost        |
| Low Cost            | Reduced redundancy                   |
| High Scalability    | More architectural complexity        |

There is rarely a solution that optimizes every quality attribute simultaneously.

---

# Common Mistakes

* Focusing only on functional requirements.
* Ignoring scalability and future growth.
* Assuming all requirements have equal priority.
* Choosing technologies before understanding requirements.
* Overengineering simple applications.
* Forgetting compliance or security needs.

---

# Interview Perspective

System design interviews almost always begin with requirement clarification.

A good approach is:

### Step 1

Clarify functional requirements.

Examples:

* What features are required?
* Who are the users?
* What workflows should be supported?

### Step 2

Clarify non-functional requirements.

Examples:

* Scale?
* Latency?
* Availability?
* Consistency?
* Security?
* Budget?

Only after these are clear should you begin designing the architecture.

Interviewers appreciate candidates who ask thoughtful clarifying questions instead of making assumptions.

---

# Quick Revision

```text
Requirements

├── Functional
│     ├── Login
│     ├── Search
│     ├── Payment
│     ├── Chat
│     └── Notifications
│
└── Non-Functional
      ├── Scalability
      ├── Availability
      ├── Reliability
      ├── Performance
      ├── Security
      ├── Fault Tolerance
      ├── Maintainability
      ├── Observability
      └── Cost Efficiency
```

---

# Key Takeaways

* Functional requirements define **what** the system should do.
* Non-functional requirements define **how well** the system should perform.
* Both types of requirements are essential for successful system design.
* Always clarify requirements before discussing architecture or technologies.
* Many architectural decisions—such as caching, replication, load balancing, and database selection—are driven by non-functional requirements.
* Clear requirement gathering is the first and most important step in any system design interview or real-world project.

---

## 🎯 What's Next?

The introduction section is now complete.

The next folder is:

**`02-Computer-Science-Foundations/`**

Topics:

1. Processes & Threads
2. Concurrency
3. Synchronization
4. Memory Management
5. Scheduling
6. Deadlocks

These operating system concepts form the foundation for understanding scalability, parallelism, and distributed systems.
