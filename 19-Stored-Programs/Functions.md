# 🧮 SQL Functions

## 📌 Definition

A **SQL function** is a database routine that performs an operation and **returns a value**.

There are two important categories:

```text
Functions
├── Built-in Functions
└── User-Defined Functions
```

---

# 1. Built-in Functions

These are provided by the database system.

Examples:

```sql
SELECT UPPER('rahul');
```

```sql
SELECT LENGTH('Rahul');
```

```sql
SELECT COUNT(*)
FROM employees;
```

Common built-in functions include:

* String functions
* Aggregate functions
* Date functions
* Numeric functions

---

# 2. User-Defined Function

A user-defined function is created by the developer.

MySQL example:

```sql
DELIMITER //

CREATE FUNCTION get_bonus(salary DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN salary * 0.10;
END //

DELIMITER ;
```

Use it:

```sql
SELECT get_bonus(50000);
```

Result:

```text
5000
```

---

# 🔥 Function vs Stored Procedure

| Function                                         | Stored Procedure                         |
| ------------------------------------------------ | ---------------------------------------- |
| Must return a value                              | Does not have to return a value          |
| Can be used in expressions                       | Called using `CALL`                      |
| Used for calculations/logic that returns a value | Used for performing operations           |
| Can have input parameters                        | Can have `IN`, `OUT`, `INOUT` parameters |

---

# 🎯 Most Asked Interview Questions

### 1. What is a SQL function?

> A SQL function is a routine that performs an operation and returns a value.

### 2. What is the difference between function and procedure?

> A function returns a value and can be used in expressions, while a procedure is called to perform a set of operations and does not have to return a value.

### 3. What are built-in functions?

> Functions already provided by the database, such as `COUNT()`, `UPPER()`, `LENGTH()`, and date functions.

---

# 🧠 Quick Revision

```text
FUNCTION
   ↓
Performs operation
   ↓
Returns value
```

> **Memory Trick:** **Function = Return a value | Procedure = Perform operations**
