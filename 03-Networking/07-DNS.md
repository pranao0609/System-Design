# DNS (Domain Name System)

> *"DNS is the Internet's phonebook. It translates human-readable domain names into IP addresses so that computers can locate and communicate with each other."*

---

# Table of Contents

* What is DNS?
* Why Do We Need DNS?
* How DNS Works
* DNS Hierarchy
* Types of DNS Servers
* DNS Record Types
* DNS Caching
* Recursive vs Iterative Query
* Real-World Example
* Interview Questions
* Quick Revision

---

# What is DNS?

**DNS (Domain Name System)** is a distributed naming system that converts **domain names** into **IP addresses**.

Humans prefer names like:

```text id="c0i9nt"
www.google.com
```

Computers communicate using IP addresses like:

```text id="k3qmyl"
142.250.183.110
```

DNS bridges this gap.

---

# Why Do We Need DNS?

Imagine remembering the IP address of every website you visit.

Instead of typing:

```text id="x3hzx7"
142.250.183.110
```

you simply type:

```text id="gzv8r8"
www.google.com
```

DNS resolves the name to the correct IP address automatically.

Benefits:

* Easy-to-remember names
* Flexibility (IP can change without changing the domain name)
* Scalable Internet addressing

---

# How DNS Works

When you enter a URL:

```text id="slpn1k"
https://www.google.com
```

the browser first asks DNS for the server's IP address.

```text id="5fzjlwm"
User

↓

Browser

↓

DNS Resolver

↓

DNS Server

↓

IP Address

↓

Google Server
```

Once the IP address is obtained, the browser establishes a connection with the server.

---

# DNS Resolution Process

```text id="pns4l5"
1. User enters domain

↓

2. Browser checks cache

↓

3. OS checks cache

↓

4. DNS Resolver

↓

5. Root DNS Server

↓

6. TLD DNS Server

↓

7. Authoritative DNS Server

↓

8. Returns IP Address

↓

9. Browser connects to server
```

---

# DNS Hierarchy

DNS is organized in a hierarchical structure.

```text id="8bjlwm"
                 Root (.)
                    │
          ┌─────────┴─────────┐
          │                   │
        .com                .org
          │
      google.com
          │
      www.google.com
```

Each level delegates responsibility to the next.

---

# Types of DNS Servers

## 1. DNS Resolver

Receives DNS queries from clients.

Usually provided by:

* ISP
* Google DNS (8.8.8.8)
* Cloudflare DNS (1.1.1.1)

---

## 2. Root Name Server

The top-level DNS server.

Responsibilities:

* Knows where Top-Level Domain (TLD) servers are located.
* Does **not** know individual domain IPs.

---

## 3. TLD (Top-Level Domain) Server

Responsible for domain extensions such as:

```text id="lljlwm"
.com

.org

.net

.edu

.in
```

It directs the resolver to the appropriate authoritative server.

---

## 4. Authoritative Name Server

Stores the actual DNS records for a domain.

Example:

```text id="wjlwm4"
google.com

↓

142.250.183.110
```

This is the final source of truth.

---

# DNS Record Types

| Record | Purpose                        |
| ------ | ------------------------------ |
| A      | Maps domain → IPv4 address     |
| AAAA   | Maps domain → IPv6 address     |
| CNAME  | Alias for another domain       |
| MX     | Mail server                    |
| NS     | Name server                    |
| TXT    | Verification & metadata        |
| PTR    | Reverse DNS lookup             |
| SOA    | Start of Authority information |

Example:

```text id="vjlwm5"
google.com

A

↓

142.250.183.110
```

---

# DNS Caching

To improve performance, DNS responses are cached.

Cache locations:

```text id="jlwm6a"
Browser Cache

↓

Operating System Cache

↓

DNS Resolver Cache
```

Benefits:

* Faster lookups
* Reduced network traffic
* Lower DNS server load

Each DNS record has a **TTL (Time To Live)** value indicating how long it can be cached.

---

# Recursive vs Iterative Query

## Recursive Query

The DNS resolver performs all lookups and returns the final answer.

```text id="jlwm7b"
Client

↓

Resolver

↓

Root

↓

TLD

↓

Authoritative

↓

Client Gets IP
```

Most users experience recursive queries.

---

## Iterative Query

Each DNS server returns the best information it has, directing the requester to the next server.

```text id="jlwm8c"
Client

↓

Root

↓

TLD

↓

Authoritative
```

The requester performs the remaining lookups.

---

# Real-World Example

Suppose you open:

```text id="jlwm9d"
https://www.github.com
```

Flow:

```text id="jlwm0e"
Browser

↓

DNS Lookup

↓

IP Address Returned

↓

TCP Connection

↓

HTTPS Request

↓

GitHub Server

↓

Response
```

Without DNS, the browser wouldn't know where to send the request.

---

# Advantages

* Human-friendly names
* Distributed architecture
* Highly scalable
* Fast due to caching
* Fault tolerant through multiple DNS servers

---

# Limitations

* DNS lookups add slight latency.
* Cache may contain outdated records until TTL expires.
* DNS attacks (e.g., spoofing, cache poisoning) are possible without security extensions.

---

# Quick Revision

```text id="jlwm1f"
DNS

Domain Name

↓

DNS Resolver

↓

Root Server

↓

TLD Server

↓

Authoritative Server

↓

IP Address

Common Records

A

AAAA

CNAME

MX

NS

TXT

Caching

Browser

↓

OS

↓

Resolver

↓

TTL
```

---

# Key Takeaways

* DNS translates **domain names** into **IP addresses**, enabling devices to locate servers on the Internet.
* DNS follows a **hierarchical structure** consisting of Root, TLD, and Authoritative Name Servers.
* DNS caching improves performance by storing recent lookup results.
* Common DNS records include **A, AAAA, CNAME, MX, NS, and TXT**.
* Understanding DNS is essential because every web request begins with a DNS lookup before establishing a network connection.

---

> **Next Topic:** `08-TLS-and-SSL.md`
