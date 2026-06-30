# Joins

> *"A JOIN combines rows from two or more tables based on a related column, allowing relational databases to retrieve connected data efficiently."*

---

# Table of Contents

* What is a JOIN?
* Why Do We Need JOINs?
* Types of JOINs
* INNER JOIN
* LEFT JOIN
* RIGHT JOIN
* FULL OUTER JOIN
* CROSS JOIN
* SELF JOIN
* JOIN vs UNION
* Best Practices
* Interview Questions
* Quick Revision
* Key Takeaways

---

# What is a JOIN?

A **JOIN** is an SQL operation used to combine data from multiple tables based on a common column.

Example:

Instead of storing customer and order information in one table, databases store them separately.

```text id="join1"
Customers

↓

CustomerID

↓

Orders
```

A JOIN combines these tables to retrieve meaningful information.

---

# Why Do We Need JOINs?

Consider two tables.

### Customers

```text id="join2"
+------------+--------+
| CustomerID | Name   |
+------------+--------+
| 1          | Alice  |
| 2          | Bob    |
| 3          | Carol  |
+------------+--------+
```

### Orders

```text id="join3"
+---------+------------+--------+
| OrderID | CustomerID | Amount |
+---------+------------+--------+
| 101     | 1          | 500    |
| 102     | 2          | 800    |
| 103     | 1          | 300    |
+---------+------------+--------+
```

To display:

```text
Alice → ₹500
Alice → ₹300
Bob   → ₹800
```

we use a JOIN.

---

# Types of JOINs

```text id="join4"
JOIN

├── INNER JOIN

├── LEFT JOIN

├── RIGHT JOIN

├── FULL OUTER JOIN

├── CROSS JOIN

└── SELF JOIN
```

---

# INNER JOIN

Returns only the rows that exist in **both** tables.

```sql id="join5"
SELECT *
FROM Customers
INNER JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

Visualization:

```text id="join6"
Customers  ∩  Orders
```

Only matching records are returned.

---

# LEFT JOIN

Returns:

* All rows from the **left table**
* Matching rows from the right table

If no match exists, NULL values are returned.

```sql id="join7"
SELECT *
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

Visualization:

```text id="join8"
Customers

◯──────────◯

Orders

Return Entire Left Circle
```

---

# RIGHT JOIN

Returns:

* All rows from the **right table**
* Matching rows from the left table

```sql id="join9"
SELECT *
FROM Customers
RIGHT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

Visualization:

```text id="join10"
Customers

◯──────────◯

Orders

Return Entire Right Circle
```

---

# FULL OUTER JOIN

Returns:

* All rows from both tables
* Matching rows where available
* NULL where no match exists

```sql id="join11"
SELECT *
FROM Customers
FULL OUTER JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

Visualization:

```text id="join12"
Customers ∪ Orders
```

Not supported directly in MySQL (can be simulated using `UNION`).

---

# CROSS JOIN

Returns the **Cartesian Product** of two tables.

Every row from the first table is combined with every row from the second table.

```sql id="join13"
SELECT *
FROM Customers
CROSS JOIN Products;
```

Example:

3 Customers × 5 Products = 15 Rows

---

# SELF JOIN

A table is joined with itself.

Useful for hierarchical data.

Example:

Employees and Managers.

```text id="join14"
Employee

↓

ManagerID

↓

Employee
```

Query:

```sql id="join15"
SELECT e.Name, m.Name AS Manager
FROM Employees e
JOIN Employees m
ON e.ManagerID = m.EmployeeID;
```

---

# Visual Comparison

```text id="join16"
INNER

Only Matching Rows

LEFT

All Left + Matching Right

RIGHT

All Right + Matching Left

FULL

All Rows from Both

CROSS

Every Combination

SELF

Table Joined with Itself
```

---

# JOIN vs UNION

| JOIN                 | UNION                           |
| -------------------- | ------------------------------- |
| Combines Columns     | Combines Rows                   |
| Uses Related Columns | Requires Same Number of Columns |
| Multiple Tables      | Similar Queries                 |
| Horizontal Merge     | Vertical Merge                  |

---

# Real-World Example

E-commerce Database

```text id="join17"
Customers

↓

Orders

↓

Products

↓

Payments
```

Retrieve:

* Customer Name
* Product Name
* Payment Status

using multiple JOINs.

---

# Best Practices

* Join using indexed columns.
* Avoid unnecessary JOINs.
* Use aliases for readability.
* Select only required columns.
* Prefer INNER JOIN when unmatched rows are not needed.
* Analyze execution plans for complex JOIN queries.

---

# Interview Questions

* What is a JOIN?
* Difference between INNER and LEFT JOIN?
* Difference between LEFT and RIGHT JOIN?
* What is FULL OUTER JOIN?
* What is CROSS JOIN?
* What is SELF JOIN?
* Difference between JOIN and UNION?
* Which JOIN is used most frequently?
* How do indexes improve JOIN performance?

---

# Quick Revision

```text id="join18"
JOIN

↓

Combine Tables

Types

✔ INNER

✔ LEFT

✔ RIGHT

✔ FULL

✔ CROSS

✔ SELF

INNER

↓

Matching Rows

LEFT

↓

All Left Rows

RIGHT

↓

All Right Rows

FULL

↓

All Rows

CROSS

↓

Cartesian Product

SELF

↓

Same Table
```

---

# Key Takeaways

* A **JOIN** combines related data from multiple tables using a common column.
* **INNER JOIN** returns only matching rows.
* **LEFT JOIN** and **RIGHT JOIN** include all rows from one table and matching rows from the other.
* **FULL OUTER JOIN** returns all rows from both tables, while **CROSS JOIN** returns every possible combination.
* **SELF JOIN** is useful for hierarchical relationships such as employee-manager structures.
* Efficient JOIN operations, supported by proper indexing, are fundamental to designing high-performance relational databases.

---

> **Next Topic:** `07-Query-Optimization.md`
