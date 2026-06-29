# 03. Networking Fundamentals

Modern distributed systems communicate over networks. Whether you're designing a social media platform, an e-commerce application, or a real-time chat system, understanding networking fundamentals is essential.

This section covers how data travels across the internet—from a user's browser to a server and back. It introduces the protocols, layers, and communication mechanisms that power modern web applications.

By the end of this section, you'll understand how clients and servers communicate, how requests are routed, how secure communication works, and how APIs enable distributed systems.

---

# 📚 Topics Covered

## 1. OSI Model

Understand the seven-layer OSI model, the responsibility of each layer, encapsulation, and how data flows through a network.

📄 **File:** `01-OSI-Model.md`

---

## 2. TCP/IP Model

Learn the TCP/IP protocol suite, its four layers, and how it differs from the OSI model.

📄 **File:** `02-TCP-IP-Model.md`

---

## 3. TCP vs UDP

Compare the two primary transport layer protocols, their characteristics, advantages, disadvantages, and use cases.

📄 **File:** `03-TCP-vs-UDP.md`

---

## 4. HTTP & HTTPS

Understand how browsers communicate with servers using HTTP, the request-response lifecycle, status codes, cookies, sessions, and HTTPS encryption.

📄 **File:** `04-HTTP-and-HTTPS.md`

---

## 5. HTTP/2 & HTTP/3

Explore improvements over HTTP/1.1, including multiplexing, header compression, server push, QUIC, and reduced latency.

📄 **File:** `05-HTTP2-and-HTTP3.md`

---

## 6. DNS (Domain Name System)

Learn how domain names are translated into IP addresses, DNS hierarchy, caching, recursive and iterative lookups.

📄 **File:** `06-DNS.md`

---

## 7. TLS / SSL

Understand how secure communication is established using encryption, certificates, digital signatures, and the TLS handshake.

📄 **File:** `07-TLS-and-SSL.md`

---

## 8. WebSockets

Learn how persistent full-duplex communication works and why WebSockets are widely used in chat applications, multiplayer games, and live dashboards.

📄 **File:** `08-WebSockets.md`

---

## 9. gRPC

Explore Google's high-performance Remote Procedure Call (RPC) framework, Protocol Buffers, streaming, and use cases in microservices.

📄 **File:** `09-gRPC.md`

---

## 10. REST APIs

Learn REST architecture, HTTP methods, resource design, status codes, idempotency, versioning, authentication, and API best practices.

📄 **File:** `10-REST-APIs.md`

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

* Explain how data travels from a client to a server.
* Understand the OSI and TCP/IP networking models.
* Compare TCP and UDP and choose the appropriate protocol.
* Describe the HTTP request-response lifecycle.
* Explain HTTPS and the TLS handshake.
* Understand DNS resolution and caching.
* Differentiate HTTP/1.1, HTTP/2, and HTTP/3.
* Explain when to use WebSockets instead of HTTP.
* Build and design RESTful APIs.
* Understand why gRPC is widely used in microservices.

---

# 📂 Folder Structure

```text
03-Networking-Fundamentals/
│
├── README.md
├── 01-OSI-Model.md
├── 02-TCP-IP-Model.md
├── 03-TCP-vs-UDP.md
├── 04-HTTP-and-HTTPS.md
├── 05-HTTP2-and-HTTP3.md
├── 06-DNS.md
├── 07-TLS-and-SSL.md
├── 08-WebSockets.md
├── 09-gRPC.md
└── 10-REST-APIs.md
```

---

# 🌍 Why This Section Matters

Every request made by a user—whether opening a website, streaming a video, or sending a chat message—travels through multiple networking layers before reaching a server.

Understanding these concepts helps explain:

* Why websites load quickly or slowly.
* How browsers communicate with servers.
* Why HTTPS is secure.
* How APIs exchange information.
* Why WebSockets are preferred for real-time communication.
* How microservices communicate efficiently.
* How distributed systems exchange data across the internet.

These concepts form the backbone of backend engineering and are frequently discussed in system design interviews.

---

