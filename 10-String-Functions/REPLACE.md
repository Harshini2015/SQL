# 🔄 REPLACE Function

## 📌 Definition

The **`REPLACE()`** function replaces **all occurrences** of a specified substring within a string with a new replacement substring.

---

## 🔑 Key Concepts

* **Replaces All Occurrences:** Finds every instance of `search_str` and swaps it with `replace_str`.
* **Case Sensitivity:** Operates case-sensitively in most standard SQL databases (depends on database collation).
* **Data Cleansing:** Widely used for data cleaning (e.g. removing spaces, removing special symbols, updating domain extensions).

---

## 💻 Syntax

```sql
REPLACE(string, search_substring, replacement_substring)
```

---

## 📝 Examples

### 1. Replacing Substring in Text
```sql
SELECT REPLACE('SQL Tutorial 2024', '2024', '2025') AS updated_text;
-- Returns 'SQL Tutorial 2025'
```

### 2. Cleaning Formatting (Removing Hyphens & Spaces from Phone Number)
```sql
SELECT REPLACE(REPLACE(phone, '-', ''), ' ', '') AS clean_phone
FROM contacts;
```

---

# 🎯 Most Asked Interview Questions

### 1. What does `REPLACE()` do if the search substring is not found in the target string?
> If the search substring is not found, `REPLACE()` returns the original string unchanged.

---

### 2. Does `REPLACE()` replace only the first occurrence or all occurrences?
> `REPLACE()` replaces **all occurrences** of the search substring throughout the target string.

---

### 3. How do you remove all spaces from a string column using `REPLACE()`?
> By specifying an empty string `''` as the replacement: `REPLACE(column_name, ' ', '')`.

---

# 🧠 Quick Revision

```text
REPLACE(string, search, replacement)
 ├── Replaces ALL occurrences
 ├── Searching for ' ' and replacing with '' removes spaces
 └── Returns original string if search string not found
```

> **Memory Trick:** `REPLACE = Global Find & Swap`
