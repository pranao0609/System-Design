# WebSockets

> *"WebSockets provide full-duplex, persistent communication between a client and a server, enabling real-time applications such as chat systems, online gaming, stock trading, and live notifications."*

---

# Table of Contents

* What are WebSockets?
* Why Do We Need WebSockets?
* HTTP vs WebSockets
* How WebSockets Work
* WebSocket Handshake
* WebSocket Connection Lifecycle
* Use Cases
* Advantages & Limitations
* Interview Questions
* Quick Revision

---

# What are WebSockets?

**WebSocket** is a communication protocol that enables **persistent, bidirectional (full-duplex)** communication between a client and a server over a single TCP connection.

Unlike HTTP, where the client must initiate every request, WebSockets allow **both the client and server to send data at any time**.

---

# Why Do We Need WebSockets?

HTTP follows a **request-response** model.

```text id="ws1"
Client

↓

Request

↓

Server

↓

Response
```

If the server has new data, it **cannot send it automatically**.

The client must send another request.

This is inefficient for applications that require real-time updates.

---

# HTTP vs WebSockets

| Feature       | HTTP             | WebSocket   |
| ------------- | ---------------- | ----------- |
| Communication | Request-Response | Full-Duplex |
| Connection    | Short-lived      | Persistent  |
| Real-Time     | No               | Yes         |
| Overhead      | Higher           | Lower       |
| Server Push   | No               | Yes         |

---

# How WebSockets Work

A WebSocket connection starts as an HTTP request.

```text id="ws2"
Client

↓

HTTP Upgrade Request

↓

Server

↓

101 Switching Protocols

↓

WebSocket Connection Established
```

After the upgrade, both client and server communicate freely.

---

# WebSocket Handshake

```text id="ws3"
Client                     Server

HTTP Upgrade Request ----->

                 <--------- 101 Switching Protocols

WebSocket Connection Established
```

The connection remains open until one side closes it.

---

# WebSocket Connection Lifecycle

```text id="ws4"
Connect

↓

Handshake

↓

Open Connection

↓

Exchange Messages

↓

Close Connection
```

Unlike HTTP, there is no need to reconnect for every message.

---

# Full-Duplex Communication

Once connected:

```text id="ws5"
Client

⇄

Server
```

Both can send and receive messages independently and simultaneously.

---

# Real-World Example

## Chat Application

```text id="ws6"
User A

⇄

WebSocket Server

⇄

User B
```

When User A sends a message, the server immediately pushes it to User B without waiting for another request.

---

## Stock Market Dashboard

```text id="ws7"
Stock Exchange

↓

Server

↓

Live Price Updates

↓

Browser
```

Prices update instantly as they change.

---

## Multiplayer Online Game

Player positions and actions are continuously exchanged between the client and server using WebSockets to minimize latency.

---

# Common Use Cases

* Live Chat Applications
* Multiplayer Games
* Live Sports Scores
* Stock Market Dashboards
* Cryptocurrency Exchanges
* Online Collaboration Tools
* Real-Time Notifications
* IoT Monitoring Systems

---

# Advantages

* Low latency.
* Persistent connection.
* Full-duplex communication.
* Reduced overhead.
* Efficient for frequent message exchange.

---

# Limitations

* Requires persistent server resources.
* More complex than HTTP.
* Not suitable for simple request-response applications.
* Scaling large numbers of WebSocket connections requires careful infrastructure design.

---

# WebSocket vs HTTP Polling

## HTTP Polling

```text id="ws8"
Client

↓

Request

↓

Response

↓

Wait

↓

Request Again
```

The client repeatedly checks for updates.

---

## WebSocket

```text id="ws9"
Client

⇄

Server

Persistent Connection

Instant Updates
```

The server pushes updates immediately.

---

# Secure WebSockets

Secure WebSockets use **TLS**.

| Protocol | Purpose             |
| -------- | ------------------- |
| `ws://`  | Unencrypted         |
| `wss://` | Encrypted using TLS |

For production applications, **`wss://`** is recommended.

---

# Quick Revision

```text id="ws10"
WebSockets

↓

HTTP Upgrade

↓

101 Switching Protocols

↓

Persistent Connection

↓

Full-Duplex Communication

Protocols

ws://

wss://

Use Cases

✔ Chat

✔ Gaming

✔ Stock Market

✔ Notifications

✔ Live Dashboards
```

---

# Key Takeaways

* **WebSockets** provide persistent, full-duplex communication over a single TCP connection.
* The connection begins with an **HTTP Upgrade** request and transitions to the WebSocket protocol.
* Unlike HTTP, WebSockets allow both the client and server to send messages at any time.
* They are ideal for **real-time applications** such as chat systems, multiplayer games, financial dashboards, and collaborative tools.
* For secure communication, use **`wss://`**, which encrypts traffic using TLS.

---

> **Next Topic:** `10-gRPC.md`
