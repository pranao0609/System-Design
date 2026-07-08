# Layer 7 (L7) Load Balancing

> *"Layer 7 (L7) Load Balancing distributes traffic based on application-layer information such as URLs, HTTP headers, cookies, hostnames, and request content."*

---

# Table of Contents

* What is Layer 7 Load Balancing?
* Why Do We Need L7 Load Balancing?
* How L7 Load Balancing Works
* OSI Layer 7
* Content-Based Routing
* Load Balancing Algorithms
* Advantages
* Disadvantages
* L7 vs L4 Load Balancing
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Layer 7 Load Balancing?

**Layer 7 (L7) Load Balancing** operates at the **Application Layer** of the OSI model.

Unlike L4, it understands HTTP/HTTPS traffic and can inspect:

* URL Path
* HTTP Method
* Hostname
* Headers
* Cookies
* Query Parameters

This enables intelligent request routing.

---

# Why Do We Need L7 Load Balancing?

Consider an e-commerce application.

Users access different services:

```text id="l71"
/products

/orders

/payments

/images
```

Instead of sending every request to the same backend, L7 Load Balancing routes each request to the appropriate service.

---

# How L7 Load Balancing Works

```text id="l72"
Client

↓

HTTP Request

↓

L7 Load Balancer

↓

Inspect URL/Header

↓

Route to Correct Service
```

The load balancer analyzes the request before forwarding it.

---

# OSI Layer 7

The OSI model consists of seven layers.

```text id="l73"
Application (7) ← L7

Presentation (6)

Session (5)

Transport (4)

Network (3)

Data Link (2)

Physical (1)
```

L7 Load Balancers operate at the **Application Layer**.

---

# Content-Based Routing

One of the biggest advantages of L7 Load Balancing is routing based on request content.

Example:

```text id="l74"
/api/*

↓

API Servers

/images/*

↓

Image Servers

/videos/*

↓

Video Servers

/admin/*

↓

Admin Service
```

Each request reaches the appropriate backend service.

---

# Host-Based Routing

Requests can also be routed using the hostname.

Example:

```text id="l75"
api.example.com

↓

API Cluster

shop.example.com

↓

Shopping Service

blog.example.com

↓

Blog Service
```

This is common in microservices and multi-tenant applications.

---

# Load Balancing Algorithms

L7 Load Balancers commonly support:

* Round Robin
* Least Connections
* Weighted Round Robin
* IP Hash
* Least Response Time

In addition, routing decisions can be based on application-layer information.

---

# Advantages

* Content-aware routing.
* Supports URL-based routing.
* Supports hostname-based routing.
* Cookie-based session management.
* SSL/TLS termination.
* Better suited for microservices.

---

# Disadvantages

* More CPU intensive.
* Higher latency than L4.
* More complex configuration.
* Limited to application-layer protocols (e.g., HTTP/HTTPS).

---

# L7 vs L4 Load Balancing

| Layer 7                 | Layer 4             |
| ----------------------- | ------------------- |
| Application Layer       | Transport Layer     |
| Understands HTTP/HTTPS  | Uses only IP & Port |
| Routes by URL & Headers | Routes by IP & Port |
| More intelligent        | Faster              |
| Higher CPU usage        | Lower CPU usage     |

---

# Real-World Examples

## Netflix

Routes requests to different microservices based on API paths.

---

## Kubernetes Ingress

Ingress Controllers route requests to different services based on paths and hostnames.

---

## Amazon

Different URLs (orders, payments, products) are routed to different backend services.

---

## GitHub

Routes API traffic separately from the web interface.

---

# Popular L7 Load Balancers

* NGINX
* HAProxy
* Envoy Proxy
* Traefik
* AWS Application Load Balancer (ALB)
* Google Cloud HTTP(S) Load Balancer

---

# When to Use L7 Load Balancing

Use L7 when:

* Building REST APIs.
* Using microservices.
* Routing by URL or hostname.
* SSL termination is required.
* Cookie-based session routing is needed.

---

# Quick Revision

```text id="l76"
Layer 7 Load Balancing

↓

Application Layer

↓

Understands

✔ URL

✔ Headers

✔ Cookies

✔ Hostname

Routing

✔ URL-Based

✔ Host-Based

✔ Content-Based

Popular

NGINX

Envoy

Traefik

AWS ALB
```

---

# Key Takeaways

* **Layer 7 Load Balancing** operates at the **Application Layer** and understands HTTP/HTTPS traffic.
* It supports **URL-based, host-based, and content-based routing**, making it ideal for microservices and modern web applications.
* Features such as **SSL termination, cookie-based session management, and intelligent request routing** provide greater flexibility than L4 load balancing.
* L7 load balancing has higher processing overhead but enables much more advanced traffic management.
* It is widely used in **Kubernetes, cloud platforms, API gateways, and large-scale web applications**.

---

> **Next Topic:** `05-Consistent-Hashing.md`
