# ⚖️ Normalization vs Denormalization

## 📌 Overview

* **Normalization:** The process of organizing table schemas to **eliminate data redundancy** and ensure **data integrity** by splitting tables into smaller, linked entities.
* **Denormalization:** The intentional strategy of **adding redundant data** or combining tables to **optimize read performance** and reduce complex joins.

---

## ⚖️ Detailed Comparison

| Feature | Normalization | Denormalization |
| :--- | :--- | :--- |
| **Primary Goal** | Minimize data redundancy & maintain integrity | Maximize read performance & query speed |
| **Target System** | **OLTP** (Online Transaction Processing - Web Apps) | **OLAP** (Online Analytical Processing - Data Warehouses) |
| **Data Integrity** | **High** (Enforced via constraints) | Risk of inconsistencies (Requires custom sync logic) |
| **Read Speed** | Slower (Requires multiple `JOIN` operations) | **Faster** (Pre-joined tables, fewer `JOIN`s) |
| **Write Speed** | **Faster** (Inserts/Updates modify single rows) | Slower (Updates must propagate to redundant columns) |
| **Storage Space** | Lower (No redundant data) | Higher (Redundant data stored) |

---

# 🎯 Most Asked Interview Questions

### 1. What is the main purpose of normalization?
> Normalization minimizes data redundancy, prevents database anomalies (Insert, Update, Delete anomalies), and enforces data integrity in transactional databases.

---

### 2. When would you intentionally choose to denormalize a database?
> In reporting systems or data warehouses (OLAP) where fast read query performance is critical, and joining large tables produces severe performance bottlenecks.

---

### 3. What type of database system uses normalization vs denormalization?
> * **OLTP** (Transactional web applications) uses **Normalized** databases.
> * **OLAP** (Data Warehouses / Analytics) uses **Denormalized** databases (e.g. Star Schema, Snowflake Schema).

---

# 🧠 Quick Revision

```text
Normalization   → Eliminate Redundancy → Fast Writes → OLTP
Denormalization → Add Redundancy       → Fast Reads  → OLAP
```

> **Memory Trick:** `Normalization = Clean Data (OLTP) | Denormalization = Fast Reads (OLAP)`
