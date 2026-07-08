# Layer 4 (L4) Load Balancing

> *"Layer 4 (L4) Load Balancing distributes network traffic based on transport-layer information such as IP addresses and TCP/UDP ports, without inspecting the application data."*

---

# Table of Contents

* What is Layer 4 Load Balancing?
* Why Do We Need L4 Load Balancing?
* How L4 Load Balancing Works
* OSI Layer 4
* Load Balancing Algorithms
* Advantages
* Disadvantages
* L4 vs L7 Load Balancing
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Layer 4 Load Balancing?

**Layer 4 (L4) Load Balancing** operates at the **Transport Layer** of the OSI model.

It makes routing decisions based on:

* Source IP Address
* Destination IP Address
* TCP Port
* UDP Port

It **does not inspect HTTP requests, URLs, headers, or cookies**.

---

# Why Do We Need L4 Load Balancing?

Imagine thousands of users accessing a web application.

```text id="l41"
Users

↓

Single Server

↓

Overloaded
```

By placing an L4 Load Balancer in front:

```text id="l42"
Users

↓

L4 Load Balancer

↓

Server A

Server B

Server C
```

Traffic is distributed efficiently across servers.

---

# How L4 Load Balancing Works

The load balancer receives a network connection.

It checks:

* Client IP
* Server IP
* Port Number

Then forwards the connection to a backend server.

```text id="l43"
Client

↓

TCP Connection

↓

L4 Load Balancer

↓

Backend Server
```

The load balancer does **not** analyze the request content.

---

# OSI Layer 4

The OSI model consists of seven layers.

```text id="l44"
Application (7)

Presentation (6)

Session (5)

Transport (4)  ← L4

Network (3)

Data Link (2)

Physical (1)
```

L4 Load Balancers operate at the **Transport Layer**.

---

# Load Balancing Algorithms

Common algorithms include:

### Round Robin

Requests are distributed one by one.

```text id="l45"
Request 1 → Server A

Request 2 → Server B

Request 3 → Server C

Request 4 → Server A
```

---

### Least Connections

The server with the fewest active connections receives the next request.

Useful when request durations vary.

---

### IP Hash

The client's IP address determines the backend server.

This helps maintain session affinity.

---

### Weighted Round Robin

Servers with greater capacity receive a larger share of requests.

Example:

```text id="l46"
Server A

Weight = 3

Server B

Weight = 1
```

Server A receives more traffic.

---

# Advantages

* Extremely fast.
* Low processing overhead.
* Supports both TCP and UDP.
* High throughput.
* Suitable for non-HTTP protocols.

---

# Disadvantages

* Cannot inspect application-layer data.
* Cannot route based on URL or HTTP headers.
* Limited flexibility compared to L7 load balancing.
* Cannot perform content-based routing.

---

# L4 vs L7 Load Balancing

| Layer 4                     | Layer 7                       |
| --------------------------- | ----------------------------- |
| Operates at Transport Layer | Operates at Application Layer |
| Uses IP & Port              | Uses URL, Headers, Cookies    |
| Faster                      | More intelligent routing      |
| Lower CPU usage             | Higher processing overhead    |
| No content inspection       | Full HTTP awareness           |

---

# Real-World Examples

## Database Load Balancing

Distributes TCP connections across database replicas.

---

## Game Servers

Balances UDP traffic for multiplayer games.

---

## DNS Servers

Routes DNS requests using UDP.

---

## Streaming Platforms

Balances TCP connections for media delivery.

---

# Popular L4 Load Balancers

* HAProxy (TCP Mode)
* NGINX Stream Module
* AWS Network Load Balancer (NLB)
* Google Cloud Network Load Balancer
* F5 BIG-IP

---

# When to Use L4 Load Balancing

Use L4 when:

* High performance is required.
* Traffic is TCP or UDP based.
* Content inspection is unnecessary.
* Low latency is important.
* Network-level routing is sufficient.

---

# Quick Revision

```text id="l47"
Layer 4 Load Balancing

↓

Transport Layer

↓

Uses

✔ IP Address

✔ TCP Port

✔ UDP Port

Algorithms

✔ Round Robin

✔ Least Connections

✔ IP Hash

✔ Weighted Round Robin

Benefits

✔ Fast

✔ High Throughput

✔ Low Latency
```

---

# Key Takeaways

* **Layer 4 Load Balancing** operates at the **Transport Layer** of the OSI model.
* It routes traffic using **IP addresses and TCP/UDP ports**, without inspecting application data.
* L4 load balancing offers **high performance, low latency, and support for multiple protocols**.
* It is commonly used for **databases, game servers, DNS services, and other TCP/UDP applications**.
* When application-aware routing is required (based on URLs, headers, or cookies), **Layer 7 Load Balancing** is a better choice.

---

> **Next Topic:** `04-L7-Load-Balancing.md`
