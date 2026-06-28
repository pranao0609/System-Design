# Processes and Threads

> *"A process is an independent program in execution, while a thread is the smallest unit of execution within a process. Modern applications rely on multiple threads to improve responsiveness and efficiently utilize CPU resources."*

---

# Table of Contents

* What is a Process?
* Process Lifecycle
* Process Memory Layout
* Process Control Block (PCB)
* What is a Thread?
* Thread Lifecycle
* Types of Threads
* Process vs Thread
* Context Switching
* Multitasking, Multithreading & Multiprocessing
* Inter-Process Communication (IPC)
* Thread Synchronization (Overview)
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is a Process?

A **Process** is a program that is currently being executed.

When you open an application such as Chrome, VS Code, Spotify, or WhatsApp, the operating system creates a new process.

Each process has its own:

* Memory
* CPU registers
* Program Counter
* Process ID (PID)
* File Descriptors
* Stack
* Heap

A process is isolated from other processes, which improves stability and security.

---

## Examples

Running the following applications:

```text
Google Chrome
Visual Studio Code
Spotify
Discord
```

creates four independent processes.

If Spotify crashes, Chrome continues running because they have separate memory spaces.

---

# Process Lifecycle

A process moves through several states during execution.

```text
                 +-------+
                 |  New  |
                 +-------+
                     │
                     ▼
               +-----------+
               |  Ready    |
               +-----------+
                     │
                     ▼
               +-----------+
               | Running   |
               +-----------+
                │    │
      Waiting   │    │ Time Slice Ends
                ▼    ▼
           +---------+
           | Waiting |
           +---------+
                │
                ▼
             Running
                │
                ▼
           +-----------+
           |Terminated |
           +-----------+
```

### States

### 1. New

The process has been created but has not yet started execution.

---

### 2. Ready

The process is waiting for CPU allocation.

---

### 3. Running

The CPU is currently executing the process.

---

### 4. Waiting (Blocked)

The process waits for:

* Disk I/O
* Network Response
* User Input
* File Access

---

### 5. Terminated

Execution has completed.

---

# Process Memory Layout

Each process has its own virtual memory space.

```text
+----------------------+
|       Stack          |
| Local Variables      |
| Function Calls       |
+----------------------+

|        Heap          |
| Dynamic Allocation   |
+----------------------+

| Initialized Data     |
+----------------------+

| Uninitialized Data   |
| (.bss)               |
+----------------------+

| Code (.text)         |
| Executable Code      |
+----------------------+
```

---

## Code Segment

Contains executable instructions.

Example:

```cpp
int main() {
    return 0;
}
```

---

## Data Segment

Stores initialized global and static variables.

```cpp
int x = 10;
```

---

## BSS Segment

Stores uninitialized global variables.

```cpp
int count;
```

---

## Heap

Used for dynamic memory allocation.

Example:

```cpp
new Student();
malloc();
```

Characteristics:

* Grows upward.
* Managed by the programmer (C/C++) or runtime (Java, Python).

---

## Stack

Stores:

* Function calls
* Local variables
* Return addresses

Characteristics:

* Grows downward.
* Automatically managed.

---

# Process Control Block (PCB)

The operating system stores information about every process inside a **Process Control Block (PCB)**.

```text
PCB

├── Process ID
├── Process State
├── CPU Registers
├── Program Counter
├── Scheduling Information
├── Memory Information
├── Open Files
└── Priority
```

The scheduler uses the PCB during context switching.

---

# What is a Thread?

A **Thread** is the smallest unit of execution inside a process.

A process can have:

* One thread (Single-threaded)
* Multiple threads (Multithreaded)

Threads within the same process share:

* Heap
* Code
* Global Variables
* Open Files

Each thread has its own:

* Stack
* Registers
* Program Counter

---

## Example

Google Chrome

```text
Chrome Process

│
├── UI Thread
├── Rendering Thread
├── Network Thread
├── JavaScript Thread
└── GPU Thread
```

All these threads belong to one process and work together.

---

# Thread Lifecycle

```text
New
 │
 ▼
Ready
 │
 ▼
Running
 │
 ▼
Blocked
 │
 ▼
Running
 │
 ▼
Terminated
```

The lifecycle is similar to a process, but threads share process resources.

---

# Types of Threads

## User-Level Threads (ULT)

Managed by the application.

Advantages:

* Fast creation
* Fast switching

Disadvantages:

* Blocking system calls can block the entire process.

---

## Kernel-Level Threads (KLT)

Managed by the operating system.

Advantages:

* True parallelism
* Better scheduling

Disadvantages:

* Higher context-switching overhead.

---

# Process vs Thread

| Feature        | Process                          | Thread                     |
| -------------- | -------------------------------- | -------------------------- |
| Definition     | Independent program in execution | Smallest unit of execution |
| Memory         | Separate                         | Shared within process      |
| Address Space  | Separate                         | Shared                     |
| Communication  | IPC                              | Shared Memory              |
| Creation Cost  | High                             | Low                        |
| Context Switch | Expensive                        | Faster                     |
| Isolation      | High                             | Low                        |
| Failure Impact | Usually isolated                 | Can affect entire process  |

---

# Context Switching

A CPU can execute only one thread per core at a time.

When switching between tasks, the operating system performs a **context switch**.

```text
CPU

Process A
     │
 Save State
     │
Load State
     │
Process B
```

During a context switch, the OS saves:

* CPU Registers
* Program Counter
* Stack Pointer
* Process State

and restores the state of the next scheduled process or thread.

### Context Switching Overhead

Context switching consumes CPU time because no useful work is done during the switch.

Frequent switching can reduce overall system performance.

---

# Multitasking vs Multithreading vs Multiprocessing

## Multitasking

Running multiple programs concurrently.

Example:

```text
Chrome
VS Code
Spotify
Discord
```

---

## Multithreading

Running multiple threads within the same process.

Example:

```text
Browser

UI Thread
Download Thread
Rendering Thread
```

---

## Multiprocessing

Using multiple processes simultaneously.

Example:

```text
Python Process
Database Process
Redis Process
```

---

# Inter-Process Communication (IPC)

Processes have separate memory spaces, so they require special mechanisms to communicate.

Common IPC methods:

* Pipes
* Named Pipes (FIFO)
* Shared Memory
* Message Queues
* Sockets
* Signals
* Memory-Mapped Files

Example:

```text
Process A
     │
 Socket
     │
Process B
```

IPC is widely used in distributed systems and microservices.

---

# Thread Synchronization (Overview)

Since threads share memory, they may try to access the same data simultaneously.

Example:

```cpp
counter++;
```

If two threads execute this statement at the same time, the result may be incorrect.

This issue is called a **Race Condition**.

Synchronization mechanisms such as mutexes, semaphores, and locks are used to ensure correct execution.

> This topic is covered in detail in the **Synchronization** chapter.

---

# Real-World Examples

## Web Server

A web server receives thousands of client requests.

```text
Clients
   │
   ▼
Web Server

├── Thread 1
├── Thread 2
├── Thread 3
└── Thread Pool
```

Each thread processes one or more client requests concurrently.

---

## Database Server

A database creates multiple worker threads to execute queries in parallel while sharing the same data structures.

---

## Modern Browser

A browser separates different responsibilities into threads:

* UI Thread
* Rendering Thread
* Network Thread
* JavaScript Engine
* GPU Thread

This keeps the interface responsive while background tasks continue.

---

# Interview Questions

### Basic

* What is a process?
* What is a thread?
* Difference between process and thread?
* What is context switching?
* Why are threads lightweight?

### Intermediate

* Explain process memory layout.
* What is a PCB?
* How do processes communicate?
* What is IPC?
* What is thread safety?

### Advanced

* Why is process context switching slower than thread context switching?
* Why are thread pools used in web servers?
* How does multithreading improve scalability?
* When would you prefer multiprocessing over multithreading?

---

# Quick Revision

```text
Process
│
├── Independent Execution
├── Separate Memory
├── High Isolation
├── Expensive Creation
└── IPC Required

Thread
│
├── Part of Process
├── Shared Memory
├── Own Stack
├── Lightweight
└── Fast Switching

Memory Layout
│
├── Code
├── Data
├── BSS
├── Heap
└── Stack

IPC
│
├── Pipes
├── Shared Memory
├── Message Queue
├── Socket
└── Signals
```

---

# Key Takeaways

* A **process** is an independent program in execution with its own memory space.
* A **thread** is the smallest unit of execution within a process and shares most resources with other threads in the same process.
* Threads are more lightweight than processes, making them suitable for handling concurrent tasks.
* Context switching allows the CPU to switch between processes or threads but introduces overhead.
* Processes communicate using **IPC**, while threads communicate through shared memory.
* Understanding processes and threads is essential for building scalable servers, databases, operating systems, and distributed applications.

---

> **Next Topic:** `02-Concurrency.md`
