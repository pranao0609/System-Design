# Reverse Proxy

> *"A Reverse Proxy is a server that sits in front of one or more backend servers, receives client requests, and forwards them to the appropriate server while hiding the backend infrastructure from clients."*

---

# Table of Contents

* What is a Proxy?
* What is a Reverse Proxy?
* Why Do We Need a Reverse Proxy?
* How a Reverse Proxy Works
* Features of a Reverse Proxy
* Reverse Proxy vs Forward Proxy
* Popular Reverse Proxy Servers
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is a Proxy?

A **Proxy Server** is an intermediary between two systems.

Instead of communicating directly, requests pass through the proxy.

```text id="rp1"
Client

↓

Proxy

↓

Destination
```

There are two main types:

* Forward Proxy
* Reverse Proxy

---

# What is a Reverse Proxy?

A **Reverse Proxy** sits in front of backend servers.

Clients send requests to the reverse proxy instead of directly to the application servers.

The reverse proxy forwards each request to the appropriate backend server and returns the response to the client.

```text id="rp2"
Client

↓

Reverse Proxy

↓

Application Servers
```

Clients never communicate directly with backend servers.

---

# Why Do We Need a Reverse Proxy?

Without a reverse proxy:

```text id="rp3"
Client

↓

Server A

Server B

Server C
```

Clients must know which server to contact.

---

With a reverse proxy:

```text id="rp4"
Client

↓

Reverse Proxy

↓

Server A

Server B

Server C
```

The proxy handles request routing automatically.

Benefits include:

* Load balancing
* Improved security
* SSL/TLS termination
* Caching
* Compression
* Centralized routing

---

# How a Reverse Proxy Works

Step-by-step flow:

```text id="rp5"
Client

↓

Reverse Proxy

↓

Select Backend Server

↓

Server Processes Request

↓

Reverse Proxy

↓

Client
```

The client is unaware of which backend server handled the request.

---

# Features of a Reverse Proxy

## 1. Load Balancing

Distributes incoming requests across multiple backend servers.

---

## 2. SSL/TLS Termination

Handles HTTPS encryption at the proxy.

```text id="rp6"
HTTPS

↓

Reverse Proxy

↓

HTTP

↓

Backend Servers
```

This reduces the encryption workload on application servers.

---

## 3. Caching

Frequently requested content can be cached.

```text id="rp7"
Client

↓

Reverse Proxy Cache

↓

Response
```

This reduces backend load and improves response time.

---

## 4. Compression

Compresses responses before sending them to clients, reducing bandwidth usage.

---

## 5. Security

Backend servers remain hidden from the public internet.

Only the reverse proxy is exposed.

This reduces the attack surface.

---

## 6. URL Routing

Requests can be routed based on:

* URL path
* Hostname
* HTTP headers

Example:

```text id="rp8"
/api

↓

API Server

/images

↓

Image Server
```

---

# Reverse Proxy vs Forward Proxy

| Reverse Proxy             | Forward Proxy                      |
| ------------------------- | ---------------------------------- |
| Represents servers        | Represents clients                 |
| Protects backend servers  | Protects client identity           |
| Used by server owners     | Used by end users or organizations |
| Supports load balancing   | Supports anonymity and filtering   |
| Receives incoming traffic | Sends outgoing traffic             |

---

# Popular Reverse Proxy Servers

* Nginx
* HAProxy
* Envoy
* Traefik
* Apache HTTP Server
* Caddy

These are widely used in cloud-native and microservice architectures.

---

# Real-World Examples

## Netflix

Routes incoming traffic to appropriate microservices.

---

## Kubernetes

Ingress Controllers (such as NGINX Ingress Controller) function as reverse proxies.

---

## Amazon

Uses reverse proxies to distribute traffic across thousands of backend servers.

---

## GitHub

Uses reverse proxies to route requests efficiently and improve security.

---

# Advantages

* Improved scalability.
* Better security.
* SSL/TLS termination.
* Load balancing.
* Faster responses through caching.
* Centralized traffic management.

---

# Disadvantages

* Additional infrastructure.
* Potential single point of failure if not deployed redundantly.
* Extra configuration and maintenance.

---

# Quick Revision

```text id="rp9"
Reverse Proxy

↓

Receives Client Requests

↓

Routes Requests

↓

Backend Servers

Features

✔ Load Balancing

✔ SSL Termination

✔ Caching

✔ Compression

✔ Security

Popular

Nginx

HAProxy

Envoy

Traefik
```

---

# Key Takeaways

* A **Reverse Proxy** sits between clients and backend servers, forwarding requests on behalf of the servers.
* It improves **security, scalability, and performance** by hiding backend infrastructure and distributing traffic.
* Common features include **load balancing, SSL termination, caching, compression, and URL-based routing**.
* Popular reverse proxy solutions include **Nginx, HAProxy, Envoy, Traefik, and Apache HTTP Server**.
* Reverse proxies are a fundamental building block of modern cloud architectures, microservices, and Kubernetes deployments.

---

> **Next Topic:** `02-Forward-Proxy.md`
