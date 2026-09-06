# 🔑 PRIMARY KEY Constraint

## 📌 Definition

The **`PRIMARY KEY` constraint** uniquely identifies each row in a table. It is a combination of `NOT NULL` and `UNIQUE` constraints.

*(For detailed key concepts and theory, see [Primary-Key.md](../02-Database-Keys/Primary-Key.md))*

---

## 🔑 Key Constraint Rules

* **Uniqueness:** Ensures no duplicate values exist in the column(s).
* **Non-Null:** Automatically prohibits `NULL` values.
* **Single Constraint:** Only **1** `PRIMARY KEY` constraint is permitted per table.

---

## 💻 Syntax & Constraint Declaration

### 1. Column-Level Constraint
```sql
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50) NOT NULL
);
```

### 2. Table-Level Named Constraint
```sql
CREATE TABLE departments (
    dept_id INT,
    dept_name VARCHAR(50) NOT NULL,
    CONSTRAINT pk_departments PRIMARY KEY (dept_id)
);
```

### 3. Adding Primary Key Constraint to Existing Table
```sql
ALTER TABLE departments
ADD CONSTRAINT pk_departments PRIMARY KEY (dept_id);
```

### 4. Dropping a Primary Key Constraint
```sql
-- MySQL Syntax
ALTER TABLE departments
DROP PRIMARY KEY;
```

---

## 📝 Example

```sql
CREATE TABLE accounts (
    account_no INT,
    branch_code VARCHAR(10),
    balance DECIMAL(12, 2),
    CONSTRAINT pk_account PRIMARY KEY (account_no, branch_code)
);
```

* `pk_account` is a composite primary key constraint enforcing uniqueness on `(account_no, branch_code)`.

---

# 🎯 Most Asked Interview Questions

### 1. How does SQL enforce a Primary Key?
> SQL enforces a Primary Key by implicitly combining a `UNIQUE` index and `NOT NULL` constraints on the designated column(s).

---

### 2. How do you drop a Primary Key constraint in MySQL?
> In MySQL, use `ALTER TABLE table_name DROP PRIMARY KEY;`.

---

### 3. Why can a table have only one Primary Key constraint?
> Because a Primary Key defines the logical entity identity and determines the physical layout of data (Clustered Index order) in databases like MySQL InnoDB.

---

# 🧠 Quick Revision

```text
PRIMARY KEY Constraint
 ↓
UNIQUE + NOT NULL
 ↓
Only 1 per table
 ↓
Drop with: ALTER TABLE tbl DROP PRIMARY KEY;
```
