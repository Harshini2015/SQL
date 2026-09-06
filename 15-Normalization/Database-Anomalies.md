# ⚠️ Database Anomalies

## 📌 Definition

**Database Anomalies** are data inconsistencies or errors that occur in un-normalized databases when performing data modification operations (`INSERT`, `UPDATE`, `DELETE`).

---

## 🔑 The 3 Types of Database Anomalies

### 1. Insertion Anomaly
* **Problem:** Occurs when you **cannot insert valid data** about one entity without being forced to insert unrelated data about another entity.
* **Example:** You cannot create a new department unless at least one employee is assigned to it (because `emp_id` is part of the primary key).

---

### 2. Deletion Anomaly
* **Problem:** Occurs when deleting a record unintentionally **causes the permanent loss of other completely unrelated essential data**.
* **Example:** Deleting the last employee in a department unintentionally deletes all historical records of the department itself.

---

### 3. Update (Modification) Anomaly
* **Problem:** Occurs when duplicate data exists across multiple rows, and updating data in one place leaves other identical entries unchanged, creating **data inconsistency**.
* **Example:** If a department name changes from 'HR' to 'Human Resources', but you only update 5 out of 10 employee rows, the database becomes inconsistent.

---

# 🎯 Most Asked Interview Questions

### 1. What are database anomalies and why do they occur?
> Database anomalies are data inconsistencies that occur during `INSERT`, `UPDATE`, or `DELETE` operations due to poor table design and data redundancy in un-normalized databases.

---

### 2. How does database normalization prevent anomalies?
> Normalization decomposes large un-normalized tables into separate entity tables linked by foreign keys, ensuring each piece of data is stored in exactly one place.

---

# 🧠 Quick Revision

```text
Database Anomalies (In Un-normalized Tables)
 ├── Insertion Anomaly → Cannot add record without dummy data
 ├── Deletion Anomaly  → Deleting record loses unrelated data
 └── Update Anomaly    → Partial update causes data inconsistency
```

> **Memory Trick:** `Normalization fixes Insertion, Deletion, and Update Anomalies!`
