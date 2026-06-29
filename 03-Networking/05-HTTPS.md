# HTTPS (HyperText Transfer Protocol Secure)

> *"HTTPS is the secure version of HTTP. It uses TLS (Transport Layer Security) to encrypt communication between a client and a server, ensuring confidentiality, integrity, and authentication."*

---

# Table of Contents

* What is HTTPS?
* Why Do We Need HTTPS?
* HTTP vs HTTPS
* How HTTPS Works
* TLS Handshake
* SSL/TLS Certificate
* Public Key & Private Key
* Advantages
* Interview Questions
* Quick Revision

---

# What is HTTPS?

**HTTPS (HyperText Transfer Protocol Secure)** is the secure version of HTTP.

It combines:

```text
HTTP
+
TLS (Transport Layer Security)
=
HTTPS
```

HTTPS encrypts all communication between the client and the server so that attackers cannot read or modify the data.

Examples:

* Online Banking
* E-commerce Websites
* Gmail
* Social Media
* Payment Gateways

---

# Why Do We Need HTTPS?

Plain HTTP sends data in **plaintext**.

Example:

```text
Username = john
Password = 123456
```

Anyone intercepting the network traffic can read this information.

HTTPS solves this problem by encrypting the communication.

It provides:

* Confidentiality
* Integrity
* Authentication

---

# HTTP vs HTTPS

| Feature         | HTTP            | HTTPS       |
| --------------- | --------------- | ----------- |
| Security        | ❌ No Encryption | ✅ Encrypted |
| Port            | 80              | 443         |
| Protocol        | HTTP            | HTTP + TLS  |
| Certificate     | Not Required    | Required    |
| Data Protection | No              | Yes         |

---

# How HTTPS Works

```text
Browser
    │
HTTPS Request
    │
TLS Handshake
    │
Encrypted Connection
    │
Server
    │
Encrypted Response
    │
Browser
```

After the TLS handshake, all data is encrypted.

---

# TLS Handshake

The TLS handshake establishes a secure connection before any application data is exchanged.

```text
Client                     Server

Client Hello  ----------->

                 <--------- Server Hello

                 <--------- Certificate

Key Exchange  ----------->

Secure Connection Established

Encrypted Data Exchange
```

### Step 1: Client Hello

The browser sends:

* Supported TLS versions
* Supported encryption algorithms (cipher suites)
* Random number

---

### Step 2: Server Hello

The server responds with:

* Chosen TLS version
* Cipher suite
* Server random number

---

### Step 3: Certificate

The server sends its **Digital Certificate** to prove its identity.

The browser verifies:

* Certificate validity
* Trusted Certificate Authority (CA)
* Domain name

---

### Step 4: Key Exchange

The client and server securely establish a **shared session key**.

---

### Step 5: Secure Communication

All HTTP requests and responses are now encrypted using the session key.

---

# SSL/TLS Certificate

A certificate is a digital document that verifies the identity of a website.

It contains:

* Domain Name
* Public Key
* Certificate Authority (CA)
* Expiration Date
* Digital Signature

Example:

```text
www.example.com

Issued By:

Let's Encrypt

Valid Until:

31 Dec 2026
```

---

# Public Key & Private Key

HTTPS uses **Asymmetric Encryption** during the handshake.

```text
Server

Public Key  ─────────► Everyone

Private Key ─────────► Secret
```

* **Public Key**: Used to encrypt data.
* **Private Key**: Used to decrypt data.

After the handshake, communication switches to **Symmetric Encryption**, which is much faster.

---

# Why Use Symmetric Encryption After the Handshake?

Asymmetric encryption is computationally expensive.

Once a secure session key is established:

```text
Client

Session Key

⇄

Server

Session Key
```

Both sides use the same secret key to encrypt and decrypt data efficiently.

---

# Advantages of HTTPS

* Encrypts communication.
* Protects sensitive information.
* Prevents eavesdropping.
* Prevents data tampering.
* Authenticates the server.
* Improves user trust.
* Required for many modern browser features.

---

# Real-World Example

Opening:

```text
https://www.amazon.com
```

Flow:

```text
Browser
      │
TLS Handshake
      │
Certificate Verification
      │
Encrypted Connection
      │
HTTP Request
      │
Amazon Server
      │
Encrypted Response
      │
Browser Displays Page
```

---

# Interview Questions

* What is HTTPS?
* Difference between HTTP and HTTPS?
* What is TLS?
* Why is HTTPS secure?
* What is a Digital Certificate?
* What is a Certificate Authority (CA)?
* Difference between Public Key and Private Key?
* Why does HTTPS switch to symmetric encryption after the handshake?
* What port does HTTPS use?

---

# Quick Revision

```text
HTTPS

HTTP
+
TLS

↓

Encrypted Communication

Port

443

Security

✔ Confidentiality

✔ Integrity

✔ Authentication

Handshake

Client Hello

↓

Server Hello

↓

Certificate

↓

Key Exchange

↓

Encrypted Communication
```

---

# Key Takeaways

* HTTPS is the secure version of HTTP and uses **TLS** to encrypt communication.
* It protects data from eavesdropping, tampering, and impersonation.
* The **TLS handshake** establishes a secure connection before any application data is transmitted.
* **Digital Certificates** verify the identity of the server.
* HTTPS uses **asymmetric encryption** during the handshake and **symmetric encryption** for the actual data transfer because it is more efficient.
* HTTPS is essential for secure web applications, online banking, e-commerce, and APIs.

---

> **Next Topic:** `06-HTTP2-and-HTTP3.md`
