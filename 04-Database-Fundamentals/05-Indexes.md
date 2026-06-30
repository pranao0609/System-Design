# Indexes

> *"An index is a data structure that improves the speed of data retrieval operations by allowing the database to locate records without scanning the entire table."*

---

# Table of Contents

* What is an Index?
* Why Do We Need Indexes?
* How an Index Works
* Types of Indexes
* Clustered vs Non-Clustered Index
* Composite Index
* Unique Index
* When to Use Indexes
* Advantages & Disadvantages
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is an Index?

An **Index** is a special data structure created on one or more columns of a table to speed up data retrieval.

Without an index, the database performs a **Full Table Scan**, checking every row until it finds the required data.

With an index, the database can directly locate the required records.

Think of it like the **index of a book**. Instead of reading every page, you jump directly to the page containing the topic.

---

# Why Do We Need Indexes?

Consider a table containing **10 million users**.

Query:

```sql id="idx1"
SELECT * FROM Users
WHERE Email = 'alice@example.com';
```

Without an index:

```text id="idx2"
Database

↓

Check Row 1

↓

Check Row 2

↓

Check Row 3

↓

...

↓

Check Row 10,000,000
```

Time Complexity:

```text id="idx3"
O(n)
```

---

With an index:

```text id="idx4"
Database

↓

Index

↓

Directly Find Record
```

Time Complexity (typically B+ Tree):

```text id="idx5"
O(log n)
```

---

# How an Index Works

Most relational databases implement indexes using a **B+ Tree**.

Example:

```text id="idx6"
             50
          /      \
       20          80
     /   \       /    \
   10    30    60     90
```

Instead of checking every row, the database traverses the tree to find the required value efficiently.

Some databases also support **Hash Indexes**, which are optimized for equality lookups.

---

# Types of Indexes

## 1. Primary Index

Created automatically for the **Primary Key**.

Properties:

* Unique
* Cannot contain NULL values
* Only one per table

Example:

```text id="idx7"
StudentID

101

102

103
```

---

## 2. Unique Index

Ensures that duplicate values are not allowed.

Example:

```text id="idx8"
Email

alice@example.com

bob@example.com
```

Each email address must be unique.

---

## 3. Composite Index

An index built on **multiple columns**.

Example:

```sql id="idx9"
CREATE INDEX idx_name
ON Employees (Department, Salary);
```

Useful when queries frequently filter on both columns.

---

## 4. Full-Text Index

Designed for searching large text fields.

Example:

* Articles
* Blogs
* Product Descriptions

Instead of exact matches, it supports keyword searches.

---

# Clustered vs Non-Clustered Index

## Clustered Index

A **Clustered Index** determines the physical order of rows in a table.

Characteristics:

* Data is stored in index order.
* Only **one clustered index** per table.

Example:

```text id="idx10"
1

2

3

4

5
```

Rows are physically ordered.

---

## Non-Clustered Index

A **Non-Clustered Index** stores pointers to the actual data.

```text id="idx11"
Index

↓

Pointer

↓

Actual Row
```

Characteristics:

* Multiple non-clustered indexes can exist.
* Does not change the physical order of the table.

---

# Composite Index Example

Table:

```text id="idx12"
Employees

Department

Salary
```

Index:

```sql id="idx13"
CREATE INDEX idx_emp
ON Employees (Department, Salary);
```

Query:

```sql id="idx14"
SELECT *
FROM Employees
WHERE Department = 'IT'
AND Salary > 70000;
```

This query benefits greatly from the composite index.

---

# When Should You Create an Index?

Create indexes on:

* Primary Keys
* Foreign Keys
* Frequently searched columns
* Columns used in `WHERE`
* Columns used in `JOIN`
* Columns used in `ORDER BY`
* Columns used in `GROUP BY`

---

# When Should You Avoid Indexes?

Avoid indexing:

* Small tables
* Frequently updated columns
* Columns with very low uniqueness (e.g., Gender)
* Temporary tables

Too many indexes increase write overhead.

---

# Advantages

* Faster SELECT queries.
* Improved JOIN performance.
* Faster sorting.
* Faster filtering.
* Reduced query execution time.

---

# Disadvantages

* Extra storage required.
* Slower INSERT operations.
* Slower UPDATE operations.
* Slower DELETE operations.
* Increased maintenance cost.

---

# Real-World Example

Suppose an e-commerce platform searches products by SKU.

Without an index:

```text id="idx15"
Search

↓

Scan Millions of Products
```

With an index:

```text id="idx16"
Search

↓

Index

↓

Product Found Immediately
```

Large platforms like Amazon, Flipkart, and eBay rely heavily on indexes for fast product searches.

---

# Interview Questions

* What is an index?
* Why do databases use indexes?
* Difference between clustered and non-clustered indexes?
* What is a composite index?
* What is a unique index?
* Why do indexes improve query performance?
* What are the disadvantages of indexes?
* Which data structure is commonly used to implement indexes?

---

# Quick Revision

```text id="idx17"
Indexes

↓

Speed Up Queries

↓

B+ Tree

Types

✔ Primary

✔ Unique

✔ Composite

✔ Full-Text

Clustered

↓

Data Stored in Index Order

Non-Clustered

↓

Stores Pointers

Benefits

✔ Faster SELECT

✔ Faster JOIN

✔ Faster ORDER BY
```

---

# Key Takeaways

* An **Index** is a data structure that accelerates data retrieval by avoiding full table scans.
* Most relational databases implement indexes using **B+ Trees**.
* Common index types include **Primary**, **Unique**, **Composite**, and **Full-Text** indexes.
* **Clustered indexes** determine the physical order of data, while **Non-Clustered indexes** store pointers to rows.
* Indexes significantly improve **SELECT**, **JOIN**, and **ORDER BY** performance but increase storage usage and slow down write operations.
* Proper indexing is one of the most important techniques for optimizing database performance.

---

> **Next Topic:** `06-Joins.md`
