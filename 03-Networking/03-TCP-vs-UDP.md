# TCP vs UDP

> *"TCP and UDP are the two primary Transport Layer protocols in the TCP/IP model. TCP prioritizes reliability and ordered delivery, while UDP prioritizes speed and low latency."*

---

# Table of Contents

* What are TCP and UDP?
* Why Do We Need Transport Layer Protocols?
* What is TCP?
* What is UDP?
* TCP Connection Establishment
* TCP Connection Termination
* TCP vs UDP
* Reliability in TCP
* Flow Control
* Congestion Control
* Error Detection
* Use Cases
* Real-World Examples
* Advantages & Disadvantages
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What are TCP and UDP?

**TCP (Transmission Control Protocol)** and **UDP (User Datagram Protocol)** are the two most widely used protocols at the **Transport Layer** of the TCP/IP model.

Their job is to enable communication between applications running on different devices.

Examples:

* Opening a website
* Sending an email
* Streaming a video
* Playing an online game
* Making a video call

All of these use either TCP or UDP.

---

# Why Do We Need Transport Layer Protocols?

The Internet Protocol (IP) is responsible for delivering packets, but it does **not** guarantee:

* Delivery
* Order
* Error recovery
* Flow control

The Transport Layer adds these capabilities.

```text
Application
      │
      ▼
TCP / UDP
      │
      ▼
IP
      │
      ▼
Network
```

---

# What is TCP?

**TCP** is a **connection-oriented** protocol that provides **reliable** communication.

Before data is transferred, TCP establishes a connection between the sender and receiver.

Characteristics:

* Reliable
* Connection-oriented
* Ordered delivery
* Error recovery
* Flow control
* Congestion control

Example:

When downloading a PDF, every byte must arrive correctly.

TCP guarantees this.

---

# What is UDP?

**UDP** is a **connectionless** protocol.

It sends data without establishing a connection.

Characteristics:

* Fast
* Lightweight
* No retransmissions
* No ordering guarantee
* Low latency

Example:

During a live football match, receiving the latest video frame is more important than retransmitting an old lost frame.

---

# TCP Connection (Three-Way Handshake)

Before sending data, TCP establishes a connection.

```text
Client                     Server

  SYN  -------------------->

       <--------------------  SYN + ACK

  ACK  -------------------->
```

### Step 1

Client sends:

```text
SYN
```

"I want to establish a connection."

---

### Step 2

Server replies:

```text
SYN + ACK
```

"I received your request and I'm ready."

---

### Step 3

Client responds:

```text
ACK
```

"Connection established."

Now data transfer begins.

---

# TCP Connection Termination (Four-Way Handshake)

Closing a TCP connection requires four steps.

```text
Client                    Server

 FIN ---------------------->

      <--------------------- ACK

      <--------------------- FIN

 ACK ----------------------->
```

This ensures both sides finish transmitting data safely.

---

# TCP vs UDP

| Feature            | TCP                 | UDP            |
| ------------------ | ------------------- | -------------- |
| Connection         | Connection-Oriented | Connectionless |
| Reliability        | Reliable            | Unreliable     |
| Ordering           | Guaranteed          | Not Guaranteed |
| Error Recovery     | Yes                 | No             |
| Flow Control       | Yes                 | No             |
| Congestion Control | Yes                 | No             |
| Speed              | Slower              | Faster         |
| Header Size        | 20–60 Bytes         | 8 Bytes        |
| Overhead           | High                | Low            |

---

# Reliability in TCP

TCP guarantees reliable communication using:

* Acknowledgments (ACKs)
* Sequence Numbers
* Retransmissions
* Checksums

Example:

```text
Packets

1

2

3

4

Packet 3 Lost

↓

Retransmit Packet 3

↓

Receive 4
```

The receiver eventually receives all packets in the correct order.

---

# Flow Control

A fast sender can overwhelm a slow receiver.

TCP prevents this using the **Sliding Window Protocol**.

```text
Sender

[1][2][3][4]

↓

Receiver Window

Can Accept Only 2 Packets
```

The sender transmits only as much data as the receiver can handle.

Benefits:

* Prevents buffer overflow.
* Improves efficiency.

---

# Congestion Control

Network congestion occurs when too many packets enter the network.

TCP adjusts its sending rate dynamically.

Common algorithms:

* Slow Start
* Congestion Avoidance
* Fast Retransmit
* Fast Recovery

Goal:

Avoid overloading the network.

---

# Error Detection

Both TCP and UDP include a **Checksum**.

```text
Sender

↓

Checksum Added

↓

Receiver

↓

Verify Checksum
```

If corruption is detected:

* TCP requests retransmission.
* UDP discards the packet.

---

# Ports

TCP and UDP both use **Port Numbers** to identify applications.

Examples:

| Protocol | Default Port |
| -------- | -----------: |
| HTTP     |           80 |
| HTTPS    |          443 |
| FTP      |           21 |
| SSH      |           22 |
| DNS      |           53 |
| SMTP     |           25 |

Example:

```text
IP Address

192.168.1.10

Port

443

↓

HTTPS Service
```

An IP address identifies the device, while the port identifies the application on that device.

---

# Use Cases

## TCP Applications

Use TCP when:

* Data must arrive correctly.
* Order matters.
* Reliability is essential.

Examples:

* Web Browsing (HTTP/HTTPS)
* Banking Applications
* Email
* Cloud Storage
* File Downloads
* REST APIs
* Database Connections

---

## UDP Applications

Use UDP when:

* Low latency is more important than perfect reliability.

Examples:

* Online Gaming
* Video Streaming
* Voice Calls (VoIP)
* Live Broadcasting
* DNS Queries
* IoT Devices

---

# Real-World Examples

## Downloading a File

```text
Browser

↓

TCP

↓

Internet

↓

Server
```

Every byte must arrive correctly.

TCP is used.

---

## Video Call

```text
Camera

↓

UDP

↓

Internet

↓

Receiver
```

If one video frame is lost,

the next frame replaces it.

Retransmitting the lost frame would only increase latency.

---

## Online Multiplayer Game

Player movement updates are transmitted using UDP because speed is more important than guaranteed delivery.

---

# Advantages & Disadvantages

## TCP

### Advantages

* Reliable
* Ordered Delivery
* Error Recovery
* Flow Control
* Congestion Control

### Disadvantages

* Slower
* Higher Overhead
* More Complex

---

## UDP

### Advantages

* Very Fast
* Low Latency
* Simple
* Small Header
* Low Overhead

### Disadvantages

* No Reliability
* No Ordering
* No Retransmission
* Packet Loss Possible

---

# When to Choose TCP or UDP

| Scenario        | Protocol        |
| --------------- | --------------- |
| Website         | TCP             |
| REST API        | TCP             |
| Banking         | TCP             |
| Email           | TCP             |
| File Transfer   | TCP             |
| Video Streaming | UDP             |
| Voice Call      | UDP             |
| Online Gaming   | UDP             |
| DNS Query       | UDP (primarily) |

---

# Quick Revision

```text
Transport Layer

├── TCP
│     ├── Reliable
│     ├── Connection-Oriented
│     ├── Ordered Delivery
│     ├── ACK
│     ├── Retransmission
│     └── Flow Control
│
└── UDP
      ├── Fast
      ├── Connectionless
      ├── Low Latency
      ├── No ACK
      ├── No Ordering
      └── No Retransmission
```

### Memory Trick

```text
TCP

T = Trustworthy

C = Connection

P = Perfect Delivery

UDP

U = Ultra Fast

D = Doesn't Guarantee Delivery

P = Packets Only
```

---

# Key Takeaways

* TCP and UDP are the two primary Transport Layer protocols in the TCP/IP model.
* **TCP** provides reliable, ordered, and connection-oriented communication using acknowledgments, retransmissions, flow control, and congestion control.
* **UDP** is connectionless, lightweight, and optimized for low latency, making it suitable for real-time applications.
* Choose **TCP** when correctness is more important than speed.
* Choose **UDP** when speed and low latency are more important than guaranteed delivery.
* Understanding the trade-offs between TCP and UDP is fundamental for designing scalable web applications, APIs, streaming platforms, and distributed systems.

---

> **Next Topic:** `04-HTTP-and-HTTPS.md`
