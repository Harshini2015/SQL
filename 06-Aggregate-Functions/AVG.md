# 📈 AVG Function

## 📌 Definition

The **`AVG()`** aggregate function calculates the arithmetic mean (average) of non-null values in a numeric column.

---

## 🔑 Key Concepts & The `NULL` Trap

* **Ignores `NULL` in Denominator:** `AVG()` skips `NULL` values when computing both the **sum** (numerator) and the **count of rows** (denominator).
* **Formula:**
  $$\text{AVG(column)} = \frac{\text{Sum of non-null values}}{\text{Count of non-null rows}}$$

### ⚠️ Critical Interview Example:
For dataset values `[100, 200, 300, NULL]`:
* `AVG(column)` = $\frac{100 + 200 + 300}{3} = \mathbf{200}$ *(Denominator is 3)*
* `AVG(COALESCE(column, 0))` = $\frac{100 + 200 + 300 + 0}{4} = \mathbf{150}$ *(Denominator is 4)*

---

## 💻 Syntax & Examples

```sql
SELECT department, AVG(salary) AS avg_dept_salary
FROM employees
GROUP BY department;
```

---

## 📝 Example

### `marks` Table

| student_id | score |
| ---------: | ----: |
|          1 |    80 |
|          2 |    90 |
|          3 |  NULL |

```sql
SELECT 
    AVG(score) AS avg_ignoring_null,                -- (80 + 90) / 2 = 85
    AVG(COALESCE(score, 0)) AS avg_treating_null_zero -- (80 + 90 + 0) / 3 = 56.67
FROM marks;
```

---

# 🎯 Most Asked Interview Questions

### 1. How does `AVG()` handle `NULL` values in SQL?
> `AVG()` completely ignores `NULL` values. It calculates the sum of non-null values divided by the count of non-null rows.

---

### 2. How do you force `AVG()` to include `NULL` rows by treating them as zero?
> Wrap the column in `COALESCE` or `IFNULL`: `AVG(COALESCE(column_name, 0))`.

---

### 3. What does `AVG()` return for an empty table?
> `AVG()` returns `NULL` for an empty table or a column containing only `NULL`s.

---

# 🧠 Quick Revision

```text
AVG(col)
 ├── Sum of non-null values ÷ Count of non-null rows
 ├── Ignores NULLs from row count
 └── To treat NULL as 0: AVG(COALESCE(col, 0))
```

> **Memory Trick:** `AVG skips NULLs in both Sum AND Count!`
