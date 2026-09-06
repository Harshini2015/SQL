# ⚙️ Stored Procedure

## 📌 Definition

A **stored procedure** is a named collection of SQL statements stored in the database and executed when called.

---

# 💻 Create Procedure

MySQL:

```sql
DELIMITER //

CREATE PROCEDURE get_employees()
BEGIN
    SELECT *
    FROM employees;
END //

DELIMITER ;
```

---

# ▶️ Execute Procedure

```sql
CALL get_employees();
```

---

# 🧩 Procedure with Parameter

```sql
DELIMITER //

CREATE PROCEDURE get_employee(IN emp_id INT)
BEGIN
    SELECT *
    FROM employees
    WHERE employee_id = emp_id;
END //

DELIMITER ;
```

Call:

```sql
CALL get_employee(101);
```

---

# 🗑️ Delete Procedure

```sql
DROP PROCEDURE get_employee;
```

---

# 🎯 Why Use Stored Procedures?

* Reuse SQL logic
* Reduce repeated SQL code
* Centralize database operations
* Can control access to underlying data

---

# 🎯 Most Asked Interview Questions

### 1. What is a stored procedure?

> A stored procedure is a named collection of SQL statements stored in the database and executed using a call.

### 2. How do you execute a stored procedure in MySQL?

```sql
CALL procedure_name();
```

### 3. Can a stored procedure accept parameters?

> Yes. It can have `IN`, `OUT`, and `INOUT` parameters.

### 4. Procedure vs normal SQL query?

> A procedure is stored in the database and can contain multiple SQL statements and control logic, while a normal query is executed directly.

---

# 🧠 Quick Revision

```text
Procedure
 ↓
Stored SQL logic
 ↓
CALL procedure_name()
```

> **Memory Trick:** **Procedure = Stored SQL Program**
