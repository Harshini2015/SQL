# 🔗 CONCAT & CONCAT_WS Functions

## 📌 Definition

The **`CONCAT()`** string function concatenates (combines) two or more strings into a single string.

---

## 🔑 Key Concepts & Variants

* **`CONCAT(str1, str2, ...)`:** Joins strings end-to-end.
* **`CONCAT_WS(separator, str1, str2, ...)`:** **CONCAT With Separator** joins strings with a specified delimiter (e.g. comma, space, hyphen).
* **`NULL` Behavior in MySQL:**
  * `CONCAT()` returns **`NULL`** if **any argument is `NULL`** (`CONCAT('Hello', NULL)` $\rightarrow$ `NULL`).
  * `CONCAT_WS()` **ignores `NULL` values** completely and concatenates the remaining strings!

---

## 💻 Syntax & Examples

### 1. Combining First Name and Last Name
```sql
SELECT CONCAT(first_name, ' ', last_name) AS full_name
FROM employees;
```

### 2. Formatting Address with `CONCAT_WS`
```sql
SELECT CONCAT_WS(', ', street, city, state, zip_code) AS full_address
FROM customers;
```

---

## 📝 Example

### `employees` Table

| first_name | last_name | middle_name |
| :--------- | :-------- | :---------- |
| Rahul      | Sharma    | Kumar       |
| Priya      | Singh     | NULL        |

```sql
SELECT 
    CONCAT(first_name, ' ', middle_name, ' ', last_name) AS concat_name,
    CONCAT_WS(' ', first_name, middle_name, last_name) AS concat_ws_name
FROM employees;
```

### Result:

| concat_name | concat_ws_name |
| :---------- | :------------- |
| Rahul Kumar Sharma | Rahul Kumar Sharma |
| **NULL** | Priya Singh |

---

# 🎯 Most Asked Interview Questions

### 1. What happens if you pass a `NULL` value to `CONCAT()` in MySQL?
> In MySQL, `CONCAT()` returns `NULL` if any input argument is `NULL`.

---

### 2. How does `CONCAT_WS()` differ from `CONCAT()`?
> `CONCAT_WS()` takes a separator as its first argument and automatically **skips any `NULL` values** rather than returning `NULL`.

---

### 3. What is the SQL standard operator for string concatenation?
> The ANSI SQL standard string concatenation operator is `||` (e.g., `'Hello ' || name`).

---

# 🧠 Quick Revision

```text
CONCAT Functions
 ├── CONCAT(a, b, c) → Any NULL turns entire result NULL!
 └── CONCAT_WS(sep, a, b) → Skips NULLs & inserts separator
```

> **Memory Trick:** `CONCAT + NULL = NULL | CONCAT_WS ignores NULLs`
