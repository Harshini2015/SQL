# ⌛ DATEDIFF Function

## 📌 Definition

The **`DATEDIFF()`** function calculates the difference (number of days, months, or years) between two date expressions.

---

## 🔑 Dialect Differences (Crucial for Interviews!)

### 1. MySQL `DATEDIFF(expr1, expr2)`
* Calculates $\mathbf{expr1 - expr2}$ in **days**.
* Syntax: `DATEDIFF(end_date, start_date)`
* Example: `DATEDIFF('2025-01-10', '2025-01-01')` returns **`9`**.

### 2. SQL Server `DATEDIFF(unit, startdate, enddate)`
* Requires a unit parameter (`DAY`, `MONTH`, `YEAR`, `HOUR`).
* Syntax: `DATEDIFF(DAY, '2025-01-01', '2025-01-10')` returns **`9`**.

---

## 💻 Syntax & Examples (MySQL)

```sql
-- Calculate employee tenure in days
SELECT 
    name, 
    DATEDIFF(CURRENT_DATE, hire_date) AS days_employed
FROM employees;
```

---

## 📝 Consecutive Date Problem (LeetCode Pattern)

Find weather records where the temperature was higher than the previous day:

```sql
SELECT w1.id
FROM Weather w1
JOIN Weather w2
    ON DATEDIFF(w1.recordDate, w2.recordDate) = 1
WHERE w1.temperature > w2.temperature;
```

---

# 🎯 Most Asked Interview Questions

### 1. How does `DATEDIFF()` work in MySQL vs SQL Server?
> In MySQL, `DATEDIFF(end, start)` returns the difference in **days** without specifying a unit. In SQL Server, `DATEDIFF(unit, start, end)` takes 3 arguments including the datepart unit (`DAY`, `MONTH`, `YEAR`).

---

### 2. What does `DATEDIFF('2025-01-01', '2025-01-05')` return in MySQL?
> It returns **`-4`** (because the first date is earlier than the second date).

---

# 🧠 Quick Revision

```text
DATEDIFF Function
 ├── MySQL: DATEDIFF(date1, date2) → Returns (date1 - date2) in DAYS
 └── SQL Server: DATEDIFF(DAY, start, end)
```

> **Memory Trick:** `MySQL DATEDIFF(date1, date2) = date1 - date2 in DAYS`
