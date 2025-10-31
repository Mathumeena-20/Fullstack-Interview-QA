## 🧩 1️⃣ **Can a table have multiple primary keys?**

### ❌ **Answer:**

No.
A table **can have only one primary key constraint**, but that key can include **multiple columns** (a *composite primary key*).

---

### 💡 **Example:**

```sql
CREATE TABLE student_course (
    student_id INT,
    course_id INT,
    PRIMARY KEY (student_id, course_id)
);
```

🧠 **Explanation:**

* Only **one** primary key constraint exists.
* It ensures **each combination** of `(student_id, course_id)` is unique.
* You can’t create another `PRIMARY KEY` in this table.

---

## 🧩 2️⃣ **Can a unique key contain NULL values?**

### ✅ **Answer:**

Yes, a **unique constraint allows NULLs** — because NULL represents “unknown,” and multiple unknowns are allowed.

---

### 💡 **Example:**

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email TEXT UNIQUE
);

INSERT INTO users (email) VALUES (NULL), (NULL);  -- ✅ Allowed
```

🧠 **Explanation:**

* PostgreSQL treats each `NULL` as distinct, so multiple NULLs do not violate `UNIQUE`.
* But duplicate *non-null* values are not allowed.

---

## 🧩 3️⃣ **What happens if you insert a NULL in a NOT NULL column?**

### ❌ **Answer:**

You’ll get an **error** — PostgreSQL prevents NULL insertion in a `NOT NULL` column.

---

### 💡 **Example:**

```sql
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name TEXT NOT NULL
);

INSERT INTO employees (name) VALUES (NULL);
```

🧠 **Output:**

```
ERROR: null value in column "name" violates not-null constraint
```

---

## 🧩 4️⃣ **How do you rename a column or table?**

### ✅ **A. Rename a column**

```sql
ALTER TABLE employees RENAME COLUMN name TO full_name;
```

### ✅ **B. Rename a table**

```sql
ALTER TABLE employees RENAME TO staff;
```

🧠 **Explanation:**

* Simple, transaction-safe operation.
* PostgreSQL automatically updates internal references, but **you must manually update** dependent queries, views, or triggers.

---

## 🧩 5️⃣ **Can you have an index on an expression (e.g., LOWER(column_name))?**

### ✅ **Answer:**

Yes! PostgreSQL supports **expression indexes** (functional indexes).

---

### 💡 **Example:**

```sql
CREATE INDEX idx_users_lower_email ON users (LOWER(email));
```

Now queries like:

```sql
SELECT * FROM users WHERE LOWER(email) = 'john@example.com';
```

✅ **Use the index efficiently**, improving performance.

---

🧠 **Why it’s useful:**

* Case-insensitive lookups (`LOWER()`)
* Partial or computed searches (`SUBSTRING()`, `COALESCE()`)

---

## 🧩 6️⃣ **How to find duplicate rows in a table?**

### ✅ **Use GROUP BY and HAVING:**

```sql
SELECT email, COUNT(*)
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

🧠 **Explanation:**

* `GROUP BY` groups identical values.
* `HAVING COUNT(*) > 1` filters duplicates.

---

### ✅ **To delete duplicates (keep one):**

```sql
DELETE FROM users a
USING users b
WHERE a.ctid < b.ctid
AND a.email = b.email;
```

🧠 `ctid` is a PostgreSQL internal row identifier — useful for duplicate cleanup.

---

## 🧩 7️⃣ **What’s the difference between NOW() and CURRENT_TIMESTAMP?**

### ✅ **Answer:**

They are **functionally equivalent** — both return the **current date and time** with time zone.

---

### 💡 **Example:**

```sql
SELECT NOW(), CURRENT_TIMESTAMP;
```

🧠 **Output:**

```
2025-10-31 22:30:45.123456+05:30 | 2025-10-31 22:30:45.123456+05:30
```

---

### ✅ **BUT:**

* `NOW()` is a **PostgreSQL function**.
* `CURRENT_TIMESTAMP` is **ANSI SQL standard**.
* In a transaction, both return the **time when the transaction started** (not updated each query).

---

### 💡 **Example (demonstrating snapshot):**

```sql
BEGIN;
SELECT NOW();
-- Wait 10 seconds
SELECT NOW();
COMMIT;
```

🧠 Both timestamps will be the same — because PostgreSQL ensures **transaction time consistency**.

---

## ✅ **Summary Table**

| Question                   | Answer                                | Example                            |
| -------------------------- | ------------------------------------- | ---------------------------------- |
| Multiple Primary Keys?     | ❌ Only one allowed (can be composite) | `PRIMARY KEY (col1, col2)`         |
| Unique Key with NULLs?     | ✅ Allowed (NULL ≠ NULL)               | Multiple NULL emails               |
| NULL in NOT NULL column?   | ❌ Error                               | `INSERT ... (NULL)`                |
| Rename column/table        | ✅ `ALTER TABLE ... RENAME`            | `ALTER TABLE emp RENAME TO staff;` |
| Index on expression        | ✅ Supported                           | `CREATE INDEX ... ON LOWER(email)` |
| Find duplicates            | ✅ Use `GROUP BY + HAVING`             | `HAVING COUNT(*) > 1`              |
| NOW() vs CURRENT_TIMESTAMP | ✅ Same, transaction-scoped            | Both return current timestamp      |

