# 🛡️ UNIQUE Constraint

## 📌 Definition

The **`UNIQUE`** constraint ensures that all values in a column (or group of columns) are **distinct** and prevents duplicate entries.

---

## 🔑 Key Concepts

* **Prevents Duplicates:** No two rows can store the same non-null value in a `UNIQUE` column.
* **Allows `NULL` Values:** In standard SQL and MySQL, a `UNIQUE` column can accept `NULL` values (and multiple `NULL`s since `NULL != NULL`).
* **Multiple Constraints:** A single table can have **multiple `UNIQUE` constraints**.
* **Automatic Index:** RDBMS engines automatically create a **Non-Clustered Index** (or Unique Index) on `UNIQUE` columns to enforce uniqueness efficiently.

---

## 💻 Syntax

### 1. Column-Level Syntax
```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    username VARCHAR(50) UNIQUE,
    email VARCHAR(100) UNIQUE
);
```

### 2. Table-Level Syntax (Composite Unique Constraint)
```sql
CREATE TABLE department_managers (
    dept_id INT,
    manager_id INT,
    CONSTRAINT uq_dept_manager UNIQUE (dept_id, manager_id)
);
```

### 3. Adding `UNIQUE` Constraint to Existing Table
```sql
ALTER TABLE users
ADD CONSTRAINT uq_email UNIQUE (email);
```

---

## 📝 Example

### `users` Table

| user_id | email | phone |
| ------: | :---- | :---- |
|       1 | rahul@domain.com | 9876543210 |
|       2 | priya@domain.com | 9123456789 |
|       3 | NULL | NULL |

* Inserting `email = 'rahul@domain.com'` again will fail with `Duplicate entry` error.
* Inserting `email = NULL` is permitted.

---

## ⚖️ Important Difference: Primary Key vs Unique Constraint

| Feature | PRIMARY KEY | UNIQUE Constraint |
| :--- | :--- | :--- |
| **Null Values** | Disallows `NULL` values completely | Allows `NULL` values |
| **Quantity per Table** | Maximum **1** per table | **Multiple** allowed per table |
| **Default Index Type** | Clustered Index (MySQL/SQL Server) | Non-Clustered Index |
| **Primary Goal** | Entity identity | Enforcing uniqueness on non-primary fields |

---

# 🎯 Most Asked Interview Questions

### 1. What is the `UNIQUE` constraint?
> The `UNIQUE` constraint prevents duplicate values in a column or set of columns, ensuring data integrity.

---

### 2. Can a column with a `UNIQUE` constraint store `NULL` values?
> Yes. In MySQL and most standard databases, a `UNIQUE` column can store `NULL` values, and it can store multiple `NULL` values because `NULL` represents an unknown value.

---

### 3. What is the difference between `UNIQUE` and `PRIMARY KEY` constraints?
> A table can have only **one** `PRIMARY KEY` (which cannot contain `NULL`s), whereas it can have **multiple** `UNIQUE` constraints (which can contain `NULL`s).

---

# 🧠 Quick Revision

```text
UNIQUE Constraint
 ↓
Guarantees distinct non-null values
 ↓
Allows NULL values
 ↓
Multiple allowed per table
 ↓
Creates Non-Clustered Index
```

> **Memory Trick:** `UNIQUE = No Duplicates Allowed (NULLs OK)`
