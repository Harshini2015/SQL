# 🔠 UPPER & LOWER Functions

## 📌 Definition

The **`UPPER()`** (or `UCASE()`) function converts all characters in a string to **uppercase**, while the **`LOWER()`** (or `LCASE()`) function converts all characters to **lowercase**.

---

## 🔑 Key Concepts

* **Standardization:** Frequently used to standardize data formatting (e.g. storing email addresses in lowercase).
* **Case-Insensitive Searching:** Used in `WHERE` clauses to perform case-insensitive comparisons across database engines.
* **Non-Alphabetical Characters:** Numbers, symbols, and punctuation remain unchanged.

---

## 💻 Syntax & Examples

```sql
-- Convert string to UPPERCASE
SELECT UPPER(name) FROM employees;

-- Convert string to lowercase
SELECT LOWER(email) FROM users;
```

---

## 📝 Case-Insensitive Comparison Example

```sql
SELECT * FROM users
WHERE LOWER(email) = LOWER('Rahul.Sharma@Gmail.COM');
```

---

# 🎯 Most Asked Interview Questions

### 1. How do you perform a case-insensitive string search in a case-sensitive database?
> By wrapping both the column and the search term in `LOWER()` or `UPPER()`:
> `WHERE LOWER(name) = LOWER('Rahul')`.

---

### 2. Are `UCASE()` and `LCASE()` valid standard SQL?
> `UPPER()` and `LOWER()` are ANSI standard SQL functions. `UCASE()` and `LCASE()` are synonym functions supported in MySQL.

---

# 🧠 Quick Revision

```text
String Case Conversion
 ├── UPPER('abc') → 'ABC'
 └── LOWER('ABC') → 'abc'
```

> **Memory Trick:** `UPPER = ALL CAPS | LOWER = all small`
