# 🧱 SQL Data Types

## 📌 Definition

A **data type** defines what kind of value a column can store.

Example:

```sql
CREATE TABLE employees (
    employee_id INT,
    name VARCHAR(100),
    salary DECIMAL(10,2),
    joining_date DATE
);
```

Here:

```text
employee_id  → INT
name         → VARCHAR
salary       → DECIMAL
joining_date → DATE
```

---

# 🔢 1. Numeric Data Types

Used to store numbers.

| Data Type      | Used For                          |
| -------------- | --------------------------------- |
| `INT`          | Whole numbers                     |
| `BIGINT`       | Very large whole numbers          |
| `DECIMAL(p,s)` | Exact decimal values              |
| `FLOAT`        | Approximate decimal values        |
| `DOUBLE`       | Larger approximate decimal values |

### Example

```sql
age INT
salary DECIMAL(10,2)
```

### DECIMAL(10,2)

```text
10 → Total digits
2  → Digits after decimal
```

Example:

```text
12345678.90
```

---

# 🔤 2. String Data Types

Used to store text.

| Data Type    | Used For             |
| ------------ | -------------------- |
| `CHAR(n)`    | Fixed-length text    |
| `VARCHAR(n)` | Variable-length text |
| `TEXT`       | Large text           |

### CHAR vs VARCHAR

| `CHAR`                     | `VARCHAR`                      |
| -------------------------- | ------------------------------ |
| Fixed length               | Variable length                |
| Good for fixed-size values | Good for varying-length values |
| Example: country code      | Example: name                  |

Example:

```sql
country_code CHAR(2)
name VARCHAR(100)
```

> **Interview favorite:** `CHAR` = fixed, `VARCHAR` = variable.

---

# 📅 3. Date and Time Data Types

| Data Type   | Stores                                                |
| ----------- | ----------------------------------------------------- |
| `DATE`      | Date                                                  |
| `TIME`      | Time                                                  |
| `DATETIME`  | Date + time                                           |
| `TIMESTAMP` | Date + time with database-specific timestamp behavior |

### Examples

```sql
birth_date DATE
login_time TIME
created_at DATETIME
updated_at TIMESTAMP
```

---

# 🔘 4. Boolean

Used to represent true/false values.

In MySQL:

```sql
is_active BOOLEAN
```

MySQL treats `BOOLEAN` as a synonym for `TINYINT(1)`.

Typically:

```text
TRUE  → 1
FALSE → 0
```

---

# 🧩 Choosing Data Types

Example:

```sql
CREATE TABLE employees (
    employee_id INT,
    name VARCHAR(100),
    salary DECIMAL(10,2),
    is_active BOOLEAN,
    joining_date DATE
);
```

| Column         | Data Type | Reason               |
| -------------- | --------- | -------------------- |
| `employee_id`  | `INT`     | Whole number         |
| `name`         | `VARCHAR` | Variable-length text |
| `salary`       | `DECIMAL` | Exact monetary value |
| `is_active`    | `BOOLEAN` | True/false           |
| `joining_date` | `DATE`    | Date                 |

---

# 🎯 Most Asked Interview Questions

### 1. What is a data type?

> A data type defines the kind of value that a column can store.

---

### 2. What is the difference between CHAR and VARCHAR?

> `CHAR` stores fixed-length strings, while `VARCHAR` stores variable-length strings.

---

### 3. Which data type is preferred for storing salary?

> Usually `DECIMAL`, because it stores exact decimal values and is appropriate for monetary amounts.

---

### 4. What is DECIMAL(10,2)?

> It allows up to 10 total digits, with 2 digits after the decimal point.

Example:

```text
12345678.90
```

---

### 5. Difference between INT and BIGINT?

> Both store integer values, but `BIGINT` supports a much larger range of values than `INT`.

---

### 6. Which data type is used to store dates?

> `DATE`.

For date and time together, use a suitable type such as `DATETIME` or `TIMESTAMP`, depending on the requirement and database.

---

# 🧠 Quick Revision

```text
Numeric
→ INT
→ BIGINT
→ DECIMAL
→ FLOAT / DOUBLE

String
→ CHAR
→ VARCHAR
→ TEXT

Date/Time
→ DATE
→ TIME
→ DATETIME
→ TIMESTAMP

Boolean
→ BOOLEAN
```

### Remember

```text
CHAR      → Fixed text
VARCHAR   → Variable text
INT       → Whole number
DECIMAL   → Exact decimal
DATE      → Date
DATETIME  → Date + time
BOOLEAN   → True / False
```

> **Interview Tip:** The most important comparisons to remember are **CHAR vs VARCHAR**, **INT vs BIGINT**, and **DECIMAL vs FLOAT/DOUBLE**.
