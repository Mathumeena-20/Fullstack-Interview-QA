Here’s a **comprehensive list of PostgreSQL interview questions** for someone with **2+ years of experience**, covering fundamentals, SQL queries, performance tuning, indexing, and practical usage.

---

## 🧠 **1. Basic PostgreSQL Concepts**

1. What is PostgreSQL? How is it different from other databases like MySQL or Oracle?
2. Explain the architecture of PostgreSQL.
3. What is the role of the `postmaster` process in PostgreSQL?
4. What is a schema in PostgreSQL?
5. What is the difference between a database and a schema?
6. How do you connect to a PostgreSQL database using the command line?
7. What are some data types supported by PostgreSQL?
8. What is the purpose of the `serial` and `bigserial` data types?
9. What is the use of the `UUID` type?
10. How do you handle case-sensitive queries in PostgreSQL?

---

## 💡 **2. SQL Queries and Joins**

1. Write a query to get the second highest salary from an `employees` table.
2. Write a query to find employees who joined in the last 30 days.
3. What is the difference between `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN`?
4. How do you perform cross joins in PostgreSQL?
5. How can you get distinct records from a table?
6. Write a query to count the number of employees in each department.
7. What is a CTE (Common Table Expression)? Give an example.
8. What is the difference between a CTE and a subquery?
9. How do you perform pagination in PostgreSQL (e.g., showing 10 records per page)?
10. What is the `RETURNING` clause used for in an `INSERT`, `UPDATE`, or `DELETE` statement?

---

## ⚙️ **3. Constraints and Keys**

1. What are the different types of constraints in PostgreSQL?
2. What is the difference between a primary key and a unique key?
3. What are foreign keys and how do you define them?
4. What is the difference between `ON DELETE CASCADE` and `ON DELETE SET NULL`?
5. How can you drop a constraint from a table?

---

## 🧩 **4. Indexing and Performance**

1. What are indexes? Why are they important?
2. What types of indexes does PostgreSQL support?

   * (e.g., B-tree, Hash, GIN, GiST, BRIN)
3. How do you create an index?
4. What is a composite index?
5. What is the difference between a clustered and a non-clustered index?
6. How can you check if an index is being used in a query?
7. What does the `EXPLAIN` command do?
8. How do you optimize a slow query in PostgreSQL?
9. How do `VACUUM` and `ANALYZE` help in performance tuning?
10. What is autovacuum?

---

## 🔐 **5. Transactions and Concurrency**

1. What is a transaction in PostgreSQL?
2. Explain the ACID properties.
3. What are isolation levels? Name all isolation levels supported by PostgreSQL.
4. What is the default isolation level in PostgreSQL?
5. What is the difference between `COMMIT` and `ROLLBACK`?
6. What is a deadlock and how do you prevent it?
7. How can you handle concurrency in PostgreSQL?

---

## 🧮 **6. Functions and Stored Procedures**

1. How do you create a function in PostgreSQL?
2. What is the difference between a function and a stored procedure?
3. How do you return multiple rows from a function?
4. What is the `DO` block in PostgreSQL?
5. What are triggers? When do you use them?
6. What are some common use cases for triggers?

---

## 🧱 **7. JSON and Advanced Features**

1. How do you store JSON data in PostgreSQL?
2. What is the difference between `json` and `jsonb`?
3. How can you query a `jsonb` column?
4. Give an example of using PostgreSQL array data types.
5. How do you use `hstore` in PostgreSQL?

---

## 🧰 **8. Backup, Restore, and Maintenance**

1. How do you back up a PostgreSQL database?
2. How do you restore a database from a backup file?
3. What is the difference between `pg_dump` and `pg_dumpall`?
4. What is WAL (Write-Ahead Logging)?
5. How do you monitor database performance?

---

## 🌐 **9. Real-Time / Practical Scenarios**

1. A query is running slow — how do you debug it?
2. How do you migrate a table from one schema to another?
3. How would you handle schema changes in production?
4. How do you check active connections in PostgreSQL?
5. What’s the difference between `DELETE`, `TRUNCATE`, and `DROP`?
6. How do you store hierarchical data (e.g., categories and subcategories)?
7. How do you perform case-insensitive searches?
8. How do you ensure data integrity between related tables?

---

## 💬 **10. Bonus — Common Trick Questions**

1. Can a table have multiple primary keys?
2. Can a unique key contain NULL values?
3. What happens if you insert a NULL in a NOT NULL column?
4. How do you rename a column or table?
5. Can you have an index on an expression (e.g., `LOWER(column_name)`)?
6. How to find duplicate rows in a table?
7. What’s the difference between `NOW()` and `CURRENT_TIMESTAMP`?
