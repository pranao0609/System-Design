# HTTP/2 & HTTP/3

> *"HTTP/2 and HTTP/3 are modern versions of HTTP designed to reduce latency, improve performance, and make web communication faster and more efficient."*

---

# Table of Contents

* Why HTTP Needed Improvements
* Evolution of HTTP
* HTTP/1.1 Limitations
* What is HTTP/2?
* Features of HTTP/2
* What is HTTP/3?
* HTTP/2 vs HTTP/3
* Real-World Example
* Interview Questions
* Quick Revision

---

# Why HTTP Needed Improvements

HTTP/1.1 worked well for many years, but modern websites contain:

* Hundreds of images
* CSS files
* JavaScript files
* Fonts
* Videos
* API requests

Loading all these resources using HTTP/1.1 created performance bottlenecks.

---

# Evolution of HTTP

```text
HTTP/1.0 (1996)

↓

HTTP/1.1 (1997)

↓

HTTP/2 (2015)

↓

HTTP/3 (2022)
```

Each version introduced improvements in speed and efficiency.

---

# HTTP/1.1 Limitations

### Multiple Connections

Browsers often opened several TCP connections to download resources simultaneously.

```text
Browser

├── TCP Connection 1

├── TCP Connection 2

├── TCP Connection 3

└── TCP Connection 4
```

This increased overhead.

---

### Head-of-Line Blocking

Requests on the same connection were processed sequentially.

```text
Request 1

↓

Request 2

↓

Request 3
```

If one request was delayed, the following requests had to wait.

---

### Large Headers

HTTP headers were sent in full with every request, even if they were identical.

---

# What is HTTP/2?

HTTP/2 is an improved version of HTTP/1.1 that uses **a single TCP connection** to send multiple requests simultaneously.

It is fully compatible with existing HTTP methods and status codes.

---

# Features of HTTP/2

## 1. Multiplexing

Multiple requests and responses can share one TCP connection.

```text
Single TCP Connection

├── Request A

├── Request B

├── Request C

└── Request D
```

This reduces latency and improves resource utilization.

---

## 2. Binary Protocol

HTTP/1.1 uses plain text.

HTTP/2 uses **binary frames**.

Advantages:

* Faster parsing
* Reduced errors
* More efficient communication

---

## 3. Header Compression (HPACK)

Repeated HTTP headers are compressed before transmission.

Example:

```text
Authorization

User-Agent

Cookie
```

Instead of sending the same headers repeatedly, HTTP/2 compresses them.

Result:

* Reduced bandwidth usage.
* Faster requests.

---

## 4. Server Push

The server can proactively send resources before the browser requests them.

Example:

```text
Browser Requests

index.html

↓

Server Automatically Sends

style.css

script.js

logo.png
```

This reduces additional round trips.

---

# What is HTTP/3?

HTTP/3 is the latest version of HTTP.

The biggest change is:

```text
HTTP/1.1

↓

TCP

HTTP/2

↓

TCP

HTTP/3

↓

QUIC (UDP-based)
```

Instead of TCP, HTTP/3 uses **QUIC**, which runs over UDP.

---

# Why QUIC?

TCP requires a connection setup and suffers from **Head-of-Line Blocking** at the transport layer.

QUIC addresses these issues by providing:

* Faster connection establishment.
* Independent streams.
* Better performance on unreliable networks.
* Improved mobile experience.

---

# Features of HTTP/3

## 1. Uses QUIC

QUIC combines:

* Reliable transport
* Encryption (TLS 1.3)
* Multiplexing

into a single protocol.

---

## 2. Faster Connection Setup

HTTP/3 reduces the number of round trips needed to establish a secure connection.

Result:

* Lower latency.
* Faster page loads.

---

## 3. No Transport-Level Head-of-Line Blocking

If one packet is lost, only the affected stream waits.

Other streams continue.

```text
Stream A

✔ Running

Stream B

Packet Lost

Waiting

Stream C

✔ Running
```

---

## 4. Better Mobile Performance

HTTP/3 performs well on unstable or changing networks.

Example:

Switching from:

```text
Wi-Fi

↓

4G

↓

5G
```

can happen with minimal interruption.

---

# HTTP/2 vs HTTP/3

| Feature               | HTTP/2                | HTTP/3                        |
| --------------------- | --------------------- | ----------------------------- |
| Transport Protocol    | TCP                   | QUIC (UDP)                    |
| Multiplexing          | Yes                   | Yes                           |
| Header Compression    | HPACK                 | QPACK                         |
| Encryption            | TLS                   | TLS 1.3 Integrated            |
| Connection Setup      | Slower                | Faster                        |
| Head-of-Line Blocking | Possible at TCP layer | Eliminated at transport layer |

---

# Comparison of HTTP Versions

| Feature            | HTTP/1.1 | HTTP/2 | HTTP/3           |
| ------------------ | -------- | ------ | ---------------- |
| Protocol           | Text     | Binary | Binary           |
| Multiplexing       | No       | Yes    | Yes              |
| Header Compression | No       | Yes    | Yes              |
| Server Push        | No       | Yes    | Limited/Optional |
| Transport          | TCP      | TCP    | QUIC (UDP)       |
| Performance        | Good     | Better | Best             |

---

# Real-World Example

Opening:

```text
https://www.youtube.com
```

### HTTP/1.1

```text
Browser

↓

Multiple TCP Connections

↓

Server
```

---

### HTTP/2

```text
Browser

↓

One TCP Connection

↓

Multiple Streams

↓

Server
```

---

### HTTP/3

```text
Browser

↓

QUIC Connection

↓

Independent Streams

↓

Server
```

This results in faster loading and improved reliability, especially on mobile networks.

---

# Advantages

## HTTP/2

* Faster page loading.
* Reduced latency.
* Lower bandwidth usage.
* Efficient multiplexing.

---

## HTTP/3

* Faster connection establishment.
* Better mobile performance.
* Eliminates transport-level Head-of-Line Blocking.
* Improved handling of packet loss.

---

# Quick Revision

```text
HTTP Evolution

HTTP/1.0

↓

HTTP/1.1

↓

HTTP/2

↓

HTTP/3

HTTP/2

✔ Multiplexing

✔ Binary Protocol

✔ Header Compression

✔ Server Push

HTTP/3

✔ QUIC

✔ UDP

✔ Faster Setup

✔ Better Mobile Performance

✔ No Transport-Level HOL Blocking
```

---

# Key Takeaways

* HTTP/2 and HTTP/3 improve the performance of modern web applications by reducing latency and optimizing resource transfer.
* **HTTP/2** introduces multiplexing, binary framing, header compression, and server push while continuing to use TCP.
* **HTTP/3** replaces TCP with **QUIC**, a UDP-based transport protocol that integrates TLS 1.3 and eliminates transport-level Head-of-Line Blocking.
* Both versions are backward-compatible with the HTTP request-response model, making adoption easier for existing applications.
* Understanding these improvements is important for designing high-performance web applications and scalable backend systems.

---

> **Next Topic:** `DNS.md`
