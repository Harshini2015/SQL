# ✂️ TRIM, LTRIM & RTRIM Functions

## 📌 Definition

The **`TRIM()`** function removes unwanted leading and trailing whitespace (or specified prefix/suffix characters) from a string.

---

## 🔑 Key Concepts & Variants

* **`TRIM(string)`:** Removes whitespace from **both left and right** ends of the string.
* **`LTRIM(string)`:** Removes whitespace from the **left (leading)** side only.
* **`RTRIM(string)`:** Removes whitespace from the **right (trailing)** side only.
* **Custom Character Trimming:** `TRIM(BOTH 'x' FROM string)` removes specific non-space characters.

---

## 💻 Syntax & Examples

### 1. Removing Whitespace
```sql
SELECT 
    TRIM('   SQL Notes   ')  AS trim_both,  -- Returns 'SQL Notes'
    LTRIM('  SQL Notes   ') AS trim_left,  -- Returns 'SQL Notes   '
    RTRIM('  SQL Notes   ') AS trim_right; -- Returns '  SQL Notes'
```

### 2. Custom Character Trimming (MySQL / PostgreSQL)
```sql
SELECT TRIM(BOTH '0' FROM '00012345000') AS clean_code;
-- Returns '12345'
```

---

# 🎯 Most Asked Interview Questions

### 1. How do you remove both leading and trailing spaces from a user input string in SQL?
> By using `TRIM(column_name)`.

---

### 2. How do you remove leading zeros from a numerical string formatted as `'000456'`?
> By using `TRIM(LEADING '0' FROM '000456')` (or `LTRIM` variations).

---

# 🧠 Quick Revision

```text
Trimming Functions
 ├── LTRIM(str) → Removes left spaces
 ├── RTRIM(str) → Removes right spaces
 └── TRIM(str)  → Removes spaces from both ends
```

> **Memory Trick:** `LTRIM = Left | RTRIM = Right | TRIM = Both Sides`
