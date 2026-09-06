# 📏 LENGTH & CHAR_LENGTH Functions

## 📌 Definition

The **`LENGTH()`** function returns the length of a string measured in **bytes**, whereas **`CHAR_LENGTH()`** returns the length of a string measured in **characters**.

---

## 🔑 Key Concepts & Differences

* **`LENGTH(string)`:** Returns string length in **bytes**.
* **`CHAR_LENGTH(string)`:** Returns string length in **characters** (multi-byte UTF-8 characters count as 1 character).
* **For ASCII Text:** `LENGTH()` and `CHAR_LENGTH()` return identical numbers.
* **Dialect Variations:**
  * **MySQL:** `LENGTH()` (bytes) vs `CHAR_LENGTH()` (characters).
  * **SQL Server:** Uses `LEN()` (trims trailing spaces).
  * **Oracle / PostgreSQL:** `LENGTH()` counts characters.

---

## 💻 Syntax & Example

```sql
SELECT 
    name,
    LENGTH(name) AS len_bytes,
    CHAR_LENGTH(name) AS len_chars
FROM users;
```

---

## 📝 Multi-Byte Character Example

Consider a UTF-8 character string containing unicode/emoji: `'Hello 🌍'`

```sql
SELECT 
    LENGTH('Hello 🌍') AS byte_count,      -- Returns 10 (Emoji takes 4 bytes in UTF-8)
    CHAR_LENGTH('Hello 🌍') AS char_count;  -- Returns 7 (6 letters/space + 1 emoji)
```

---

# 🎯 Most Asked Interview Questions

### 1. What is the difference between `LENGTH()` and `CHAR_LENGTH()` in MySQL?
> `LENGTH()` returns the length of the string in **bytes**, while `CHAR_LENGTH()` returns the number of **characters** regardless of multi-byte encoding.

---

### 2. How do you find records where a phone number does not contain exactly 10 digits?
> Using `WHERE CHAR_LENGTH(phone_number) != 10`.

---

### 3. What function is used in SQL Server to find string length?
> SQL Server uses the `LEN()` function (which ignores trailing spaces).

---

# 🧠 Quick Revision

```text
String Length Functions
 ├── LENGTH(str) → Length in BYTES (MySQL)
 └── CHAR_LENGTH(str) → Length in CHARACTERS
```

> **Memory Trick:** `CHAR_LENGTH = Character Count | LENGTH = Byte Count`
