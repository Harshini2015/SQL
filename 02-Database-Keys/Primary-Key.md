# 🔑 Primary Key

## 📌 Definition

A **Primary Key** is a column (or combination of columns) that uniquely identifies each row (record) in a database table.

---

## 🔑 Key Concepts

* **Uniqueness:** No two rows can have the same primary key value.
* **NOT NULL:** A primary key column cannot contain `NULL` values.
* **Single Constraint:** A table can have **only one** primary key.
* **Automatic Index:** Most RDBMS engines automatically create a **Clustered Index** (or Unique Index) on the primary key column for fast data retrieval.

---

## 💻 Syntax

### 1. Column-Level Syntax (Single Column)
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    salary DECIMAL(10, 2)
);
```

### 2. Table-Level Syntax (Composite Primary Key)
```sql
CREATE TABLE order_items (
    order_id INT,
    product_id INT,
    quantity INT,
    PRIMARY KEY (order_id, product_id)
);
```

### 3. Adding Primary Key to Existing Table
```sql
ALTER TABLE employees
ADD CONSTRAINT pk_employee PRIMARY KEY (emp_id);
```

---

## 📝 Example

### `employees` Table

| emp_id | name  | department | salary |
| -----: | ----- | ---------- | -----: |
|    101 | Rahul | IT         |  60000 |
|    102 | Priya | HR         |  65000 |
|    103 | Amit  | Finance    |  55000 |

* `emp_id` uniquely identifies each employee.
* Attempting to insert `101` again will result in a **Duplicate entry** error.
* Attempting to insert `NULL` for `emp_id` will result in a **Column cannot be null** error.

---

## ⚖️ Important Difference: Primary Key vs Unique Key

| Feature | Primary Key | Unique Key |
| :--- | :--- | :--- |
| **Null Values** | Does NOT allow `NULL` values | Allows `NULL` values (depends on RDBMS) |
| **Limit per Table** | Only **1** Primary Key per table | Multiple Unique keys allowed per table |
| **Default Index** | Creates a **Clustered Index** (in MySQL/SQL Server) | Creates a **Non-Clustered Index** by default |
| **Purpose** | Uniquely identifies a record in table | Ensures uniqueness of non-primary values (e.g. Email) |

---

# 🎯 Most Asked Interview Questions

### 1. What is a Primary Key?
> A Primary Key is a column or set of columns that uniquely identifies each row in a table. It cannot contain `NULL` values.

---

### 2. Can a table have more than one Primary Key?
> No. A table can have only **one** Primary Key constraint. However, that primary key can be composed of multiple columns (Composite Primary Key).

---

### 3. What is the difference between Primary Key and Unique Key?
> A Primary Key uniquely identifies a record and cannot contain `NULL` values (only one allowed per table). A Unique Key prevents duplicate values but can accept `NULL` values (multiple allowed per table).

---

### 4. What type of index is created automatically on a Primary Key?
> In MySQL (InnoDB) and SQL Server, a **Clustered Index** is created automatically on the Primary Key column.

---

# 🧠 Quick Revision

```text
Primary Key
 ↓
Unique + NOT NULL
 ↓
Only 1 per table
 ↓
Creates Clustered Index
 ↓
Uniquely identifies every row
```

> **Memory Trick:** `Primary Key = UNIQUE + NOT NULL + SINGLE PER TABLE`
