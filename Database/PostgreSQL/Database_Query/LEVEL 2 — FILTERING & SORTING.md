**Q1. Find employees with a salary greater than 70000, sorted by salary descending.**

**✅ Query:**

SELECT first_name, last_name, salary

FROM employees

WHERE salary > 70000

ORDER BY salary DESC;

**OUTPUT**

| first_name | last_name | salary    |
| ---------- | --------- | --------- |
| David      | WHite     | 80000.00  |
| Bob        | Smith     | 75000.00  |
|Emma        | Davis     | 72000.00  |


**Q2. Find employees in New York or Boston.**

**✅ Query:**

SELECT e.first_name, e.last_name, d.location

FROM employees e

JOIN departments d ON e.dept_id = d.dept_id

WHERE d.location IN ('New York','Boston');

| first_name | last_name | location |
| ---------- | --------- | -------- |
| Alice      | BROWn     | New York |
| Carol      | Johnson   | New York |
| David      | WHite     | Boston   |

**Q3. List employees whose last name starts with ‘D’.**

**✅ Query:**

SELECT first_name, last_name

FROM employees

WHERE last_name LIKE 'D%';

| first_name | last_name |
| ---------- | --------- |
| Emma       | Davis     |


**Q4. Show employees not assigned to any project.**

**✅ Query:**

SELECT e.first_name, e.last_name

FROM employees e

LEFT JOIN employee_projects ep ON e.emp_id = ep.emp_id

WHERE ep.emp_id IS NULL;

**OUTPUT**

No data found

**Q5. Show top 2 highest-paid employees**

**✅ Query:**

SELECT first_name, last_name, salary

FROM employees

ORDER BY salary DESC

LIMIT 2;

| first_name | last_name   | salary |
| ---------- | ---------   | ------ |
| David      | WHite       | 80000  |
| Bob        | Smith       | 75000  |





