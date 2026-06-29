# OSI Model (Open Systems Interconnection Model)

> *"The OSI Model is a conceptual framework that standardizes how data is transmitted between devices over a network by dividing communication into seven logical layers."*

---

# Table of Contents

* What is the OSI Model?
* Why was the OSI Model Created?
* Why Do We Need Layers?
* The Seven Layers of the OSI Model
* Data Flow Through the OSI Model
* Encapsulation & Decapsulation
* Protocol Data Units (PDUs)
* Devices at Each Layer
* OSI vs TCP/IP
* Real-World Example
* Mnemonics
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is the OSI Model?

The **OSI (Open Systems Interconnection) Model** is a **7-layer conceptual model** developed by the **International Organization for Standardization (ISO)**.

It provides a standardized way to understand how different networking systems communicate with one another.

Instead of treating communication as one large process, the OSI Model divides it into **seven independent layers**, where each layer has a specific responsibility.

Think of it as a pipeline where each layer performs one task and passes the data to the next layer.

---

# Why was the OSI Model Created?

Before the OSI Model, networking technologies were vendor-specific and often incompatible.

Problems included:

* Different communication standards
* Difficult interoperability
* Complex troubleshooting
* Vendor lock-in

The OSI Model solved these issues by defining standard responsibilities for each layer.

Benefits:

* Standardization
* Easier troubleshooting
* Modular design
* Vendor independence
* Better understanding of network communication

---

# Why Do We Need Layers?

Imagine sending a package through a courier service.

Different people perform different jobs:

```text
You Pack the Item
        │
Courier Collects Package
        │
Transportation
        │
Sorting Center
        │
Delivery Vehicle
        │
Recipient Receives Package
```

Each person has a specific responsibility.

Similarly, the OSI Model separates networking into layers so each layer focuses on one task.

Advantages:

* Simpler implementation
* Easier maintenance
* Independent upgrades
* Better debugging

---

# The Seven Layers

```text
+---------------------------+
| 7. Application            |
+---------------------------+
| 6. Presentation           |
+---------------------------+
| 5. Session                |
+---------------------------+
| 4. Transport              |
+---------------------------+
| 3. Network                |
+---------------------------+
| 2. Data Link              |
+---------------------------+
| 1. Physical               |
+---------------------------+
```

Data travels **down** these layers at the sender and **up** these layers at the receiver.

---

# Layer 7 – Application Layer

The Application Layer is the closest layer to the user.

It provides network services to applications.

Examples:

* Web Browsers
* Email Clients
* Messaging Apps
* FTP Clients

Common Protocols:

* HTTP
* HTTPS
* FTP
* SMTP
* IMAP
* DNS

Responsibilities:

* User interaction
* Network services
* File transfer
* Email
* Web communication

Example:

Typing:

```text
https://www.google.com
```

starts at the Application Layer.

---

# Layer 6 – Presentation Layer

The Presentation Layer ensures that data is presented in a format understandable by both sender and receiver.

Responsibilities:

* Data Formatting
* Encryption
* Decryption
* Compression
* Decompression
* Character Encoding

Examples:

* TLS/SSL Encryption
* JPEG
* PNG
* MP3
* UTF-8

Think of this layer as a translator.

---

# Layer 5 – Session Layer

The Session Layer manages communication sessions between devices.

Responsibilities:

* Session Establishment
* Session Maintenance
* Session Termination
* Synchronization

Examples:

* Video Calls
* Database Connections
* Remote Login Sessions

Without this layer, every request would require creating a completely new communication session.

---

# Layer 4 – Transport Layer

The Transport Layer provides **end-to-end communication**.

Responsibilities:

* Reliability
* Error Recovery
* Flow Control
* Segmentation
* Reassembly

Protocols:

* TCP
* UDP

TCP provides:

* Reliable delivery
* Ordered delivery
* Error checking

UDP provides:

* Faster communication
* Lower overhead
* No delivery guarantees

Applications:

* Video Streaming
* Gaming
* DNS Queries

---

# Layer 3 – Network Layer

Responsible for routing packets between networks.

Responsibilities:

* Logical Addressing
* Routing
* Path Selection

Protocols:

* IP
* ICMP
* OSPF
* BGP

Device:

```text
Router
```

Example:

Finding the shortest path between your laptop and Google's servers.

---

# Layer 2 – Data Link Layer

Provides communication between devices on the same local network.

Responsibilities:

* MAC Addressing
* Error Detection
* Framing
* Media Access Control

Protocols:

* Ethernet
* Wi-Fi (802.11)
* PPP

Device:

```text
Switch
```

---

# Layer 1 – Physical Layer

The lowest layer.

Responsible for transmitting raw bits over physical media.

Examples:

* Electrical Signals
* Optical Signals
* Radio Waves

Hardware:

* Ethernet Cable
* Fiber Optic Cable
* Wi-Fi Radio
* Connectors
* Hubs

Data Unit:

```text
Bits
```

---

# Summary of All Layers

| Layer | Name         | Main Responsibility     | Examples     |
| ----- | ------------ | ----------------------- | ------------ |
| 7     | Application  | User Services           | HTTP, FTP    |
| 6     | Presentation | Encryption, Compression | TLS, JPEG    |
| 5     | Session      | Session Management      | RPC, NetBIOS |
| 4     | Transport    | Reliable Delivery       | TCP, UDP     |
| 3     | Network      | Routing                 | IP           |
| 2     | Data Link    | MAC Addressing          | Ethernet     |
| 1     | Physical     | Bit Transmission        | Cable, Fiber |

---

# Data Flow Through the OSI Model

Suppose you open YouTube.

```text
Browser
      │
Application
      │
Presentation
      │
Session
      │
Transport
      │
Network
      │
Data Link
      │
Physical
      │
──────── Internet ────────
      │
Physical
      │
Data Link
      │
Network
      │
Transport
      │
Session
      │
Presentation
      │
Application
      │
YouTube Server
```

---

# Encapsulation

As data moves **down** the OSI stack, each layer adds its own header.

```text
Application Data
        │
        ▼
TCP Header
        │
        ▼
IP Header
        │
        ▼
Ethernet Header
        │
        ▼
Bits
```

This process is called **Encapsulation**.

---

# Decapsulation

At the receiving end, each layer removes its corresponding header.

```text
Bits

↓

Ethernet Header Removed

↓

IP Header Removed

↓

TCP Header Removed

↓

Original Data
```

---

# Protocol Data Units (PDUs)

Each layer has its own name for the data.

| Layer        | PDU                            |
| ------------ | ------------------------------ |
| Application  | Data                           |
| Presentation | Data                           |
| Session      | Data                           |
| Transport    | Segment (TCP) / Datagram (UDP) |
| Network      | Packet                         |
| Data Link    | Frame                          |
| Physical     | Bits                           |

---

# Devices at Each Layer

| Layer        | Device               |
| ------------ | -------------------- |
| Application  | Gateway, Proxy       |
| Presentation | Gateway              |
| Session      | Gateway              |
| Transport    | Firewall             |
| Network      | Router               |
| Data Link    | Switch, Bridge       |
| Physical     | Hub, Repeater, Cable |

---

# OSI vs TCP/IP

| OSI Model          | TCP/IP Model             |
| ------------------ | ------------------------ |
| 7 Layers           | 4 Layers                 |
| Conceptual Model   | Practical Implementation |
| Developed by ISO   | Developed by DARPA       |
| Mainly Educational | Used on the Internet     |

Mapping:

```text
OSI                    TCP/IP

Application ┐
Presentation│
Session     ┘ → Application

Transport → Transport

Network → Internet

Data Link ┐
Physical ┘ → Network Access
```

---

# Real-World Example

Suppose you send a WhatsApp message.

```text
Application

↓

Encrypt Message

↓

Create Session

↓

TCP

↓

IP

↓

Wi-Fi Frame

↓

Bits

↓

Internet

↓

Receiver
```

Each layer performs its specific responsibility before passing the data to the next.

---

# Mnemonics

Top to Bottom (7 → 1)

```text
All People Seem To Need Data Processing
```

* Application
* Presentation
* Session
* Transport
* Network
* Data Link
* Physical

Bottom to Top (1 → 7)

```text
Please Do Not Throw Sausage Pizza Away
```

* Physical
* Data Link
* Network
* Transport
* Session
* Presentation
* Application

---

# Quick Revision

```text
OSI Model

7 → Application
6 → Presentation
5 → Session
4 → Transport (TCP, UDP)
3 → Network (IP)
2 → Data Link (Ethernet)
1 → Physical (Bits)

PDU

Application → Data
Transport → Segment
Network → Packet
Data Link → Frame
Physical → Bits

Devices

Router → Layer 3
Switch → Layer 2
Hub → Layer 1
```

---

# Key Takeaways

* The **OSI Model** is a conceptual framework that divides network communication into seven layers.
* Each layer has a specific responsibility, making networking modular and easier to understand.
* Data is **encapsulated** as it moves down the stack and **decapsulated** as it moves up at the receiver.
* The Transport Layer provides end-to-end communication, while the Network Layer handles routing.
* Although the Internet uses the TCP/IP model in practice, the OSI model remains the standard framework for learning, troubleshooting, and designing networked systems.

---

> **Next Topic:** `02-TCP-IP-Model.md`
