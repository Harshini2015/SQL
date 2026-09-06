# 🧠 Logical Operators

## 📌 Definition

**Logical Operators** combine multiple conditions in a `WHERE` or `HAVING` clause to produce a single boolean result (`TRUE`, `FALSE`, or `UNKNOWN`).

---

## 🔑 Key Operators & Truth Tables

| Operator | Description | Returns TRUE when |
| :--- | :--- | :--- |
| **`AND`** | Logical Conjunction | **Both** conditions are `TRUE` |
| **`OR`** | Logical Disjunction | **At least one** condition is `TRUE` |
| **`NOT`** | Logical Negation | The underlying condition is `FALSE` |

### Operator Precedence:
1. `NOT` (Highest)
2. `AND`
3. `OR` (Lowest)

> 💡 **Best Practice:** Always use parentheses `()` to clarify complex conditions.

---

## 💻 Syntax & Example

```sql
SELECT name, department, salary
FROM employees
WHERE (department = 'IT' OR department = 'HR')
  AND salary > 50000;
```

---

## 📝 Truth Tables with Three-Valued Logic (`NULL`)

| Condition A | Condition B | A AND B | A OR B |
| :--- | :--- | :--- | :--- |
| `TRUE` | `TRUE` | `TRUE` | `TRUE` |
| `TRUE` | `FALSE` | `FALSE` | `TRUE` |
| `TRUE` | `NULL` | `NULL` | `TRUE` |
| `FALSE` | `NULL` | `FALSE` | `NULL` |

---

# 🎯 Most Asked Interview Questions

### 1. What is the operator precedence among `AND`, `OR`, and `NOT`?
> `NOT` takes highest precedence, followed by `AND`, and finally `OR`.

---

### 2. Why is grouping with parentheses `()` important when combining `AND` and `OR`?
> Because `AND` executes before `OR`. Without parentheses, `col1 = 'A' OR col2 = 'B' AND salary > 50` is evaluated as `col1 = 'A' OR (col2 = 'B' AND salary > 50)`, which can produce unintended query results.

---

### 3. What does `TRUE AND NULL` evaluate to in SQL?
> It evaluates to `NULL` (or `UNKNOWN`).

---

# 🧠 Quick Revision

```text
Logical Operators
 ├── AND → All must be TRUE
 ├── OR  → Any one TRUE is enough
 └── NOT → Reverses boolean outcome
 
Precedence: NOT > AND > OR
```

> **Memory Trick:** `AND requires ALL | OR requires ONE | NOT flips state`
