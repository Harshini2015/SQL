# 🪞 SELF JOIN

## 📌 Definition

A **`SELF JOIN`** is a regular join operation in which a table is **joined with itself**. It is used to query hierarchical data or compare rows within the same table.

---

## 🔑 Key Concepts

* **Table Aliases Mandatory:** Since the query references the same table twice, **distinct aliases** (e.g. `e` for employee and `m` for manager) must be assigned to avoid ambiguity.
* **Hierarchical Relationships:** Ideal for representing tree-like or parent-child data stored in a single table (e.g., organizational charts).
* **Row Comparisons:** Used to compare rows against other rows in the same table (e.g., consecutive dates, duplicate records).

---

## 💻 Syntax

```sql
SELECT e1.column_name, e2.column_name
FROM table_name e1
JOIN table_name e2
    ON e1.common_column = e2.matching_column;
```

---

## 📝 Example: Employee & Manager Hierarchy

### `employees` Table

| emp_id | name  | manager_id | salary |
| -----: | :---- | ---------: | -----: |
|      1 | Rahul |       NULL |  90000 |
|      2 | Priya |          1 |  60000 |
|      3 | Amit  |          1 |  95000 |
|      4 | Neha  |          2 |  50000 |

### Query 1: Get Each Employee and Their Manager Name
```sql
SELECT 
    e.name AS employee_name,
    m.name AS manager_name
FROM employees e
LEFT JOIN employees m
    ON e.manager_id = m.emp_id;
```

### Output 1:

| employee_name | manager_name |
| :------------ | :----------- |
| Rahul         | **NULL**     |
| Priya         | Rahul        |
| Amit          | Rahul        |
| Neha          | Priya        |

---

### Query 2: Find Employees Earning MORE than their Manager
```sql
SELECT 
    e.name AS employee_name,
    e.salary AS emp_salary,
    m.name AS manager_name,
    m.salary AS mgr_salary
FROM employees e
JOIN employees m
    ON e.manager_id = m.emp_id
WHERE e.salary > m.salary;
```

### Output 2:

| employee_name | emp_salary | manager_name | mgr_salary |
| :------------ | ---------: | :----------- | ---------: |
| Amit          |      95000 | Rahul        |      90000 |

---

# 🎯 Most Asked Interview Questions

### 1. What is a `SELF JOIN`?
> A `SELF JOIN` is a query in which a table is joined with itself using table aliases to compare rows or analyze hierarchical relationships within the same dataset.

---

### 2. Why are table aliases mandatory in a `SELF JOIN`?
> Because the database engine needs to distinguish between the two instances of the table referenced in the query.

---

### 3. Name 3 common scenarios where `SELF JOIN` is used.
> 1. Finding employee-manager relationships.
> 2. Identifying employees who earn more than their direct managers.
> 3. Finding consecutive date records or duplicate rows within a single table.

---

# 🧠 Quick Revision

```text
Table A (as 'e')
       ↕  ON e.manager_id = m.emp_id
Table A (as 'm')
       ↓
Self-referential Hierarchy Resolved
```

> **Memory Trick:** `SELF JOIN = Mirror Table with Aliases (e vs m)`
