# TLS & SSL (Transport Layer Security / Secure Sockets Layer)

> *"TLS is the security protocol that encrypts communication over the Internet. It ensures that data exchanged between a client and a server remains confidential, authentic, and unaltered."*

---

# Table of Contents

* What are SSL & TLS?
* Why Do We Need TLS?
* SSL vs TLS
* How TLS Works
* TLS Handshake
* Certificates & Certificate Authorities (CA)
* Symmetric vs Asymmetric Encryption
* Digital Signatures
* TLS Versions
* Interview Questions
* Quick Revision

---

# What are SSL & TLS?

**SSL (Secure Sockets Layer)** and **TLS (Transport Layer Security)** are cryptographic protocols used to secure communication over a network.

Today:

* **SSL is obsolete**.
* **TLS** is the modern and secure replacement.

Whenever you visit a website using:

```text id="tls1"
https://example.com
```

your browser uses **TLS** to establish a secure connection.

---

# Why Do We Need TLS?

Without TLS:

```text id="tls2"
Browser
      │
Plain Text Data
      │
Internet
      │
Attacker Can Read Data
```

Sensitive information like:

* Passwords
* Credit Card Numbers
* Banking Details
* Personal Messages

could be intercepted.

TLS protects against this.

---

# Security Goals of TLS

TLS provides three major security properties:

### 1. Confidentiality

Only the sender and receiver can read the data.

---

### 2. Integrity

Ensures the data has not been modified during transmission.

---

### 3. Authentication

Verifies that the client is communicating with the legitimate server.

---

# SSL vs TLS

| SSL                | TLS                           |
| ------------------ | ----------------------------- |
| Older protocol     | Modern protocol               |
| Less secure        | More secure                   |
| Deprecated         | Widely used                   |
| SSL 3.0 vulnerable | TLS 1.2 & TLS 1.3 recommended |

Although people still say "SSL Certificate," modern websites actually use **TLS certificates**.

---

# How TLS Works

Before any HTTP data is exchanged:

```text id="tls3"
Browser

↓

TLS Handshake

↓

Secure Connection

↓

Encrypted HTTP Communication
```

The handshake establishes encryption keys and verifies the server.

---

# TLS Handshake

```text id="tls4"
Client                     Server

Client Hello  ----------->

                 <--------- Server Hello

                 <--------- Certificate

Key Exchange  ----------->

Secure Session Established

Encrypted Communication
```

---

## Step 1 – Client Hello

The browser sends:

* Supported TLS versions
* Supported Cipher Suites
* Random Number

---

## Step 2 – Server Hello

The server replies with:

* Selected TLS version
* Cipher Suite
* Server Random Number

---

## Step 3 – Certificate

The server sends its digital certificate.

The browser verifies:

* Certificate Authority (CA)
* Expiration Date
* Domain Name
* Digital Signature

If verification fails:

```text id="tls5"
⚠ Connection Not Secure
```

---

## Step 4 – Key Exchange

The client and server securely generate a shared **Session Key**.

---

## Step 5 – Secure Communication

All subsequent data is encrypted using the session key.

---

# Certificates

A **Digital Certificate** proves the identity of a website.

Example:

```text id="tls6"
Domain

www.example.com

Issued By

Let's Encrypt

Valid Until

31 Dec 2027
```

A certificate contains:

* Domain Name
* Public Key
* Certificate Authority
* Validity Period
* Digital Signature

---

# Certificate Authority (CA)

A **Certificate Authority (CA)** is a trusted organization that issues digital certificates.

Examples:

* Let's Encrypt
* DigiCert
* GlobalSign
* Sectigo

Browsers trust certificates signed by recognized CAs.

---

# Public Key & Private Key

TLS uses **Asymmetric Encryption** during the handshake.

```text id="tls7"
Server

Public Key

↓

Shared Publicly

Private Key

↓

Secret
```

* Public Key encrypts data.
* Private Key decrypts data.

---

# Symmetric Encryption

After the handshake:

```text id="tls8"
Client

Session Key

⇄

Server

Session Key
```

Both use the same secret key.

Advantages:

* Much faster.
* Lower CPU usage.
* Ideal for large data transfers.

---

# Why Use Both?

TLS combines the strengths of both encryption methods.

```text id="tls9"
Handshake

↓

Asymmetric Encryption

↓

Session Key Created

↓

Symmetric Encryption

↓

Fast Secure Communication
```

---

# Digital Signatures

Digital signatures verify that the certificate was issued by a trusted Certificate Authority and has not been modified.

They provide:

* Authenticity
* Integrity

---

# TLS Versions

| Version | Status      |
| ------- | ----------- |
| SSL 2.0 | Obsolete    |
| SSL 3.0 | Obsolete    |
| TLS 1.0 | Deprecated  |
| TLS 1.1 | Deprecated  |
| TLS 1.2 | Widely Used |
| TLS 1.3 | Recommended |

TLS 1.3:

* Faster handshake
* Better security
* Reduced latency

---

# Real-World Example

Opening:

```text id="tls10"
https://www.amazon.com
```

Flow:

```text id="tls11"
Browser

↓

DNS Lookup

↓

TCP Connection

↓

TLS Handshake

↓

Encrypted HTTP Request

↓

Amazon Server

↓

Encrypted Response
```

---

# Advantages

* Encrypts communication.
* Prevents eavesdropping.
* Prevents tampering.
* Authenticates servers.
* Improves user trust.
* Required for secure web applications.

---

# Quick Revision

```text id="tls12"
TLS

↓

Handshake

↓

Certificate Verification

↓

Session Key

↓

Encrypted Communication

Security Goals

✔ Confidentiality

✔ Integrity

✔ Authentication

Encryption

Handshake

↓

Asymmetric

Communication

↓

Symmetric
```

---

# Key Takeaways

* **TLS** is the modern protocol used to secure communication over the Internet, replacing the older SSL protocol.
* It provides **Confidentiality, Integrity, and Authentication**.
* The **TLS Handshake** establishes trust and securely exchanges encryption keys.
* Digital certificates issued by trusted **Certificate Authorities (CAs)** verify server identity.
* TLS uses **asymmetric encryption** during the handshake and **symmetric encryption** for efficient data transfer.
* Modern web applications, APIs, cloud platforms, and online services rely on **TLS 1.2** and **TLS 1.3** for secure communication.

---

> **Next Topic:** `09-WebSockets.md`
