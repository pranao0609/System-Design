# CPU Scheduling

> *"CPU Scheduling is the process by which the operating system decides which process or thread gets the CPU next. Efficient scheduling improves CPU utilization, responsiveness, and overall system performance."*

---

# Table of Contents

* What is CPU Scheduling?
* Why is CPU Scheduling Important?
* Process States
* Scheduler Types
* Scheduling Criteria
* Types of Scheduling Algorithms
* FCFS
* Shortest Job First (SJF)
* Shortest Remaining Time First (SRTF)
* Priority Scheduling
* Round Robin (RR)
* Multilevel Queue Scheduling
* Multilevel Feedback Queue (MLFQ)
* Context Switching
* Real-World Examples
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is CPU Scheduling?

A computer can execute **many processes**, but a CPU core can execute **only one process or thread at a time**.

The operating system continuously decides:

> **"Which process should use the CPU next?"**

This decision-making process is called **CPU Scheduling**.

Its objectives are to:

* Maximize CPU utilization
* Minimize waiting time
* Improve response time
* Increase throughput
* Ensure fairness among processes

---

# Why is CPU Scheduling Important?

Imagine running:

* Google Chrome
* Visual Studio Code
* Spotify
* Docker
* Terminal

All of these programs compete for CPU time.

Without scheduling:

* Some processes may never execute.
* Interactive applications become unresponsive.
* CPU resources may be wasted.

A scheduler ensures every process gets a fair opportunity to execute while optimizing overall system performance.

---

# Process States

A process transitions through several states during execution.

```text
                  +-------+
                  |  New  |
                  +-------+
                      │
                      ▼
                +-----------+
                |   Ready   |
                +-----------+
                      │
            CPU Assigned
                      ▼
                +-----------+
                | Running   |
                +-----------+
                 │        │
      I/O Wait   │        │ Time Slice Over
                 ▼        ▼
            +-----------+
            | Waiting  |
            +-----------+
                 │
        I/O Complete
                 ▼
               Ready
                 │
                 ▼
             Running
                 │
                 ▼
           +-------------+
           | Terminated  |
           +-------------+
```

Only processes in the **Ready Queue** compete for CPU scheduling.

---

# Scheduler Types

Operating systems use different schedulers for different responsibilities.

```text
Operating System

│

├── Long-Term Scheduler

├── Short-Term Scheduler

└── Medium-Term Scheduler
```

---

## 1. Long-Term Scheduler

Determines:

* Which jobs enter memory.
* Degree of multiprogramming.

Runs less frequently.

---

## 2. Short-Term Scheduler

Determines:

* Which ready process gets the CPU.

Runs extremely frequently (milliseconds).

This is the scheduler most CPU scheduling algorithms refer to.

---

## 3. Medium-Term Scheduler

Temporarily suspends processes by swapping them out of memory.

Useful when RAM is limited.

---

# Scheduling Criteria

A good scheduling algorithm aims to optimize several metrics.

| Metric          | Goal     |
| --------------- | -------- |
| CPU Utilization | Maximize |
| Throughput      | Maximize |
| Turnaround Time | Minimize |
| Waiting Time    | Minimize |
| Response Time   | Minimize |
| Fairness        | Maximize |

---

# Types of Scheduling

Scheduling algorithms are broadly divided into:

## Non-Preemptive

Once a process starts executing, it continues until completion or blocking.

Examples:

* FCFS
* Non-Preemptive SJF
* Non-Preemptive Priority

---

## Preemptive

The operating system can interrupt a running process and assign the CPU to another process.

Examples:

* Round Robin
* SRTF
* Preemptive Priority
* MLFQ

Preemptive scheduling improves responsiveness for interactive systems.

---

# First Come First Serve (FCFS)

Processes execute in the order they arrive.

```text
P1 → P2 → P3 → P4
```

Advantages:

* Simple
* Easy to implement

Disadvantages:

* Convoy Effect
* Long waiting times
* Poor responsiveness

Suitable for:

* Batch systems

---

# Shortest Job First (SJF)

The process with the smallest CPU burst executes first.

```text
Burst Times

P1 = 20

P2 = 5

P3 = 8

Execution

P2 → P3 → P1
```

Advantages:

* Minimum average waiting time.

Disadvantages:

* Burst time is difficult to predict.
* Long jobs may starve.

---

# Shortest Remaining Time First (SRTF)

Preemptive version of SJF.

If a new process arrives with a shorter remaining execution time, it preempts the currently running process.

Advantages:

* Better response time than SJF.

Disadvantages:

* Frequent context switching.
* Possible starvation.

---

# Priority Scheduling

Each process is assigned a priority.

Higher-priority processes execute first.

```text
Priority

P1 = 1

P2 = 5

P3 = 3

Execution

P1 → P3 → P2
```

Advantages:

* Supports critical tasks.

Disadvantages:

* Low-priority processes may starve.

Solution:

**Aging** increases the priority of waiting processes over time.

---

# Round Robin (RR)

Each process receives a fixed **Time Quantum**.

Example:

```text
Time Quantum = 4 ms

P1

P2

P3

P4

↓

P1

P2

P3

P4
```

If a process does not finish within its time slice, it moves to the end of the ready queue.

Advantages:

* Fair scheduling.
* Excellent responsiveness.
* Widely used in interactive operating systems.

Disadvantages:

* Too small a quantum → many context switches.
* Too large a quantum → behaves like FCFS.

---

# Multilevel Queue Scheduling

Processes are placed into different queues based on type.

Example:

```text
High Priority

System Processes

↓

Interactive Processes

↓

Batch Processes
```

Each queue has its own scheduling policy.

Disadvantages:

* Processes cannot move between queues.

---

# Multilevel Feedback Queue (MLFQ)

Improves Multilevel Queue Scheduling by allowing processes to move between queues.

```text
Queue 1

Highest Priority

↓

Queue 2

↓

Queue 3

↓

Queue 4
```

Short interactive jobs stay near the top.

Long-running CPU-intensive jobs gradually move to lower-priority queues.

Advantages:

* Excellent responsiveness.
* Prevents starvation.
* Used by many modern operating systems.

---

# Context Switching

When the CPU changes from one process to another:

```text
Running Process

↓

Save CPU Registers

↓

Load Next Process

↓

Resume Execution
```

This operation is called **Context Switching**.

Context switching consumes CPU time but performs no useful application work.

Excessive context switching reduces system performance.

---

# Comparison of Scheduling Algorithms

| Algorithm   | Preemptive | Advantages                  | Disadvantages                  |
| ----------- | ---------- | --------------------------- | ------------------------------ |
| FCFS        | No         | Simple                      | Poor response time             |
| SJF         | No         | Lowest average waiting time | Starvation                     |
| SRTF        | Yes        | Better response time        | Frequent context switching     |
| Priority    | Both       | Supports critical tasks     | Starvation                     |
| Round Robin | Yes        | Fair and responsive         | Quantum selection is important |
| MLFQ        | Yes        | Highly adaptive             | Complex implementation         |

---

# Real-World Examples

## Desktop Operating Systems

Windows, Linux, and macOS primarily use preemptive scheduling with priority-based and feedback mechanisms.

---

## Web Servers

Worker threads receive CPU time based on the operating system scheduler.

---

## Mobile Operating Systems

Android and iOS prioritize UI threads to keep the interface responsive.

---

## Databases

Database worker threads compete for CPU resources while processing SQL queries.

Efficient scheduling improves throughput and query latency.

---

# Best Practices

* Use Round Robin for interactive systems.
* Prioritize short tasks for better responsiveness.
* Prevent starvation using aging.
* Minimize unnecessary context switching.
* Choose scheduling policies based on workload characteristics.

---

# Interview Questions

### Basic

* What is CPU Scheduling?
* Why is scheduling required?
* Difference between preemptive and non-preemptive scheduling?
* What is context switching?
* What is a time quantum?

### Intermediate

* Explain FCFS.
* Explain SJF.
* Explain Round Robin.
* What is starvation?
* What is aging?

### Advanced

* Why is MLFQ used in modern operating systems?
* Why isn't SJF commonly implemented exactly as described?
* How does Linux schedule processes?
* How does CPU scheduling impact web servers?
* How does context switching affect performance?

---

# Quick Revision

```text
CPU Scheduling
│
├── Long-Term Scheduler
├── Short-Term Scheduler
├── Medium-Term Scheduler
│
Algorithms
│
├── FCFS
├── SJF
├── SRTF
├── Priority
├── Round Robin
├── MLFQ
│
Goals
│
├── High CPU Utilization
├── Low Waiting Time
├── Low Response Time
├── High Throughput
└── Fairness
```

---

# Key Takeaways

* CPU Scheduling determines which process or thread gets CPU time next.
* Scheduling aims to maximize CPU utilization while minimizing waiting and response times.
* **FCFS** is simple but can suffer from the convoy effect.
* **SJF** minimizes average waiting time but may cause starvation.
* **Round Robin** is widely used for interactive systems due to its fairness.
* **MLFQ** combines multiple scheduling strategies and is used in many modern operating systems.
* Efficient scheduling is fundamental to operating systems, web servers, databases, and distributed systems.

---

> **Next Topic:** `06-Deadlocks.md`
