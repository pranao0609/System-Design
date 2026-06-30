# SQL Fundamentals

> *"SQL (Structured Query Language) is the standard language used to create, manage, and query relational databases."*

---

# Table of Contents

* What is SQL?
* What is a Relational Database?
* Database Terminology
* Tables, Rows & Columns
* Keys
* Constraints
* SQL Command Categories
* CRUD Operations
* Basic SQL Queries
* Aggregate Functions
* Sorting & Filtering
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is SQL?

**SQL (Structured Query Language)** is the standard language used to interact with **Relational Database Management Systems (RDBMS)**.

Using SQL, we can:

* Create databases
* Create tables
* Insert data
* Retrieve data
* Update records
* Delete records
* Manage permissions

Popular SQL databases:

* MySQL
* PostgreSQL
* Oracle Database
* Microsoft SQL Server
* SQLite

---

# What is a Relational Database?

A **Relational Database** stores data in the form of **tables**.

Each table consists of:

* Rows (Records)
* Columns (Attributes)

Example:

```text id="sql1"
Students Table

+----+--------+------+
| ID | Name   | Age  |
+----+--------+------+
| 1  | Alice  | 20   |
| 2  | Bob    | 21   |
| 3  | Carol  | 19   |
+----+--------+------+
```

Relationships between tables are created using **keys**.

---

# Database Terminology

| Term     | Meaning                            |
| -------- | ---------------------------------- |
| Database | Collection of tables               |
| Table    | Collection of related data         |
| Row      | Single record                      |
| Column   | Attribute of a record              |
| Schema   | Structure of the database          |
| Query    | SQL command executed on a database |

---

# Tables, Rows & Columns

```text id="sql2"
Employees

+----+----------+------------+
| ID | Name     | Department |
+----+----------+------------+
| 1  | Rahul    | HR         |
| 2  | Priya    | IT         |
| 3  | Aman     | Sales      |
+----+----------+------------+
```

* **Table** → Employees
* **Rows** → Employee records
* **Columns** → ID, Name, Department

---

# Keys

## Primary Key

A **Primary Key** uniquely identifies each row in a table.

Example:

```text id="sql3"
StudentID

101

102

103
```

Rules:

* Unique
* Cannot be NULL

---

## Foreign Key

A **Foreign Key** creates a relationship between two tables.

Example:

```text id="sql4"
Students

StudentID

↓

Enrollments

StudentID
```

It ensures **referential integrity**.

---

# Constraints

Constraints enforce rules on data.

| Constraint  | Purpose                     |
| ----------- | --------------------------- |
| PRIMARY KEY | Unique identifier           |
| FOREIGN KEY | Relationship between tables |
| UNIQUE      | No duplicate values         |
| NOT NULL    | Value required              |
| CHECK       | Custom validation           |
| DEFAULT     | Default value               |

Example:

```sql id="sql5"
Age INT CHECK (Age >= 18)
```

---

# SQL Command Categories

## DDL (Data Definition Language)

Used to define database structure.

Commands:

```sql id="sql6"
CREATE
ALTER
DROP
TRUNCATE
```

---

## DML (Data Manipulation Language)

Used to manipulate data.

Commands:

```sql id="sql7"
INSERT
UPDATE
DELETE
```

---

## DQL (Data Query Language)

Used to retrieve data.

Command:

```sql id="sql8"
SELECT
```

---

## DCL (Data Control Language)

Used for permissions.

Commands:

```sql id="sql9"
GRANT
REVOKE
```

---

## TCL (Transaction Control Language)

Used to manage transactions.

Commands:

```sql id="sql10"
COMMIT
ROLLBACK
SAVEPOINT
```

---

# CRUD Operations

CRUD represents the four basic database operations.

| Operation | SQL Command |
| --------- | ----------- |
| Create    | INSERT      |
| Read      | SELECT      |
| Update    | UPDATE      |
| Delete    | DELETE      |

---

# Basic SQL Queries

## Create Table

```sql id="sql11"
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT
);
```

---

## Insert Data

```sql id="sql12"
INSERT INTO Students
VALUES (101, 'Alice', 20);
```

---

## Retrieve Data

```sql id="sql13"
SELECT * FROM Students;
```

---

## Retrieve Specific Columns

```sql id="sql14"
SELECT Name, Age
FROM Students;
```

---

## Filter Data

```sql id="sql15"
SELECT *
FROM Students
WHERE Age > 20;
```

---

## Update Data

```sql id="sql16"
UPDATE Students
SET Age = 21
WHERE StudentID = 101;
```

---

## Delete Data

```sql id="sql17"
DELETE FROM Students
WHERE StudentID = 101;
```

---

# Aggregate Functions

Aggregate functions perform calculations on multiple rows.

| Function | Purpose       |
| -------- | ------------- |
| COUNT()  | Count rows    |
| SUM()    | Total         |
| AVG()    | Average       |
| MAX()    | Highest value |
| MIN()    | Lowest value  |

Example:

```sql id="sql18"
SELECT AVG(Age)
FROM Students;
```

---

# Sorting Data

Use **ORDER BY**.

```sql id="sql19"
SELECT *
FROM Students
ORDER BY Age ASC;
```

Descending order:

```sql id="sql20"
ORDER BY Age DESC;
```

---

# Filtering Data

Use **WHERE**.

```sql id="sql21"
SELECT *
FROM Employees
WHERE Department = 'IT';
```

---

# SQL Execution Order

Although we write SQL in one order, the database processes it differently.

```text id="sql22"
FROM

↓

WHERE

↓

GROUP BY

↓

HAVING

↓

SELECT

↓

ORDER BY

↓

LIMIT
```

Understanding this helps in writing optimized queries.

---

# Real-World Example

E-commerce Database:

```text id="sql23"
Customers

↓

Orders

↓

Products

↓

Payments
```

SQL queries retrieve and manage data across these related tables.

---

# Advantages

* Easy to learn.
* Standardized language.
* Powerful querying capabilities.
* Supports transactions.
* Works across multiple database systems.

---

# Interview Questions

* What is SQL?
* What is a relational database?
* Difference between SQL and MySQL?
* What is a Primary Key?
* What is a Foreign Key?
* What are SQL constraints?
* Difference between DELETE, TRUNCATE, and DROP?
* What are CRUD operations?
* What is the difference between DDL and DML?

---

# Quick Revision

```text id="sql24"
SQL

↓

RDBMS

↓

Tables

↓

Rows

↓

Columns

Keys

✔ Primary Key

✔ Foreign Key

Commands

DDL

DML

DQL

DCL

TCL

CRUD

Create → INSERT

Read → SELECT

Update → UPDATE

Delete → DELETE
```

---

# Key Takeaways

* **SQL** is the standard language for managing relational databases.
* Data is organized into **tables** consisting of rows and columns.
* **Primary Keys** uniquely identify records, while **Foreign Keys** establish relationships between tables.
* SQL commands are categorized into **DDL, DML, DQL, DCL, and TCL**.
* CRUD operations form the foundation of database interaction.
* SQL is an essential skill for backend development, data engineering, and system design.

---

> **Next Topic:** `02-ACID-Properties.md`
