# Transactions

> *"A transaction is a sequence of one or more database operations executed as a single logical unit of work. It ensures that all operations either succeed together or fail together."*

---

# Table of Contents

* What is a Transaction?
* Why Do We Need Transactions?
* Transaction Lifecycle
* Transaction States
* COMMIT
* ROLLBACK
* SAVEPOINT
* Auto Commit vs Manual Commit
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is a Transaction?

A **Transaction** is a group of SQL operations that are executed as **one logical unit**.

The database guarantees that:

* All operations succeed (**COMMIT**)
* OR all operations fail (**ROLLBACK**)

There is no partial execution.

Example:

```sql id="txn1"
BEGIN;

UPDATE Accounts
SET Balance = Balance - 500
WHERE ID = 1;

UPDATE Accounts
SET Balance = Balance + 500
WHERE ID = 2;

COMMIT;
```

Both updates are treated as one transaction.

---

# Why Do We Need Transactions?

Imagine transferring money between two bank accounts.

Steps:

1. Deduct money from Account A.
2. Add money to Account B.

If the database crashes after Step 1:

```text id="txn2"
Account A

₹5000 → ₹4500

↓

Crash

↓

Account B

Still ₹3000
```

Money is lost.

Transactions prevent this by rolling back incomplete changes.

---

# Transaction Lifecycle

A transaction follows a simple lifecycle.

```text id="txn3"
BEGIN

↓

Execute SQL Statements

↓

Success?

↓

YES ──► COMMIT

NO ───► ROLLBACK
```

---

# Transaction States

A transaction moves through several states during execution.

```text id="txn4"
Active

↓

Partially Committed

↓

Committed

OR

Failed

↓

Rolled Back
```

### Active

The transaction is executing SQL statements.

---

### Partially Committed

All SQL statements have executed, but changes are not yet permanently saved.

---

### Committed

The transaction completes successfully.

Changes become permanent.

---

### Failed

An error occurs.

Examples:

* Constraint violation
* System crash
* Deadlock

---

### Rolled Back

All changes are undone.

The database returns to its previous consistent state.

---

# BEGIN Transaction

Transactions typically start with:

```sql id="txn5"
BEGIN;
```

or

```sql id="txn6"
START TRANSACTION;
```

---

# COMMIT

`COMMIT` permanently saves all changes.

Example:

```sql id="txn7"
COMMIT;
```

After committing:

* Data is permanently stored.
* Changes become visible to other transactions.

---

# ROLLBACK

`ROLLBACK` undoes all changes made during the current transaction.

Example:

```sql id="txn8"
ROLLBACK;
```

Useful when:

* An error occurs.
* Business validation fails.
* The application crashes.

---

# SAVEPOINT

A **SAVEPOINT** creates a checkpoint within a transaction.

Instead of rolling back everything, you can roll back to a specific point.

Example:

```sql id="txn9"
BEGIN;

INSERT INTO Orders VALUES (...);

SAVEPOINT sp1;

UPDATE Inventory SET Stock = Stock - 1;

ROLLBACK TO sp1;

COMMIT;
```

Only the inventory update is undone.

---

# Auto Commit vs Manual Commit

## Auto Commit

Each SQL statement is treated as a separate transaction.

```text id="txn10"
INSERT

↓

Automatically COMMIT
```

Most databases enable Auto Commit by default.

---

## Manual Commit

The developer controls when to commit or roll back.

```text id="txn11"
BEGIN

↓

Multiple SQL Statements

↓

COMMIT
```

Preferred for complex business operations.

---

# Transaction Example

Suppose a customer places an order.

```text id="txn12"
Create Order

↓

Reduce Inventory

↓

Process Payment

↓

Generate Invoice

↓

COMMIT
```

If payment fails:

```text id="txn13"
ROLLBACK

↓

Order Removed

↓

Inventory Restored
```

The database remains consistent.

---

# Nested Transactions

Some databases support nested transactions using **SAVEPOINTS**.

```text id="txn14"
Main Transaction

↓

SAVEPOINT A

↓

SAVEPOINT B

↓

Rollback to A
```

This provides finer control over error recovery.

---

# Real-World Examples

## Banking

Money transfer:

* Debit Account
* Credit Account

Both operations must succeed together.

---

## E-Commerce

Order placement:

* Create Order
* Update Inventory
* Process Payment

Failure in any step triggers a rollback.

---

## Airline Reservation

Booking a seat:

* Reserve Seat
* Process Payment
* Confirm Ticket

Transactions prevent double booking.

---

# Best Practices

* Keep transactions short.
* Avoid unnecessary user interaction during a transaction.
* Commit as soon as work is complete.
* Roll back immediately on errors.
* Use SAVEPOINT for complex workflows.
* Avoid long-running transactions to reduce locking and improve concurrency.

---

# Interview Questions

* What is a database transaction?
* Why are transactions important?
* Difference between COMMIT and ROLLBACK?
* What is a SAVEPOINT?
* Difference between Auto Commit and Manual Commit?
* Explain the transaction lifecycle.
* What happens if the database crashes before COMMIT?
* How do transactions relate to ACID properties?

---

# Quick Revision

```text id="txn15"
Transaction

↓

BEGIN

↓

Execute SQL

↓

Success?

↓

COMMIT

OR

ROLLBACK

Commands

BEGIN

COMMIT

ROLLBACK

SAVEPOINT

States

Active

↓

Committed

OR

Failed

↓

Rolled Back
```

---

# Key Takeaways

* A **transaction** groups multiple database operations into a single logical unit.
* Transactions ensure either **all operations succeed** or **none are applied**, maintaining data consistency.
* **COMMIT** permanently saves changes, while **ROLLBACK** discards them.
* **SAVEPOINT** allows partial rollbacks within a transaction.
* Keeping transactions short and efficient improves performance and reduces locking issues.
* Transactions are fundamental to applications such as **banking, e-commerce, reservation systems, and payment gateways**.

---

> **Next Topic:** `04-Normalization.md`
