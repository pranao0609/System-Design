# gRPC (Google Remote Procedure Call)

> *"gRPC is a high-performance Remote Procedure Call (RPC) framework developed by Google that enables efficient communication between distributed services using HTTP/2 and Protocol Buffers."*

---

# Table of Contents

* What is gRPC?
* Why Do We Need gRPC?
* How gRPC Works
* Protocol Buffers (Protobuf)
* Types of gRPC Communication
* gRPC vs REST
* Advantages
* Limitations
* Real-World Example
* Interview Questions
* Quick Revision

---

# What is gRPC?

**gRPC (Google Remote Procedure Call)** is an open-source framework that allows one application to call a function on another application as if it were a local function.

Instead of exchanging JSON over HTTP like REST APIs, gRPC uses:

* **HTTP/2** for communication
* **Protocol Buffers (Protobuf)** for data serialization

This makes it faster and more efficient.

---

# Why Do We Need gRPC?

In a microservices architecture, multiple services communicate with each other.

Example:

```text id="grpc1"
User Service

↓

Order Service

↓

Payment Service

↓

Inventory Service
```

Using JSON-based REST APIs for every request adds overhead.

gRPC provides:

* Faster communication
* Smaller messages
* Lower latency
* Efficient streaming

---

# How gRPC Works

A client calls a method on a remote server.

```text id="grpc2"
Client

↓

gRPC Request

↓

Server

↓

Execute Method

↓

gRPC Response
```

To the client, it feels like calling a local function.

---

# Protocol Buffers (Protobuf)

gRPC uses **Protocol Buffers (Protobuf)** instead of JSON.

Example:

```proto id="grpc3"
message User {
  int32 id = 1;
  string name = 2;
}
```

Advantages:

* Compact binary format
* Faster serialization
* Smaller message size
* Strongly typed

---

# gRPC Communication Flow

```text id="grpc4"
Client

↓

Serialize (Protobuf)

↓

HTTP/2

↓

Server

↓

Deserialize

↓

Process Request

↓

Serialize Response

↓

Client
```

---

# Types of gRPC Communication

## 1. Unary RPC

One request → One response.

```text id="grpc5"
Client

↓

Request

↓

Server

↓

Response
```

Example:

Get User Details.

---

## 2. Server Streaming RPC

One request → Multiple responses.

```text id="grpc6"
Client

↓

Request

↓

Server

↓

Response 1

↓

Response 2

↓

Response 3
```

Example:

Live stock prices.

---

## 3. Client Streaming RPC

Multiple requests → One response.

```text id="grpc7"
Client

↓

Request 1

↓

Request 2

↓

Request 3

↓

Server

↓

Single Response
```

Example:

Uploading a large file.

---

## 4. Bidirectional Streaming RPC

Multiple requests ↔ Multiple responses simultaneously.

```text id="grpc8"
Client

⇄

Server
```

Example:

Chat applications.

---

# gRPC vs REST

| Feature         | gRPC     | REST              |
| --------------- | -------- | ----------------- |
| Protocol        | HTTP/2   | HTTP/1.1 / HTTP/2 |
| Data Format     | Protobuf | JSON/XML          |
| Performance     | Faster   | Slower            |
| Payload Size    | Smaller  | Larger            |
| Streaming       | Built-in | Limited           |
| Browser Support | Limited  | Excellent         |
| Human Readable  | No       | Yes               |

---

# Advantages

* High performance.
* Low latency.
* Smaller payloads.
* Built-in streaming.
* Strong API contracts using Protobuf.
* Excellent for microservices.

---

# Limitations

* Not human-readable.
* More difficult to test manually than REST.
* Limited direct browser support.
* Requires Protobuf definitions.

---

# Real-World Example

Suppose an e-commerce application processes an order.

```text id="grpc9"
Frontend

↓

Order Service

↓

Payment Service

↓

Inventory Service

↓

Shipping Service
```

These internal services communicate efficiently using gRPC.

---

# When to Use gRPC

Use gRPC for:

* Microservices
* Internal Service Communication
* Real-Time Streaming
* IoT Systems
* High-Performance APIs
* Cloud-Native Applications

Use REST for:

* Public APIs
* Browser-based applications
* Third-party integrations
* Simpler CRUD services

---

# Quick Revision

```text id="grpc10"
gRPC

↓

HTTP/2

+

Protocol Buffers

↓

Fast Communication

RPC Types

✔ Unary

✔ Server Streaming

✔ Client Streaming

✔ Bidirectional Streaming

Best For

✔ Microservices

✔ Internal APIs

✔ Real-Time Systems
```

---

# Key Takeaways

* **gRPC** is a high-performance RPC framework developed by Google.
* It uses **HTTP/2** and **Protocol Buffers** for efficient communication.
* gRPC supports **Unary**, **Server Streaming**, **Client Streaming**, and **Bidirectional Streaming** RPCs.
* Compared to REST, gRPC provides lower latency, smaller payloads, and better performance, making it ideal for **microservices** and **distributed systems**.
* REST remains a better choice for public APIs and browser-facing applications due to its simplicity and widespread support.

---

> **Next Topic:** `11-REST-APIs.md`
