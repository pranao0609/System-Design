# ACID Properties

> *"ACID is a set of four properties that ensure database transactions are processed reliably, maintaining data consistency even in the presence of failures."*

---

# Table of Contents

* What is ACID?
* Why Do We Need ACID?
* What is a Transaction?
* Atomicity
* Consistency
* Isolation
* Durability
* ACID Example
* ACID vs BASE
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is ACID?

**ACID** stands for:

* **A** → Atomicity
* **C** → Consistency
* **I** → Isolation
* **D** → Durability

These four properties ensure that every database transaction is executed **reliably and safely**, even if errors, crashes, or power failures occur.

Relational databases such as:

* PostgreSQL
* MySQL (InnoDB)
* Oracle
* SQL Server

implement ACID transactions.

---

# Why Do We Need ACID?

Imagine transferring **₹1000** from Account A to Account B.

Steps:

1. Deduct ₹1000 from Account A.
2. Add ₹1000 to Account B.

If the system crashes after Step 1 but before Step 2:

```text id="acid1"
Account A

₹5000 → ₹4000

Account B

₹3000 → ₹3000
```

₹1000 disappears.

ACID prevents such inconsistencies.

---

# What is a Transaction?

A **Transaction** is a sequence of database operations treated as a **single unit of work**.

Example:

```sql id="acid2"
BEGIN;

UPDATE Accounts
SET Balance = Balance - 1000
WHERE ID = 1;

UPDATE Accounts
SET Balance = Balance + 1000
WHERE ID = 2;

COMMIT;
```

Either **all operations succeed** or **none of them are applied**.

---

# A – Atomicity

**Atomicity** means:

> **"All or Nothing."**

A transaction either completes fully or is rolled back completely.

Example:

```text id="acid3"
Transfer Money

↓

Deduct ₹1000

↓

System Crash

↓

Rollback

↓

Original Balance Restored
```

Atomicity ensures that partial updates never occur.

---

# C – Consistency

A transaction must move the database from **one valid state to another valid state**.

Rules and constraints must always be satisfied.

Example:

```text id="acid4"
Before Transaction

Total Money = ₹8000

↓

Transfer ₹1000

↓

After Transaction

Total Money = ₹8000
```

No money is created or lost.

Consistency also enforces:

* Primary Keys
* Foreign Keys
* CHECK Constraints
* UNIQUE Constraints

---

# I – Isolation

Multiple transactions often execute simultaneously.

Isolation ensures they do not interfere with one another.

Example:

```text id="acid5"
Transaction A

Updating Balance

||

Transaction B

Reading Balance
```

Without isolation, Transaction B might read incomplete data.

Isolation prevents concurrency issues.

---

# D – Durability

Once a transaction is **committed**, its changes are permanent.

Even if:

* Power fails
* Server crashes
* Database restarts

the committed data remains.

Example:

```text id="acid6"
COMMIT

↓

Power Failure

↓

Restart Database

↓

Data Still Exists
```

Durability is achieved using:

* Transaction Logs
* Write-Ahead Logging (WAL)
* Disk Persistence

---

# ACID Summary

| Property    | Meaning                                 |
| ----------- | --------------------------------------- |
| Atomicity   | All operations succeed or none do       |
| Consistency | Database remains valid                  |
| Isolation   | Concurrent transactions don't interfere |
| Durability  | Committed data is never lost            |

---

# ACID Example

Consider an online shopping application.

```text id="acid7"
Place Order

↓

Reduce Inventory

↓

Process Payment

↓

Generate Invoice

↓

Commit
```

If payment fails:

```text id="acid8"
Rollback

↓

Inventory Restored

↓

Order Cancelled
```

The database remains consistent.

---

# ACID vs BASE

| ACID                    | BASE                                                  |
| ----------------------- | ----------------------------------------------------- |
| Strong Consistency      | Eventual Consistency                                  |
| Immediate Correctness   | High Availability                                     |
| Common in SQL Databases | Common in NoSQL Databases                             |
| Suitable for Banking    | Suitable for Social Media & Large Distributed Systems |

---

# Real-World Examples

## Banking

Money transfers require:

* Atomicity
* Consistency
* Durability

---

## E-Commerce

Order placement:

* Deduct inventory
* Create order
* Process payment

All operations should succeed together.

---

## Airline Reservation

Seat booking must prevent two users from booking the same seat simultaneously.

Isolation ensures only one booking succeeds.

---

# Advantages

* Prevents data corruption.
* Ensures reliable transactions.
* Maintains database integrity.
* Supports concurrent users safely.
* Provides crash recovery.

---

# Limitations

* Additional processing overhead.
* Can reduce throughput in highly concurrent systems.
* Strong consistency may reduce scalability in distributed environments.

---

# Interview Questions

* What does ACID stand for?
* What is Atomicity?
* Difference between Atomicity and Durability?
* Why is Isolation important?
* What is Consistency in databases?
* Why do banking systems require ACID?
* Difference between ACID and BASE?
* Which databases support ACID transactions?

---

# Quick Revision

```text id="acid9"
ACID

↓

Atomicity

(All or Nothing)

↓

Consistency

(Valid State)

↓

Isolation

(No Interference)

↓

Durability

(Permanent Storage)

Example

Money Transfer

↓

Commit

↓

Crash

↓

Data Safe
```

---

# Key Takeaways

* **ACID** ensures reliable and consistent database transactions.
* **Atomicity** guarantees that a transaction either completes entirely or is rolled back.
* **Consistency** ensures that database rules and constraints are always maintained.
* **Isolation** prevents concurrent transactions from interfering with one another.
* **Durability** guarantees that committed data survives system failures.
* ACID is critical for applications such as **banking, payments, e-commerce, healthcare, and financial systems**, where data correctness is essential.

---

> **Next Topic:** `03-Transactions.md`
