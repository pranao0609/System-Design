# 02. Computer Science Foundations

Before designing scalable distributed systems, it's essential to understand how a computer executes programs internally. Concepts such as **processes, threads, concurrency, synchronization, memory management, scheduling, and deadlocks** form the foundation of backend engineering and system design.

Many production issues—race conditions, high latency, thread contention, memory leaks, CPU starvation, and deadlocks—can only be understood by having a solid grasp of Operating System fundamentals.

---

# 📚 Topics Covered

## 1. Processes & Threads

Learn how operating systems execute programs, the difference between processes and threads, context switching, and inter-process communication.

📄 **File:** `01-Processes-and-Threads.md`

---

## 2. Concurrency

Understand how multiple tasks make progress simultaneously, different concurrency models, and challenges such as race conditions and thread safety.

📄 **File:** `02-Concurrency.md`

---

## 3. Synchronization

Learn how operating systems coordinate concurrent execution using mutexes, semaphores, monitors, condition variables, read-write locks, and atomic operations.

📄 **File:** `03-Synchronization.md`

---

## 4. Memory Management

Explore virtual memory, paging, segmentation, heap, stack, memory allocation, garbage collection, and memory fragmentation.

📄 **File:** `04-Memory-Management.md`

---

## 5. CPU Scheduling

Study how operating systems schedule processes using algorithms such as FCFS, SJF, Priority Scheduling, Round Robin, and Multilevel Feedback Queue.

📄 **File:** `05-CPU-Scheduling.md`

---

## 6. Deadlocks

Understand deadlocks, Coffman's Conditions, prevention, avoidance, detection, recovery techniques, and starvation.

📄 **File:** `06-Deadlocks.md`

---

# 🎯 Learning Objectives

After completing this section, you should be able to:

* Explain how programs execute inside an operating system.
* Differentiate between processes and threads.
* Understand concurrency and parallelism.
* Prevent race conditions using synchronization mechanisms.
* Explain virtual memory and memory allocation.
* Compare CPU scheduling algorithms.
* Detect and resolve deadlocks.
* Relate OS concepts to backend systems and distributed architectures.

---

# 📂 Folder Structure

```text
02-Computer-Science-Foundations/
│
├── README.md
├── 01-Processes-and-Threads.md
├── 02-Concurrency.md
├── 03-Synchronization.md
├── 04-Memory-Management.md
├── 05-CPU-Scheduling.md
└── 06-Deadlocks.md
```

---

# 💡 Why This Section Matters

Modern distributed systems are built on top of operating systems.

Understanding these concepts helps explain:

* Why web servers use thread pools.
* Why databases implement locking.
* Why race conditions occur.
* How high-performance servers handle thousands of concurrent requests.
* How operating systems allocate memory.
* Why deadlocks happen in databases.
* Why synchronization is required in multi-threaded applications.

These concepts are directly applicable to technologies like Java, C++, Go, Rust, Kubernetes, Redis, Kafka, MySQL, PostgreSQL, and Linux.

---

# 🚀 What's Next?

➡️ **01-Processes-and-Threads.md**

You'll learn:

* What is a Process?
* What is a Thread?
* Process Lifecycle
* Thread Lifecycle
* Process vs Thread
* Context Switching
* Multithreading
* Inter-Process Communication (IPC)
* Real-world Examples
* Interview Questions
* Quick Revision
