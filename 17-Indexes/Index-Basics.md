# ⚡ Index Basics

## 📌 Definition

An **Index** is a performance-tuning data structure (typically a **B-Tree** or B+ Tree) created on table columns to **dramatically speed up data retrieval queries (`SELECT`)**, similar to an index at the back of a textbook.

---

## 🔑 Key Concepts

* **Search Performance:** Converts a slow **Full Table Scan ($O(N)$)** into a fast **B-Tree Lookup ($O(\log N)$)**.
* **The Trade-Off (Read vs Write):**
  * **Faster Reads:** Accelerates `SELECT`, `WHERE`, `JOIN`, `ORDER BY`, and `GROUP BY` operations.
  * **Slower Writes:** Slightly slows down `INSERT`, `UPDATE`, and `DELETE` operations because the database must update index trees whenever data changes.
* **Storage Overhead:** Indexes consume extra disk and memory space.

---

## 💻 Syntax

### 1. Creating a Basic B-Tree Index
```sql
CREATE INDEX idx_emp_salary ON employees(salary);
```

### 2. Dropping an Index (MySQL)
```sql
ALTER TABLE employees DROP INDEX idx_emp_salary;
```

---

## 🏗️ B-Tree Index Structure

```text
               [ Root Node (Salary 50k) ]
                      /         \
   [ Branch: < 50k ]               [ Branch: >= 50k ]
       /       \                       /        \
  [10k, 30k]  [40k]              [50k, 70k]   [90k, 100k]  <-- Leaf Nodes
```

---

# 🎯 Most Asked Interview Questions

### 1. What is a database index and how does it improve query speed?
> An index is a B-Tree data structure pointing to table row locations. It allows the database to find target rows in $O(\log N)$ logarithmic time rather than scanning every row sequentially ($O(N)$).

---

### 2. What is the main trade-off of adding indexes to a database?
> Indexes speed up `SELECT` read operations, but they consume extra disk storage space and degrade `INSERT`, `UPDATE`, and `DELETE` write performance because indexes must be updated continuously.

---

### 3. What internal data structure is most commonly used for database indexes?
> **B-Tree** (or B+ Tree) structures.

---

# 🧠 Quick Revision

```text
Without Index → Full Table Scan O(N) (Slow)
With Index    → B-Tree Search O(log N) (Fast)

Tradeoff: Fast Reads ⚡ vs Slower Writes 🐢 + Extra Storage 💾
```

> **Memory Trick:** `Index = Textbook index for fast lookups`
