# ⚡ SQL Triggers

## 📌 Definition

A **trigger** is a database program that automatically executes when a specified event occurs on a table.

Common events:

```text
INSERT
UPDATE
DELETE
```

---

# 💻 Example

Suppose we want to automatically record when an employee is inserted.

```sql
CREATE TRIGGER employee_insert
AFTER INSERT ON employees
FOR EACH ROW
INSERT INTO employee_log(employee_id, action)
VALUES (NEW.employee_id, 'INSERT');
```

Whenever a new employee is inserted, the trigger automatically executes.

---

# 🔄 BEFORE vs AFTER

| Trigger  | Meaning                   |
| -------- | ------------------------- |
| `BEFORE` | Executes before the event |
| `AFTER`  | Executes after the event  |

Example:

```sql
CREATE TRIGGER check_salary
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
    -- validation logic
END;
```

---

# 🔑 NEW and OLD

Triggers can use:

```text
NEW → New row value
OLD → Previous row value
```

Typical usage:

| Event  | NEW | OLD |
| ------ | --- | --- |
| INSERT | ✅   | ❌   |
| UPDATE | ✅   | ✅   |
| DELETE | ❌   | ✅   |

---

# 🗑️ Delete Trigger

```sql
DROP TRIGGER employee_insert;
```

---

# 🎯 Most Asked Interview Questions

### 1. What is a trigger?

> A trigger is a database program that automatically executes when a specified database event occurs.

### 2. When can a trigger execute?

> Commonly on `INSERT`, `UPDATE`, or `DELETE`.

### 3. Difference between BEFORE and AFTER trigger?

> A `BEFORE` trigger executes before the event, while an `AFTER` trigger executes after the event.

### 4. What are NEW and OLD?

> `NEW` refers to the new row values and `OLD` refers to the previous row values.

---

# 🧠 Quick Revision

```text
TRIGGER
   ↓
Automatic execution
   ↓
INSERT / UPDATE / DELETE
```

> **Memory Trick:** **Trigger = Automatic database action**
