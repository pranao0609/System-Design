# Normalization

> *"Normalization is the process of organizing data in a relational database to reduce redundancy, eliminate anomalies, and improve data integrity."*

---

# Table of Contents

* What is Normalization?
* Why Do We Need Normalization?
* Data Redundancy
* Types of Anomalies
* Normal Forms
* First Normal Form (1NF)
* Second Normal Form (2NF)
* Third Normal Form (3NF)
* Boyce-Codd Normal Form (BCNF)
* Denormalization
* Advantages & Disadvantages
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is Normalization?

**Normalization** is the process of organizing database tables to:

* Reduce data redundancy
* Improve data consistency
* Eliminate unnecessary duplication
* Simplify database maintenance

The goal is to store each piece of information only once.

---

# Why Do We Need Normalization?

Consider the following table:

```text id="norm1"
StudentID | Name  | Course | Instructor

101       | Alice | DBMS   | Dr. Rao

102       | Bob   | DBMS   | Dr. Rao

103       | Carol | DBMS   | Dr. Rao
```

The instructor's name is repeated multiple times.

Problems:

* Wasted storage
* Difficult updates
* Increased chances of inconsistency

Normalization solves these issues.

---

# Data Redundancy

**Data Redundancy** means storing the same information multiple times.

Example:

```text id="norm2"
Course

DBMS

Instructor

Dr. Rao
```

If the instructor changes, every row must be updated.

---

# Types of Anomalies

Normalization removes three major anomalies.

---

## 1. Insert Anomaly

Cannot insert data without unrelated information.

Example:

Cannot add a new course until at least one student enrolls.

---

## 2. Update Anomaly

Updating duplicated information requires changing multiple rows.

Example:

```text id="norm3"
Dr. Rao

↓

Dr. Sharma
```

Every occurrence must be updated.

---

## 3. Delete Anomaly

Deleting one record accidentally removes important information.

Example:

Deleting the last student enrolled in DBMS also removes the course information.

---

# Normal Forms

Normalization is performed in stages called **Normal Forms**.

```text id="norm4"
Unnormalized Table

↓

1NF

↓

2NF

↓

3NF

↓

BCNF
```

Each level reduces redundancy further.

---

# First Normal Form (1NF)

### Rule

* Each column contains **atomic (single) values**.
* No repeating groups or arrays.

### Not in 1NF

```text id="norm5"
Student

Courses

Alice

DBMS, OS, CN
```

One column contains multiple values.

---

### In 1NF

```text id="norm6"
Student | Course

Alice   | DBMS

Alice   | OS

Alice   | CN
```

Each cell contains a single value.

---

# Second Normal Form (2NF)

### Rule

* Must already satisfy **1NF**.
* Remove **partial dependency**.

A non-key attribute should depend on the **entire primary key**, not just part of it.

Example:

```text id="norm7"
(StudentID, CourseID)

↓

CourseName depends only on CourseID
```

Move course information to a separate table.

---

# Third Normal Form (3NF)

### Rule

* Must satisfy **2NF**.
* Remove **transitive dependencies**.

Example:

```text id="norm8"
StudentID

↓

DepartmentID

↓

DepartmentName
```

DepartmentName depends on DepartmentID, not StudentID.

Store department details in a separate table.

---

# Boyce-Codd Normal Form (BCNF)

BCNF is a stricter version of 3NF.

Rule:

Every determinant must be a candidate key.

BCNF handles some dependency cases that 3NF cannot.

In most practical applications, **3NF is sufficient**, while BCNF is used for more complex schemas.

---

# Example of Normalization

### Before Normalization

```text id="norm9"
OrderID

CustomerName

CustomerCity

Product
```

Customer information is repeated for every order.

---

### After Normalization

```text id="norm10"
Customers

CustomerID

Name

City

↓

Orders

OrderID

CustomerID

Product
```

Customer data is stored only once.

---

# Denormalization

Sometimes databases intentionally introduce redundancy to improve performance.

This is called **Denormalization**.

Example:

Instead of joining multiple tables repeatedly, some frequently accessed data is duplicated.

Advantages:

* Faster reads
* Fewer joins

Disadvantages:

* More storage
* Risk of inconsistent data

Large-scale applications often combine normalization with selective denormalization.

---

# Advantages

* Reduces redundancy.
* Improves consistency.
* Eliminates anomalies.
* Saves storage.
* Simplifies maintenance.

---

# Disadvantages

* More tables.
* More JOIN operations.
* Slightly slower read performance.
* More complex queries.

---

# Real-World Example

E-commerce Database

Instead of:

```text id="norm11"
Order

Customer Name

Customer Address

Product
```

Use separate tables:

```text id="norm12"
Customers

↓

Orders

↓

Products
```

Relationships are maintained using **Foreign Keys**.

---

# Interview Questions

* What is normalization?
* Why is normalization important?
* What is data redundancy?
* Explain Insert, Update, and Delete anomalies.
* Difference between 1NF, 2NF, and 3NF?
* What is BCNF?
* What is denormalization?
* Why do large companies sometimes denormalize databases?

---

# Quick Revision

```text id="norm13"
Normalization

↓

Reduce Redundancy

↓

Remove Anomalies

↓

1NF

Atomic Values

↓

2NF

Remove Partial Dependency

↓

3NF

Remove Transitive Dependency

↓

BCNF

Every Determinant is a Candidate Key
```

---

# Key Takeaways

* **Normalization** organizes data to minimize redundancy and improve consistency.
* It eliminates **Insert**, **Update**, and **Delete anomalies**.
* **1NF** ensures atomic values, **2NF** removes partial dependencies, **3NF** removes transitive dependencies, and **BCNF** further strengthens dependency rules.
* **Denormalization** is sometimes used in large-scale systems to improve read performance by reducing expensive JOIN operations.
* A well-normalized database is easier to maintain, scales better, and ensures higher data integrity.

---

> **Next Topic:** `05-Indexes.md`
