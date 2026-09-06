# ✅ CHECK Constraint

## 📌 Definition

The **`CHECK`** constraint limits the range or domain of values that can be inserted or updated in a column.

---

## 🔑 Key Concepts

* **Boolean Condition:** Evaluates a logical expression (`TRUE`, `FALSE`, or `UNKNOWN`) for every inserted or updated row.
* **Rejection:** If the condition evaluates to `FALSE`, the transaction fails and the database rejects the row.
* **Allows NULL:** If a column contains `NULL`, `CHECK` constraints generally evaluate to `UNKNOWN` and pass (do not block the row), unless combined with `NOT NULL`.
* **MySQL Support:** Supported and enforced in **MySQL 8.0+** (ignored in MySQL 5.7 and earlier).

---

## 💻 Syntax

### 1. Column-Level CHECK Constraint
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INT CHECK (age >= 18),
    salary DECIMAL(10, 2) CHECK (salary > 0)
);
```

### 2. Table-Level Named CHECK Constraint
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    age INT,
    experience_years INT,
    CONSTRAINT chk_emp_age_exp CHECK (age >= 18 AND experience_years <= age - 18)
);
```

### 3. Adding CHECK Constraint to Existing Table
```sql
ALTER TABLE employees
ADD CONSTRAINT chk_salary CHECK (salary >= 10000);
```

### 4. Dropping a CHECK Constraint (MySQL 8.0+)
```sql
ALTER TABLE employees
DROP CHECK chk_salary;
```

---

## 📝 Example

### `students` Table

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    grade CHAR(1) CHECK (grade IN ('A', 'B', 'C', 'D', 'F'))
);
```

* Inserting `grade = 'A'` -> Allowed.
* Inserting `grade = 'Z'` -> Fails with constraint violation error.

---

# 🎯 Most Asked Interview Questions

### 1. What is the `CHECK` constraint used for?
> The `CHECK` constraint is used to restrict the values stored in a column by evaluating a boolean expression before saving the data.

---

### 2. Does a `CHECK` constraint block `NULL` values?
> No. A `CHECK` constraint evaluates `NULL` expressions to `UNKNOWN`, which passes the check. To block `NULL`s, combine it with a `NOT NULL` constraint.

---

### 3. Does MySQL support `CHECK` constraints?
> MySQL supports and enforces `CHECK` constraints starting from **MySQL 8.0.16**. In older versions (like 5.7), MySQL parsed `CHECK` syntax but silently ignored it.

---

# 🧠 Quick Revision

```text
CHECK Constraint
 ↓
Validates column values using logical condition
 ↓
Blocks operation if condition evaluates to FALSE
 ↓
Enforced in MySQL 8.0+
```

> **Memory Trick:** `CHECK = Custom Validation Rule`
