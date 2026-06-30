# NoSQL Databases

> *"NoSQL databases are non-relational databases designed to handle large volumes of unstructured or semi-structured data while providing high scalability, flexibility, and availability."*

---

# Table of Contents

* What is NoSQL?
* Why Do We Need NoSQL?
* SQL vs NoSQL
* Types of NoSQL Databases
* Document Databases
* Key-Value Databases
* Column-Family Databases
* Graph Databases
* When to Use NoSQL
* Popular NoSQL Databases
* Advantages & Disadvantages
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is NoSQL?

**NoSQL (Not Only SQL)** refers to a class of databases that do not rely on the traditional relational table model.

Unlike SQL databases, NoSQL databases:

* Store flexible data structures.
* Scale horizontally.
* Handle massive datasets efficiently.
* Support distributed architectures.

NoSQL databases are widely used in:

* Social Media
* E-commerce
* IoT
* Big Data
* Real-Time Analytics
* Cloud Applications

---

# Why Do We Need NoSQL?

Traditional SQL databases work well for structured data but can become difficult to scale for modern applications.

Example:

A social media application stores:

* User Profiles
* Posts
* Comments
* Likes
* Images
* Videos

Each user may have different data.

A flexible schema is more suitable than fixed relational tables.

---

# SQL vs NoSQL

| SQL              | NoSQL                |
| ---------------- | -------------------- |
| Relational       | Non-Relational       |
| Fixed Schema     | Flexible Schema      |
| Tables           | Multiple Data Models |
| Vertical Scaling | Horizontal Scaling   |
| ACID Focus       | BASE Focus           |
| JOIN Support     | Limited or No JOINs  |

---

# Types of NoSQL Databases

```text id="nosql1"
NoSQL

├── Document Database

├── Key-Value Database

├── Column-Family Database

└── Graph Database
```

---

# 1. Document Database

Stores data as **documents**, usually in JSON or BSON format.

Example:

```json id="nosql2"
{
  "id": 101,
  "name": "Alice",
  "skills": [
    "Python",
    "SQL"
  ]
}
```

Characteristics:

* Flexible schema
* Nested data
* Easy to store complex objects

Popular Databases:

* MongoDB
* CouchDB
* Firebase Firestore

Use Cases:

* User Profiles
* Product Catalogs
* Content Management Systems

---

# 2. Key-Value Database

Stores data as simple **key-value pairs**.

Example:

```text id="nosql3"
Key

User101

↓

Value

{Name: Alice}
```

Characteristics:

* Extremely fast
* Simple lookups
* Ideal for caching

Popular Databases:

* Redis
* Amazon DynamoDB
* Riak

Use Cases:

* Session Storage
* Cache
* Shopping Cart
* Leaderboards

---

# 3. Column-Family Database

Stores data in **column families** instead of rows.

Unlike SQL, each row can have different columns.

Example:

```text id="nosql4"
UserID

↓

Name

↓

Email

↓

Phone
```

Characteristics:

* Optimized for large-scale data.
* Efficient for analytics.
* Excellent write performance.

Popular Databases:

* Apache Cassandra
* Apache HBase
* Google Bigtable

Use Cases:

* Time-Series Data
* IoT
* Analytics
* Logging Systems

---

# 4. Graph Database

Stores data as **Nodes** and **Relationships**.

Example:

```text id="nosql5"
Alice

↓

Friend

↓

Bob

↓

Friend

↓

Carol
```

Characteristics:

* Optimized for relationship-heavy data.
* Fast graph traversals.

Popular Databases:

* Neo4j
* Amazon Neptune
* ArangoDB

Use Cases:

* Social Networks
* Recommendation Engines
* Fraud Detection
* Knowledge Graphs

---

# When to Use NoSQL

Choose NoSQL when:

* Data schema changes frequently.
* Massive scalability is required.
* High write throughput is important.
* Data is semi-structured or unstructured.
* Distributed architecture is needed.

---

# Popular NoSQL Databases

| Database  | Type          |
| --------- | ------------- |
| MongoDB   | Document      |
| Redis     | Key-Value     |
| Cassandra | Column-Family |
| HBase     | Column-Family |
| DynamoDB  | Key-Value     |
| Neo4j     | Graph         |
| CouchDB   | Document      |

---

# Advantages

* Horizontal scalability.
* Flexible schema.
* High availability.
* High write performance.
* Handles large datasets efficiently.

---

# Disadvantages

* Limited JOIN support.
* Eventual consistency in many systems.
* Less standardized than SQL.
* Complex transactions may be difficult.

---

# Real-World Examples

## Netflix

Uses NoSQL databases for user activity, recommendations, and streaming metadata.

---

## Facebook

Stores social relationships using graph-like data models.

---

## Amazon

Uses DynamoDB for shopping carts and session management.

---

## Redis

Commonly used for:

* Cache
* Session Storage
* Rate Limiting

---

# Interview Questions

* What is NoSQL?
* Why do we need NoSQL?
* Difference between SQL and NoSQL?
* What are the four types of NoSQL databases?
* When should you choose MongoDB?
* What is Redis used for?
* When would you use a Graph Database?
* Why are NoSQL databases horizontally scalable?

---

# Quick Revision

```text id="nosql6"
NoSQL

↓

Flexible Schema

↓

Horizontal Scaling

Types

✔ Document

✔ Key-Value

✔ Column-Family

✔ Graph

Popular

MongoDB

Redis

Cassandra

Neo4j

Best For

✔ Big Data

✔ Cloud

✔ Real-Time Apps

✔ Distributed Systems
```

---

# Key Takeaways

* **NoSQL databases** are non-relational databases designed for scalability, flexibility, and high availability.
* The four primary NoSQL models are **Document**, **Key-Value**, **Column-Family**, and **Graph** databases.
* NoSQL databases are well suited for applications with large volumes of unstructured or rapidly changing data.
* Compared to SQL databases, NoSQL systems typically favor **horizontal scaling** and flexible schemas over strict relational constraints.
* Choosing the right NoSQL database depends on the application's data model, access patterns, and scalability requirements.

---

> **Next Topic:** `10-CAP-Theorem.md`
