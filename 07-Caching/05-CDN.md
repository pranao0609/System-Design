# Content Delivery Network (CDN)

> *"A Content Delivery Network (CDN) is a globally distributed network of servers that caches and delivers content from locations closer to users, reducing latency and improving performance."*

---

# Table of Contents

* What is a CDN?
* Why Do We Need a CDN?
* How a CDN Works
* Types of Content
* Cache Hit & Cache Miss
* CDN Architecture
* Benefits of CDN
* Challenges of CDN
* Popular CDN Providers
* Real-World Examples
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is a CDN?

A **Content Delivery Network (CDN)** is a network of geographically distributed **Edge Servers** that cache content close to users.

Instead of every request going to the origin server, users are served from the nearest CDN server whenever possible.

```text id="cdn1"
User

↓

Nearest CDN Edge Server

↓

Origin Server (Only if Needed)
```

---

# Why Do We Need a CDN?

Suppose your application is hosted only in the USA.

```text id="cdn2"
India User

↓

USA Server
```

Problems:

* High latency
* Slow loading
* Increased bandwidth usage

With a CDN:

```text id="cdn3"
India User

↓

Mumbai Edge Server

↓

Fast Response
```

Content is served from a nearby location.

---

# How a CDN Works

Request flow:

```text id="cdn4"
User

↓

CDN Edge Server

↓

Content Cached?

↓

Yes → Return Content

↓

No → Origin Server

↓

Store in Cache

↓

Return Content
```

Future requests are served directly from the edge server.

---

# Types of Content

CDNs primarily cache **static content**, such as:

* Images
* CSS
* JavaScript
* Videos
* Audio Files
* Documents
* Fonts

Some CDNs also support **dynamic content acceleration** through optimized routing and caching techniques.

---

# Cache Hit & Cache Miss

## Cache Hit

The requested file already exists on the edge server.

```text id="cdn5"
User

↓

CDN

↓

Content Found

↓

Fast Response
```

---

## Cache Miss

The file is not present.

```text id="cdn6"
User

↓

CDN

↓

Origin Server

↓

Cache Content

↓

Return Response
```

The first request is slower; subsequent requests are faster.

---

# CDN Architecture

```text id="cdn7"
Users

↓

Nearest Edge Server

↓

Regional Cache

↓

Origin Server
```

This hierarchical architecture reduces latency and minimizes origin server load.

---

# Benefits of CDN

* Lower latency.
* Faster page loading.
* Reduced bandwidth costs.
* Lower origin server load.
* High availability.
* Better scalability.
* Improved user experience.

---

# Challenges of CDN

* Cache invalidation complexity.
* Additional infrastructure cost.
* Dynamic content is harder to cache.
* Data synchronization across edge locations.

---

# Popular CDN Providers

* Cloudflare
* Amazon CloudFront
* Akamai
* Fastly
* Google Cloud CDN
* Microsoft Azure CDN

---

# Real-World Examples

## Netflix

Caches videos on edge servers worldwide for faster streaming.

---

## YouTube

Serves video content from CDN edge locations closest to viewers.

---

## Amazon

Product images and static assets are delivered through CloudFront.

---

## Facebook

Photos and videos are cached globally to reduce loading times.

---

# CDN vs Cache

| CDN                         | Cache                                  |
| --------------------------- | -------------------------------------- |
| Distributed globally        | Usually local or application-level     |
| Focuses on content delivery | General-purpose data storage           |
| Edge servers                | Memory or storage-based                |
| Optimized for static assets | Can store any frequently accessed data |

---

# When to Use a CDN

Use a CDN when:

* Users are geographically distributed.
* The application serves large static files.
* Fast page loading is important.
* High traffic is expected.
* Global availability is required.

---

# Quick Revision

```text id="cdn8"
CDN

↓

Edge Servers

↓

Nearest User

↓

Cache Hit

↓

Fast Response

Cache Miss

↓

Origin Server

Benefits

✔ Low Latency

✔ High Availability

✔ Reduced Server Load

Popular

Cloudflare

CloudFront

Akamai

Fastly
```

---

# Key Takeaways

* A **Content Delivery Network (CDN)** caches content on geographically distributed edge servers to deliver it closer to users.
* CDNs significantly reduce **latency**, improve **page load times**, and reduce the load on origin servers.
* They are ideal for serving **static assets** such as images, videos, CSS, JavaScript, and documents.
* A **Cache Hit** serves content directly from the edge server, while a **Cache Miss** fetches it from the origin server before caching it.
* CDNs are an essential component of modern web applications and are widely used by companies like **Netflix, YouTube, Amazon, Facebook, and Cloudflare**.

---

> **Next Topic:** `06-Cache-Strategies.md`
