# Synchronization

> *"Synchronization is the process of coordinating multiple threads or processes so they can safely access shared resources without causing data corruption or inconsistent results."*

---

# Table of Contents

* What is Synchronization?
* Why Do We Need Synchronization?
* Shared Resources
* Race Condition
* Critical Section
* Critical Section Problem
* Synchronization Mechanisms
* Mutex
* Semaphore
* Binary vs Counting Semaphore
* Monitor
* Condition Variable
* Read-Write Lock
* Spinlock
* Atomic Operations
* Thread Synchronization Example
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Synchronization?

In a multi-threaded application, multiple threads often share resources such as:

* Variables
* Memory
* Files
* Databases
* Network Connections
* Queues

If two or more threads modify the same resource simultaneously, the data can become inconsistent.

**Synchronization** ensures that shared resources are accessed in a safe and controlled manner.

> **Only one thread should modify a shared resource at a time unless the operation is explicitly designed for concurrent access.**

---

# Why Do We Need Synchronization?

Imagine two users withdrawing money from the same bank account.

Initial Balance:

```text
₹1000
```

Thread A

```text
Withdraw ₹700
```

Thread B

```text
Withdraw ₹500
```

Without synchronization:

```text
Thread A reads balance = 1000

Thread B reads balance = 1000

Thread A writes 300

Thread B writes 500
```

Final Balance

```text
₹500 ❌
```

Correct Balance

```text
Insufficient Balance

OR

₹300
```

The incorrect result occurs because both threads accessed the shared data simultaneously.

---

# Shared Resources

Shared resources include anything multiple threads can access.

Examples:

```text
Shared Variable

Counter

Shared Queue

Database Record

Cache

File

Socket
```

Whenever multiple threads access shared resources, synchronization is required.

---

# Race Condition

A **Race Condition** occurs when the output of a program depends on the unpredictable timing of multiple threads.

Example:

```cpp
counter = 0

Thread A

counter++

Thread B

counter++
```

Expected:

```text
2
```

Possible Result:

```text
1
```

Reason:

Both threads read the same value before either writes the updated value.

---

# Critical Section

A **Critical Section** is the part of a program where shared resources are accessed.

Example:

```cpp
balance -= amount;
```

Only one thread should execute this statement at a time.

---

# Critical Section Problem

A correct synchronization solution should satisfy three conditions.

## 1. Mutual Exclusion

Only one thread can enter the critical section at a time.

---

## 2. Progress

If no thread is inside the critical section, another waiting thread should eventually be allowed to enter.

---

## 3. Bounded Waiting

A thread should not wait forever.

Every waiting thread should get a chance to execute.

---

# Synchronization Mechanisms

Operating systems provide several synchronization primitives.

```text
Synchronization

│

├── Mutex

├── Semaphore

├── Monitor

├── Condition Variable

├── Read-Write Lock

├── Spinlock

└── Atomic Operations
```

Each mechanism is suited for different use cases.

---

# Mutex (Mutual Exclusion)

A **Mutex** allows only **one thread** to access a shared resource at any given time.

```text
Thread A

↓

Lock Mutex

↓

Critical Section

↓

Unlock Mutex
```

While Thread A holds the mutex, other threads must wait.

### Advantages

* Simple
* Easy to understand
* Prevents race conditions

### Disadvantages

* Blocking
* Possible deadlocks if locks are not managed carefully

---

# Semaphore

A **Semaphore** controls access to a resource using a counter.

Instead of allowing only one thread, it can allow multiple threads.

Operations:

```text
wait()

signal()
```

---

## Binary Semaphore

Counter values:

```text
0 or 1
```

Acts similarly to a mutex.

---

## Counting Semaphore

Example:

```text
Semaphore = 5
```

Five threads can enter simultaneously.

Useful for:

* Database Connection Pools
* Printer Pools
* Thread Pools

---

# Mutex vs Semaphore

| Mutex                     | Semaphore                    |
| ------------------------- | ---------------------------- |
| One owner                 | No owner                     |
| Binary                    | Binary or Counting           |
| One thread at a time      | Multiple threads allowed     |
| Used for mutual exclusion | Used for resource management |

---

# Monitor

A **Monitor** is a high-level synchronization construct that combines:

* Shared data
* Methods
* Automatic locking

Only one thread can execute monitor methods at a time.

Languages supporting monitors:

* Java (`synchronized`)
* C#
* Kotlin

Example:

```java
synchronized void deposit() {
    balance += amount;
}
```

---

# Condition Variable

Sometimes a thread should wait until a specific condition becomes true.

Example:

Producer-Consumer Problem

```text
Producer

↓

Queue

↓

Consumer
```

If the queue is empty,

Consumer waits.

Producer adds data.

Consumer resumes.

Condition variables avoid busy waiting.

---

# Read-Write Lock

Many applications perform far more **reads** than **writes**.

A Read-Write Lock allows:

```text
Readers

✔ Multiple Allowed

Writer

✔ Only One Allowed
```

Example:

Database Systems

Thousands of users can read simultaneously,

but updates require exclusive access.

Advantages:

* Better throughput for read-heavy workloads.

---

# Spinlock

Instead of sleeping while waiting for a lock,

a thread continuously checks whether the lock has become available.

```text
while(lock == occupied)
{
    keep checking
}
```

Advantages:

* Very fast for short waiting periods.

Disadvantages:

* Wastes CPU cycles if held for too long.

Used in:

* Operating Systems
* Device Drivers
* Kernel Programming

---

# Atomic Operations

An **Atomic Operation** executes completely without interruption.

Example:

```cpp
std::atomic<int> counter;

counter++;
```

Atomic operations are implemented using CPU instructions such as:

```text
Compare-And-Swap (CAS)

Fetch-And-Add
```

Advantages:

* Faster than locks for simple operations.
* No explicit locking required.

---

# Thread Synchronization Example

Without synchronization:

```text
Thread A

Read Counter = 5

Increment

Write 6

Thread B

Read Counter = 5

Increment

Write 6
```

Final Value

```text
6 ❌
```

Correct Value

```text
7 ✔
```

Using a mutex:

```text
Thread A

Lock

Increment

Unlock

↓

Thread B

Lock

Increment

Unlock
```

Final Value

```text
7 ✔
```

---

# Best Practices

* Keep critical sections as small as possible.
* Avoid nested locks.
* Always release acquired locks.
* Prefer immutable objects when possible.
* Use atomic operations for simple counters.
* Use Read-Write Locks for read-heavy systems.
* Avoid excessive synchronization because it reduces parallelism.

---

# Interview Questions

### Basic

* What is synchronization?
* Why is synchronization needed?
* What is a race condition?
* What is a critical section?
* Difference between mutex and semaphore?

### Intermediate

* Explain binary and counting semaphores.
* What is a monitor?
* What is a condition variable?
* What is a read-write lock?
* What is a spinlock?

### Advanced

* How does Compare-And-Swap (CAS) work?
* Why are atomic operations faster than mutexes?
* When should spinlocks be preferred over mutexes?
* How does Java's `synchronized` keyword work?
* How do databases synchronize concurrent transactions?

---

# Quick Revision

```text
Synchronization

│

├── Prevent Race Conditions

├── Protect Shared Resources

├── Mutual Exclusion

└── Thread Safety

Mechanisms

│

├── Mutex

├── Semaphore

├── Monitor

├── Condition Variable

├── Read-Write Lock

├── Spinlock

└── Atomic Operations

Problems

│

├── Race Condition

├── Deadlock

├── Starvation

└── Data Corruption
```

---

# Key Takeaways

* Synchronization coordinates concurrent threads and processes to safely access shared resources.
* Race conditions occur when multiple threads modify shared data without proper coordination.
* A **mutex** provides exclusive access to a resource, while a **semaphore** controls access to a limited number of resources.
* Monitors, condition variables, read-write locks, spinlocks, and atomic operations address different synchronization scenarios.
* Choosing the right synchronization mechanism depends on the workload, contention level, and performance requirements.
* Proper synchronization is essential for building reliable multi-threaded applications, databases, operating systems, and distributed systems.

---

> **Next Topic:** `04-Memory-Management.md`
