# Deadlocks

> *"A deadlock occurs when two or more processes or threads are permanently waiting for resources held by each other, preventing all of them from making progress."*

---

# Table of Contents

* What is a Deadlock?
* Why Do Deadlocks Occur?
* Real-Life Analogy
* Necessary Conditions for Deadlock
* Resource Allocation Graph (RAG)
* Deadlock Example
* Types of Resources
* Deadlock Handling Strategies
* Deadlock Prevention
* Deadlock Avoidance
* Banker's Algorithm
* Deadlock Detection
* Deadlock Recovery
* Deadlock vs Starvation vs Livelock
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is a Deadlock?

A **Deadlock** is a situation where two or more processes or threads are unable to continue because each is waiting for a resource that another process or thread holds.

As a result:

* No process can proceed.
* CPU utilization decreases.
* The application may freeze.
* Resources remain occupied indefinitely.

Deadlocks commonly occur in:

* Operating Systems
* Databases
* Multi-threaded Applications
* Distributed Systems

---

# Why Do Deadlocks Occur?

Deadlocks occur when multiple processes compete for limited resources and acquire them in different orders.

Example:

```text
Thread A

Locks Resource 1

↓

Requests Resource 2

----------------------------

Thread B

Locks Resource 2

↓

Requests Resource 1
```

Both threads wait forever.

---

# Real-Life Analogy

Imagine two cars entering a one-lane bridge from opposite directions.

```text
Car A  ---> || <--- Car B
```

* Car A waits for Car B.
* Car B waits for Car A.

Neither can move.

This is a deadlock.

---

# Coffman's Four Necessary Conditions

A deadlock can occur **only if all four conditions are true simultaneously**.

```text
Deadlock

│

├── Mutual Exclusion

├── Hold and Wait

├── No Preemption

└── Circular Wait
```

---

## 1. Mutual Exclusion

At least one resource cannot be shared.

Example:

* Printer
* File Lock
* Database Row Lock

Only one process can use it at a time.

---

## 2. Hold and Wait

A process holds one resource while waiting for another.

Example:

```text
Thread A

Holding Lock A

Waiting for Lock B
```

---

## 3. No Preemption

Resources cannot be forcibly taken away.

The process must release them voluntarily.

---

## 4. Circular Wait

A circular chain of waiting exists.

```text
Thread A

Waiting for Thread B

↓

Thread B

Waiting for Thread C

↓

Thread C

Waiting for Thread A
```

This creates an infinite cycle.

---

# Resource Allocation Graph (RAG)

A Resource Allocation Graph visually represents resource ownership and waiting relationships.

Notation:

* Circle = Process
* Square = Resource

Example:

```text
P1 -----> R1
^          |
|          v
R2 <----- P2
```

Meaning:

* P1 is waiting for R1.
* R1 is allocated to P2.
* P2 is waiting for R2.
* R2 is allocated to P1.

A cycle in the graph may indicate a deadlock.

---

# Deadlock Example

Consider two locks:

```cpp
Thread A

lock(A);

lock(B);
```

```cpp
Thread B

lock(B);

lock(A);
```

Execution:

```text
Thread A

Locks A

↓

Waiting for B

-----------------------

Thread B

Locks B

↓

Waiting for A
```

Neither thread can continue.

---

# Types of Resources

Resources are broadly classified into two categories.

---

## Preemptable Resources

Can be taken away safely.

Examples:

* CPU
* Main Memory
* Network Bandwidth

---

## Non-Preemptable Resources

Cannot be taken away without affecting correctness.

Examples:

* Printer
* File Lock
* Database Lock
* Mutex

Deadlocks usually involve non-preemptable resources.

---

# Deadlock Handling Strategies

Operating systems typically use one of four strategies.

```text
Deadlock Handling

│

├── Prevention

├── Avoidance

├── Detection

└── Recovery
```

---

# Deadlock Prevention

Prevent deadlocks by ensuring **at least one of Coffman's conditions can never occur**.

Examples:

### Break Hold and Wait

Require processes to request all required resources at once.

### Break Circular Wait

Acquire resources in a fixed global order.

Example:

```text
Always

Lock A

↓

Lock B

↓

Lock C
```

Every thread follows the same order.

---

# Deadlock Avoidance

Avoidance dynamically checks whether granting a resource request keeps the system in a **safe state**.

The operating system decides:

> Should this request be granted?

If granting the request may lead to a deadlock, it is postponed.

---

# Safe State

A system is in a **safe state** if there exists an execution order in which every process can finish.

Example:

```text
P1

↓

P3

↓

P2
```

All processes complete successfully.

---

# Unsafe State

An unsafe state does **not** necessarily mean a deadlock has occurred.

It means the system **could** enter a deadlock depending on future resource requests.

---

# Banker's Algorithm

The **Banker's Algorithm** is the classic deadlock avoidance algorithm.

It works like a bank lending money.

The bank grants loans only if it can still satisfy all customers eventually.

Algorithm inputs:

* Maximum Resource Requirement
* Current Allocation
* Available Resources

If the request keeps the system in a safe state:

```text
Grant Request ✔
```

Otherwise:

```text
Wait ✖
```

---

# Deadlock Detection

Some operating systems allow deadlocks to occur and periodically check for them.

Methods include:

* Resource Allocation Graph
* Wait-For Graph
* Cycle Detection Algorithms

If a cycle is found:

```text
Deadlock Detected
```

---

# Deadlock Recovery

Once detected, the operating system must recover.

Common techniques:

---

## 1. Terminate Processes

Kill one or more processes.

Advantages:

* Simple

Disadvantages:

* Loss of work

---

## 2. Resource Preemption

Forcefully reclaim resources.

Advantages:

* Can resolve deadlocks without terminating all processes.

Disadvantages:

* Rollback may be required.

---

## 3. Rollback

Restore the process to a previous checkpoint and retry execution.

Used in:

* Databases
* Distributed Systems

---

# Deadlock vs Starvation vs Livelock

| Deadlock                           | Starvation                                                         | Livelock                                            |
| ---------------------------------- | ------------------------------------------------------------------ | --------------------------------------------------- |
| Processes stop permanently         | A process waits indefinitely because others keep getting resources | Processes keep changing state but make no progress  |
| Usually caused by circular waiting | Usually caused by unfair scheduling                                | Usually caused by excessive coordination            |
| No work is performed               | Other processes continue                                           | CPU remains active but useful work is not completed |

---

# Real-World Examples

## Database Transactions

Transaction A:

```sql
Lock Customer Table
```

Transaction B:

```sql
Lock Orders Table
```

Later:

```text
A wants Orders

B wants Customer
```

Deadlock occurs.

Most databases automatically detect deadlocks and abort one transaction.

---

## Operating Systems

Two processes lock files in different orders.

Each waits for the other's file lock.

---

## Banking Systems

Two concurrent money transfers may wait on account locks if locks are acquired inconsistently.

---

## Distributed Systems

Distributed transactions spanning multiple services may deadlock if resource acquisition is not coordinated properly.

---

# Best Practices

* Acquire locks in a consistent order.
* Keep critical sections short.
* Release locks as soon as possible.
* Avoid nested locks whenever possible.
* Use timeouts when acquiring locks.
* Prefer lock-free or optimistic concurrency techniques where appropriate.
* Monitor applications for deadlocks in production.

---

# Interview Questions

### Basic

* What is a deadlock?
* What causes a deadlock?
* What are Coffman's conditions?
* What is circular wait?
* What is a Resource Allocation Graph?

### Intermediate

* Explain deadlock prevention.
* Explain deadlock avoidance.
* What is the difference between prevention and avoidance?
* What is a safe state?
* What is Banker's Algorithm?

### Advanced

* How do databases detect deadlocks?
* How does lock ordering prevent deadlocks?
* Difference between deadlock and livelock?
* Difference between deadlock and starvation?
* How do distributed systems avoid deadlocks?

---

# Quick Revision

```text
Deadlock

│

├── Mutual Exclusion

├── Hold and Wait

├── No Preemption

└── Circular Wait

Handling

│

├── Prevention

├── Avoidance

├── Detection

└── Recovery

Algorithms

│

├── Resource Allocation Graph

├── Wait-For Graph

└── Banker's Algorithm
```

---

# Key Takeaways

* A **deadlock** occurs when processes or threads wait indefinitely for resources held by one another.
* All four of **Coffman's conditions** must hold for a deadlock to occur.
* Deadlocks can be handled through **prevention**, **avoidance**, **detection**, or **recovery**.
* **Banker's Algorithm** is a classic deadlock avoidance technique that grants requests only when the system remains in a safe state.
* Acquiring locks in a consistent order and minimizing lock duration are effective ways to reduce the likelihood of deadlocks.
* Understanding deadlocks is essential for designing reliable operating systems, databases, multi-threaded applications, and distributed systems.

---

# 🎉 Section Complete

You have now completed **02 - Computer Science Foundations**.

## What You've Learned

* ✅ Processes & Threads
* ✅ Concurrency
* ✅ Synchronization
* ✅ Memory Management
* ✅ CPU Scheduling
* ✅ Deadlocks

These concepts provide the operating system foundation needed for understanding web servers, databases, distributed systems, and scalable backend architectures.

---



This is one of the most important sections for system design because every distributed application communicates over a network.
