# 🚫 NOT NULL Constraint

## 📌 Definition

The **`NOT NULL`** constraint enforces a rule that a column **cannot store `NULL` (unknown or missing) values**.

---

## 🔑 Key Concepts

* **Mandatory Field:** Forces a column to always contain a valid value when inserting or updating records.
* **Column-Level Constraint:** Specified at column creation or altered later.
* **Default Behavior:** In SQL, columns allow `NULL` values by default unless explicitly defined as `NOT NULL`.

---

## 💻 Syntax

### 1. Specifying `NOT NULL` on Table Creation
```sql
CREATE TABLE employees (
    emp_id INT NOT NULL,
    name VARCHAR(50) NOT NULL,
    salary DECIMAL(10, 2) -- Allows NULL by default
);
```

### 2. Adding `NOT NULL` to Existing Column (MySQL)
```sql
ALTER TABLE employees
MODIFY salary DECIMAL(10, 2) NOT NULL;
```

### 3. Removing `NOT NULL` Constraint (MySQL)
```sql
ALTER TABLE employees
MODIFY salary DECIMAL(10, 2) NULL;
```

---

## 📝 Example

### `employees` Table

| emp_id | name  | phone |
| -----: | :---- | :---- |
|    101 | Rahul | 9876543210 |
|    102 | Priya | NULL |

* Attempting to run:
```sql
INSERT INTO employees (emp_id, name) VALUES (103, NULL);
```
Will cause an error: `Error: Column 'name' cannot be null`.

---

## ⚖️ Important Difference: NULL vs Empty String vs Zero

| Value | Meaning | Datatype | Storage |
| :--- | :--- | :--- | :--- |
| **`NULL`** | Missing / Unknown value | N/A | No memory / Special bit marker |
| **`""` (Empty String)** | Known text of zero length | String | 0 bytes content |
| **`0`** | Numerical zero | Numeric | Numeric value 0 |

---

# 🎯 Most Asked Interview Questions

### 1. What does the `NOT NULL` constraint do?
> The `NOT NULL` constraint ensures that a column must always have a value when a new row is inserted or an existing row is updated.

---

### 2. How do you check if a field contains `NULL` in SQL?
> Use `WHERE column_name IS NULL` (or `IS NOT NULL`). You cannot use `= NULL` because `NULL = NULL` evaluates to `UNKNOWN` in SQL.

---

### 3. Is `NULL` equivalent to 0 or an empty string?
> No. `NULL` means absence of a value (unknown/unassigned), whereas `0` is a number and `""` is a string of length zero.

---

# 🧠 Quick Revision

```text
NOT NULL Constraint
 ↓
Disallows missing/unknown values
 ↓
Forces user to supply a value
 ↓
Check with: WHERE col IS NULL / IS NOT NULL
```

> **Memory Trick:** `NOT NULL = Value Required!`
