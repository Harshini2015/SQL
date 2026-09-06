# ✂️ SUBSTRING & SUBSTR Functions

## 📌 Definition

The **`SUBSTRING()`** (or **`SUBSTR()`**) function extracts a portion (substring) of a text string starting at a specified position for a given length.

---

## 🔑 Key Concepts & Indexing Rules

* **1-Based Indexing:** In SQL, string indexing **starts at position 1** (NOT 0!).
* **Syntax:** `SUBSTRING(string, start_position, [length])`
  * `start_position`: Starting index (1-based).
  * `length` *(Optional)*: Number of characters to extract. If omitted, extracts everything up to the end of the string.
* **Negative Start Index (MySQL / PostgreSQL):** A negative start index counts backward from the end of the string (`-1` represents the last character).

---

## 💻 Syntax & Examples

```sql
-- Extract 4 characters starting at position 1
SELECT SUBSTRING('Database', 1, 4); -- Returns 'Data'

-- Extract from position 5 to the end
SELECT SUBSTRING('Database', 5);    -- Returns 'base'

-- Extract last 3 characters using negative index (MySQL)
SELECT SUBSTRING('Database', -3);   -- Returns 'ase'
```

---

## 📝 Practical Example: Extracting Domain from Email

```sql
SELECT 
    email,
    SUBSTRING(email, INSTR(email, '@') + 1) AS domain_name
FROM users;
```

---

# 🎯 Most Asked Interview Questions

### 1. Does string indexing start at 0 or 1 in SQL?
> String indexing in standard SQL starts at **1**.

---

### 2. What is the difference between `SUBSTRING()` and `SUBSTR()`?
> There is no difference. `SUBSTRING()` is the standard ANSI SQL name, and `SUBSTR()` is an alias supported in MySQL, Oracle, and SQLite.

---

### 3. How do you extract the first 3 characters of a string?
> `SUBSTRING(column_name, 1, 3)` or `LEFT(column_name, 3)`.

---

# 🧠 Quick Revision

```text
SUBSTRING(str, start, length)
 ├── 1-Based Indexing (Index 1 = 1st letter)
 ├── Length is optional (defaults to end of string)
 └── Negative start index counts from string end
```

> **Memory Trick:** `SQL Indexing starts at 1, NOT 0!`
