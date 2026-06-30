# Isolation Levels

> *"Isolation Levels define how concurrent transactions interact with each other. They determine the visibility of changes made by one transaction to other transactions, balancing data consistency and system performance."*

---

# Table of Contents

* What is Isolation?
* Why Do We Need Isolation Levels?
* Concurrency Problems
* Isolation Levels
* Read Uncommitted
* Read Committed
* Repeatable Read
* Serializable
* Isolation Level Comparison
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Isolation?

**Isolation** is one of the four **ACID** properties.

It ensures that multiple transactions executing simultaneously do not interfere with each other.

Example:

```text id="iso1"
Transaction A

||

Transaction B
```

Each transaction should behave as if it is the only one running.

---

# Why Do We Need Isolation Levels?

Imagine two users updating the same bank account simultaneously.

```text id="iso2"
Balance

₹10,000

↓

User A Withdraws ₹2,000

||

User B Withdraws ₹3,000
```

Without proper isolation:

* Incorrect balance
* Lost updates
* Inconsistent data

Isolation levels prevent these issues.

---

# Concurrency Problems

## 1. Dirty Read

A transaction reads data that has **not yet been committed**.

Example:

```text id="iso3"
Transaction A

Balance = ₹9000

(Not Committed)

↓

Transaction B

Reads ₹9000
```

If Transaction A rolls back, Transaction B has read invalid data.

---

## 2. Non-Repeatable Read

A transaction reads the same row twice and gets different values.

Example:

```text id="iso4"
Transaction A

Reads Salary = ₹50,000

↓

Transaction B Updates Salary

↓

Transaction A Reads Again

Salary = ₹55,000
```

The value changed during the transaction.

---

## 3. Phantom Read

A transaction executes the same query twice but gets additional rows.

Example:

```text id="iso5"
Transaction A

SELECT * FROM Employees
WHERE Department='IT'

↓

Transaction B Inserts New IT Employee

↓

Transaction A Executes Same Query

Extra Row Appears
```

---

# Isolation Levels

There are four standard SQL isolation levels.

```text id="iso6"
Read Uncommitted

↓

Read Committed

↓

Repeatable Read

↓

Serializable
```

As isolation increases:

* Data consistency improves.
* Performance decreases.

---

# 1. Read Uncommitted

Lowest isolation level.

Allows:

* Dirty Reads
* Non-Repeatable Reads
* Phantom Reads

Fastest but least reliable.

---

# 2. Read Committed

A transaction only reads **committed data**.

Prevents:

* Dirty Reads

Still allows:

* Non-Repeatable Reads
* Phantom Reads

This is the default isolation level in databases like PostgreSQL and Oracle.

---

# 3. Repeatable Read

Ensures that rows read during a transaction remain unchanged.

Prevents:

* Dirty Reads
* Non-Repeatable Reads

May still allow:

* Phantom Reads (depending on database implementation)

This is the default isolation level in MySQL (InnoDB).

---

# 4. Serializable

Highest isolation level.

Transactions execute as if they run one after another.

Prevents:

* Dirty Reads
* Non-Repeatable Reads
* Phantom Reads

Provides maximum consistency but reduces concurrency and throughput.

---

# Isolation Level Comparison

| Isolation Level  | Dirty Read  | Non-Repeatable Read | Phantom Read |
| ---------------- | ----------- | ------------------- | ------------ |
| Read Uncommitted | ❌ Possible  | ❌ Possible          | ❌ Possible   |
| Read Committed   | ✅ Prevented | ❌ Possible          | ❌ Possible   |
| Repeatable Read  | ✅ Prevented | ✅ Prevented         | ❌ Possible*  |
| Serializable     | ✅ Prevented | ✅ Prevented         | ✅ Prevented  |

> *Some databases (e.g., MySQL InnoDB) use additional mechanisms that also prevent many phantom reads.*

---

# Real-World Example

## Banking System

Money transfers require:

```text id="iso7"
Serializable
```

Highest consistency is essential.

---

## E-Commerce Website

Order placement commonly uses:

```text id="iso8"
Read Committed

or

Repeatable Read
```

to balance performance and consistency.

---

## Social Media Feed

Fetching posts often uses:

```text id="iso9"
Read Committed
```

because slight inconsistencies are usually acceptable.

---

# Best Practices

* Use the lowest isolation level that satisfies business requirements.
* Use **Serializable** only when strong consistency is critical.
* Keep transactions short.
* Avoid long-running transactions.
* Monitor for deadlocks in highly concurrent systems.

---

# Interview Questions

* What is Isolation in ACID?
* What is a Dirty Read?
* What is a Phantom Read?
* Difference between Dirty Read and Non-Repeatable Read?
* Explain the four isolation levels.
* Which isolation level is the safest?
* Which isolation level provides the best performance?
* What is the default isolation level in MySQL?
* What is the default isolation level in PostgreSQL?

---

# Quick Revision

```text id="iso10"
Isolation Levels

↓

Read Uncommitted

↓

Read Committed

↓

Repeatable Read

↓

Serializable

Concurrency Problems

Dirty Read

↓

Non-Repeatable Read

↓

Phantom Read

Higher Isolation

↓

Better Consistency

↓

Lower Performance
```

---

# Key Takeaways

* **Isolation** is an ACID property that controls how concurrent transactions interact.
* Isolation levels help prevent concurrency issues such as **Dirty Reads**, **Non-Repeatable Reads**, and **Phantom Reads**.
* The four standard isolation levels are **Read Uncommitted**, **Read Committed**, **Repeatable Read**, and **Serializable**.
* Higher isolation levels provide stronger consistency but reduce concurrency and overall performance.
* Choosing the appropriate isolation level depends on the application's consistency requirements and performance goals.

---

> **Next Topic:** `09-NoSQL-Databases.md`
