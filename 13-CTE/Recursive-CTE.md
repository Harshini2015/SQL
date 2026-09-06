# 🔄 Recursive CTE

## 📌 Definition

A **Recursive CTE** is a Common Table Expression that **references itself**. It is used to query hierarchical data structures (like manager-employee trees or category trees) or generate sequential series of values.

---

## 🔑 Core Anatomy of a Recursive CTE

A Recursive CTE consists of 3 essential parts:
1. **Anchor Member:** Initial base query that executes first and establishes the starting result set.
2. **`UNION ALL`:** Operator combining the anchor and recursive results.
3. **Recursive Member:** Query that references the CTE name itself, combined with a **termination condition** to prevent infinite loops.

---

## 💻 Syntax (MySQL 8.0+)

```sql
WITH RECURSIVE cte_name AS (
    -- 1. Anchor Member
    SELECT initial_columns FROM table_name WHERE condition
    
    UNION ALL
    
    -- 2. Recursive Member (References cte_name)
    SELECT c.next_columns
    FROM table_name t
    JOIN cte_name c ON t.parent_id = c.id
    WHERE termination_condition
)
SELECT * FROM cte_name;
```

---

## 📝 Examples

### 1. Generating a Number Series (1 to 5)

```sql
WITH RECURSIVE Numbers AS (
    -- Anchor: Start with 1
    SELECT 1 AS n
    
    UNION ALL
    
    -- Recursive: Add 1 until n reaches 5
    SELECT n + 1 
    FROM Numbers 
    WHERE n < 5
)
SELECT * FROM Numbers;
```

#### Output: `1, 2, 3, 4, 5`

---

### 2. Traversing Manager-Employee Hierarchy

Find all employees under Manager `emp_id = 1` at all depth levels:

```sql
WITH RECURSIVE EmpHierarchy AS (
    -- Anchor: Manager record
    SELECT emp_id, name, manager_id, 1 AS level
    FROM employees
    WHERE emp_id = 1
    
    UNION ALL
    
    -- Recursive: Find direct reports of current level
    SELECT e.emp_id, e.name, e.manager_id, h.level + 1
    FROM employees e
    JOIN EmpHierarchy h ON e.manager_id = h.emp_id
)
SELECT * FROM EmpHierarchy;
```

---

# 🎯 Most Asked Interview Questions

### 1. What are the main components of a Recursive CTE?
> 1. An **Anchor Member** (base query).
> 2. `UNION ALL`.
> 3. A **Recursive Member** that references the CTE name and includes a termination condition.

---

### 2. What happens if a Recursive CTE does not have a proper termination condition?
> It will enter an infinite loop until it hits the database engine's maximum recursion limit (e.g. `cte_max_recursion_depth` in MySQL) and throws an error.

---

### 3. Name 2 practical use cases for Recursive CTEs.
> 1. Traversing hierarchical organizational charts or family trees.
> 2. Generating consecutive dates, numbers, or time intervals for reporting gaps.

---

# 🧠 Quick Revision

```text
Anchor Member (Initial Base Row)
       ↓
UNION ALL
       ↓
Recursive Member (References CTE + Termination Check)
       ↓
Repeats until condition evaluates to FALSE
```

> **Memory Trick:** `Anchor + UNION ALL + Recursive Member (Self-reference)`
