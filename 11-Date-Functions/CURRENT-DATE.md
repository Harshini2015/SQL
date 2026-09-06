# 📅 CURRENT-DATE & NOW Functions

## 📌 Definition

The **`CURRENT_DATE`** and **`NOW()`** functions return the current system date and time from the database server.

---

## 🔑 Dialect Comparisons

| Function | Returns | Database Engine |
| :--- | :--- | :--- |
| **`CURRENT_DATE`** / **`CURDATE()`** | Date only (`YYYY-MM-DD`) | MySQL, PostgreSQL |
| **`NOW()`** / **`CURRENT_TIMESTAMP`** | Date and Time (`YYYY-MM-DD HH:MM:SS`) | MySQL, PostgreSQL |
| **`GETDATE()`** | Date and Time | SQL Server |
| **`SYSDATE`** | Date and Time | Oracle |

---

## 💻 Syntax & Examples (MySQL)

```sql
-- Returns current date: '2025-01-15'
SELECT CURDATE(), CURRENT_DATE;

-- Returns current date and time: '2025-01-15 14:30:00'
SELECT NOW(), CURRENT_TIMESTAMP;
```

---

## 📝 Example Query

Find orders placed **today**:

```sql
SELECT * FROM orders
WHERE DATE(order_date) = CURRENT_DATE;
```

---

# 🎯 Most Asked Interview Questions

### 1. What is the difference between `CURDATE()` and `NOW()` in MySQL?
> `CURDATE()` returns only the current date (`YYYY-MM-DD`), whereas `NOW()` returns both current date and time (`YYYY-MM-DD HH:MM:SS`).

---

### 2. How do you get the current date and time in SQL Server?
> In SQL Server, use `GETDATE()`.

---

### 3. How do you get the current date and time in Oracle?
> In Oracle, use `SYSDATE` or `CURRENT_TIMESTAMP`.

---

# 🧠 Quick Revision

```text
Current Date & Time Functions
 ├── MySQL: CURDATE() (Date) | NOW() (Date + Time)
 ├── SQL Server: GETDATE()
 └── Oracle: SYSDATE
```

> **Memory Trick:** `CURDATE = Date Only | NOW = Date + Time`
