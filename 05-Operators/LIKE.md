# 🔍 LIKE Operator & Wildcards

## 📌 Definition

The **`LIKE`** operator is used in a `WHERE` clause to perform pattern matching on string columns using **wildcard characters**.

---

## 🔑 Key Wildcard Characters

| Wildcard | Description | Example Pattern | Matches |
| :--- | :--- | :--- | :--- |
| **`%`** | Represents **zero, one, or multiple** characters | `'A%'` | Anything starting with 'A' (e.g. "Amit", "A") |
| **`_`** | Represents exactly **one single** character | `'_a%'` | Strings where 'a' is the 2nd letter (e.g. "Rahul") |

---

## 💻 Common Pattern Examples

```sql
-- 1. Starts with 'A'
SELECT * FROM employees WHERE name LIKE 'A%';

-- 2. Ends with 'n'
SELECT * FROM employees WHERE name LIKE '%n';

-- 3. Contains 'ram' anywhere
SELECT * FROM employees WHERE name LIKE '%ram%';

-- 4. Second character is 'h'
SELECT * FROM employees WHERE name LIKE '_h%';

-- 5. Exactly 5 characters long
SELECT * FROM employees WHERE name LIKE '_____';
```

---

## 🛡️ Escaping Wildcard Characters

To search for literal `%` or `_` characters in data, use an `ESCAPE` clause:

```sql
-- Finds discount strings containing literal '%' (e.g. "10% off")
SELECT * FROM promotions
WHERE discount_code LIKE '%\%%' ESCAPE '\';
```

---

## ⚖️ Dialect Note: Case Sensitivity

* **MySQL:** `LIKE` is generally **case-insensitive** by default (depending on collation like `utf8mb4_general_ci`).
* **PostgreSQL:** `LIKE` is **case-sensitive**. Use **`ILIKE`** for case-insensitive matching.

---

# 🎯 Most Asked Interview Questions

### 1. What is the difference between `%` and `_` in `LIKE` queries?
> `%` matches zero, one, or multiple characters, while `_` matches exactly one single character.

---

### 2. How do you find names where the second letter is 'a'?
> Use `WHERE name LIKE '_a%'`.

---

### 3. How do you query literal `%` or `_` characters in SQL?
> By specifying an escape character using `ESCAPE`, for example: `WHERE code LIKE '%\_%' ESCAPE '\'`.

---

### 4. What is `ILIKE` in PostgreSQL?
> `ILIKE` is a PostgreSQL-specific operator that performs case-insensitive pattern matching.

---

# 🧠 Quick Revision

```text
LIKE Operator
 ├── % → Zero or multiple characters
 ├── _ → Exactly one character
 ├── ESCAPE '\' → Search literal % or _
 └── PostgreSQL: ILIKE (Case-insensitive)
```

> **Memory Trick:** `% = Any length | _ = Single letter`
