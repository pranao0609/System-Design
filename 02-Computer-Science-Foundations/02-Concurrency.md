# Concurrency

> *"Concurrency is about dealing with multiple tasks at the same time, while parallelism is about executing multiple tasks at the same instant."*

---

# Table of Contents

* What is Concurrency?
* Why Do We Need Concurrency?
* Concurrency vs Parallelism
* How Concurrency Works
* Concurrency Models
* Problems in Concurrent Systems
* Race Condition
* Critical Section
* Thread Safety
* Atomic Operations
* Lock-Free Programming
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Concurrency?

**Concurrency** is the ability of a system to make progress on multiple tasks by managing and switching between them efficiently.

A concurrent system does **not** necessarily execute multiple tasks simultaneously. Instead, it allows multiple tasks to **overlap in execution**, giving the illusion that they are running at the same time.

For example:

* A web server handles thousands of client requests.
* A browser downloads files while rendering web pages.
* A mobile application plays music while downloading updates.

All of these are examples of concurrency.

---

# Why Do We Need Concurrency?

Modern applications perform many tasks simultaneously.

Examples include:

* Handling multiple users
* Downloading files
* Reading databases
* Writing logs
* Processing payments
* Sending notifications
* Streaming videos

Without concurrency:

* CPU resources remain underutilized.
* Applications become slow and unresponsive.
* Long-running tasks block other operations.

Concurrency improves:

* Responsiveness
* Resource utilization
* Throughput
* User experience

---

# Concurrency vs Parallelism

These terms are often confused but represent different concepts.

## Concurrency

Multiple tasks **make progress together**, but they may share a single CPU core.

```text
CPU

Task A
████
     ████
          ███

Task B
    ████
         ███
```

The operating system rapidly switches between tasks.

---

## Parallelism

Multiple tasks execute **at the exact same time** using multiple CPU cores.

```text
Core 1

Task A
██████████

Core 2

Task B
██████████
```

---

## Comparison

| Feature            | Concurrency                           | Parallelism                           |
| ------------------ | ------------------------------------- | ------------------------------------- |
| Meaning            | Multiple tasks make progress together | Multiple tasks execute simultaneously |
| CPU Cores          | One or many                           | Multiple                              |
| Goal               | Better responsiveness                 | Faster execution                      |
| Requires Multicore | No                                    | Yes                                   |
| Example            | Browser tabs                          | Video rendering                       |

---

# How Concurrency Works

The operating system scheduler allocates a small time slice to each thread or process.

```text
Time →

Thread A

████

Thread B

    ████

Thread C

        ████

Thread A

             ███
```

Because switching happens very quickly, users perceive all tasks as running together.

---

# Concurrency Models

Different systems achieve concurrency using different approaches.

---

## 1. Multi-Threading

Multiple threads execute within the same process.

```text
Process

│
├── Thread 1
├── Thread 2
├── Thread 3
└── Thread 4
```

Advantages

* Lightweight
* Shared memory
* Fast communication

Disadvantages

* Race conditions
* Synchronization complexity

---

## 2. Multi-Processing

Multiple independent processes execute concurrently.

```text
Process A

Process B

Process C
```

Advantages

* Better isolation
* Crash resistance

Disadvantages

* Higher memory usage
* IPC required

---

## 3. Event-Driven Concurrency

Instead of creating many threads, a single event loop handles many events asynchronously.

Example:

```text
Client Requests
       │
       ▼
   Event Queue
       │
       ▼
   Event Loop
       │
       ▼
Callbacks
```

Popular in:

* Node.js
* Nginx
* Redis

---

## 4. Asynchronous Programming

A task begins execution and continues later without blocking the current thread.

Example:

```text
Read File

↓

Continue Processing

↓

File Finished

↓

Handle Result
```

Languages:

* JavaScript
* Python (asyncio)
* C#
* Kotlin
* Rust

---

# Problems in Concurrent Systems

Running multiple tasks simultaneously introduces several challenges.

---

## Race Condition

A **race condition** occurs when multiple threads access and modify shared data simultaneously, causing unpredictable results.

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

Possible result:

```text
1
```

because both threads read the same value before either writes the updated value.

---

## Critical Section

A **critical section** is a block of code that accesses shared resources.

Only one thread should execute it at a time.

Example:

```cpp
balance = balance - amount;
```

If multiple threads modify `balance` simultaneously, incorrect results may occur.

---

## Deadlock

Two or more threads wait indefinitely for each other to release resources.

```text
Thread A

Waiting for Lock B

Thread B

Waiting for Lock A
```

Neither thread can continue.

This topic is covered in detail in the **Deadlocks** chapter.

---

## Starvation

A thread never receives CPU time because higher-priority threads continuously execute.

---

## Livelock

Threads remain active but continuously react to each other without making useful progress.

Unlike a deadlock, threads are not blocked—they are simply unable to complete their work.

---

# Thread Safety

A piece of code is **thread-safe** if it produces correct results when executed by multiple threads simultaneously.

Methods to achieve thread safety:

* Mutexes
* Semaphores
* Atomic Operations
* Read-Write Locks
* Thread-safe Data Structures
* Immutability

---

# Atomic Operations

An **atomic operation** executes completely or not at all.

No other thread can observe it in an intermediate state.

Example:

```cpp
std::atomic<int> counter;

counter++;
```

Atomic operations eliminate many race conditions without requiring explicit locks.

---

# Lock-Free Programming

Some high-performance systems avoid traditional locks.

Instead, they use:

* Atomic Instructions
* Compare-And-Swap (CAS)
* Lock-Free Queues
* Lock-Free Stacks

Advantages:

* Better scalability
* Lower latency
* Reduced contention

Disadvantages:

* More difficult to implement and reason about

Lock-free algorithms are common in databases, operating systems, and high-performance messaging systems.

---

# Real-World Examples

## Web Server

```text
Clients

│
▼

Web Server

├── Worker Thread 1
├── Worker Thread 2
├── Worker Thread 3
└── Worker Thread N
```

Each thread handles incoming client requests concurrently.

---

## Browser

Modern browsers execute multiple concurrent tasks:

* Rendering HTML
* Running JavaScript
* Downloading Images
* Playing Audio
* Handling User Input

This ensures a smooth user experience.

---

## Database

Database systems execute many SQL queries concurrently while maintaining consistency through synchronization and transaction management.

---

# Best Practices

* Minimize shared mutable state.
* Prefer immutable objects where possible.
* Keep critical sections small.
* Avoid nested locks.
* Use thread-safe libraries.
* Choose asynchronous I/O for I/O-bound workloads.
* Use thread pools instead of creating threads repeatedly.

---

# Interview Questions

### Basic

* What is concurrency?
* Difference between concurrency and parallelism?
* What is a race condition?
* What is a critical section?
* What is thread safety?

### Intermediate

* Explain atomic operations.
* What causes deadlocks?
* What is starvation?
* What is livelock?
* What is asynchronous programming?

### Advanced

* Explain Compare-And-Swap (CAS).
* Why are thread pools used?
* When should lock-free programming be preferred?
* How does concurrency improve scalability in web servers?

---

# Quick Revision

```text
Concurrency
│
├── Multiple Tasks
├── Time Sharing
├── Scheduler
└── Better Responsiveness

Concurrency Models
│
├── Multithreading
├── Multiprocessing
├── Event Loop
└── Async Programming

Problems
│
├── Race Condition
├── Deadlock
├── Starvation
├── Livelock
└── Data Corruption

Solutions
│
├── Mutex
├── Semaphore
├── Atomic Operations
├── Read-Write Lock
└── Thread-Safe Structures
```

---

# Key Takeaways

* **Concurrency** enables multiple tasks to make progress together, improving responsiveness and resource utilization.
* **Parallelism** executes multiple tasks simultaneously using multiple CPU cores.
* Concurrent systems face challenges such as race conditions, deadlocks, starvation, and livelock.
* Thread safety is achieved using synchronization mechanisms, atomic operations, and careful management of shared state.
* Modern web servers, browsers, databases, and distributed systems rely heavily on concurrency to handle large numbers of requests efficiently.

---

> **Next Topic:** `03-Synchronization.md`
