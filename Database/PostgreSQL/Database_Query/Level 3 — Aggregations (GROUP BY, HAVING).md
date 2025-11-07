**1.Find the average salary per department.**

**✅ Query:**

SELECT d.dept_name, AVG(e.salary) AS avg_salary

FROM employees e

JOIN departments d ON e.dept_id = d.dept_id

GROUP BY d.dept_name;

**OUTPUT**

| dept_name   | avg_salary     |
| ----------- | ----------     |
| Marketing   | 73500.0000000  |
| Engineering | 57500.0000000  |
| HR          | 80000.0000000  |


**Q2. List departments where average salary > 65000**

**✅ Query:**

SELECT d.dept_name,AVG(e.salary) AS avg_salary

FROM employees e

JOIN departments d ON e.dept_id = d.dept_id

GROUP BY d.dept_name

HAVING AVG(e.salary) > 65000;

**OUTPUT**

| dept_name   | avg_salary |
| ----------- | ---------- |
| Marketing   | 73500.000  |
| HR          | 80000.00   |


**Q3. Count how many employees work in each location**

**✅ Query:**

SELECT d.location, COUNT(e.emp_id) AS total_employees

FROM employees e

JOIN departments d ON e.dept_id = d.dept_id

GROUP BY d.location

**OUTPUT:**

| location        | total_employees |
| --------        | --------------- |
| New York        | 2               |
| San Francisco   | 2               |
| Boston          | 1               |


**Q4. Find the total hours worked on each project**

**✅ Query:**

SELECT p.project_name, SUM(ep.hours_workes) AS total_hours

FROM projects p

JOIN employee_projects ep ON p.project_id = ep.project_id

GROUP BY p.project_name;

**OUTPUT**

| project_name      | total_hours |
| ---------------   | ----------- |
| Website Revamp    | 220         |
|HR Automation      | 200         |
| Ad Camaign        | 200         |

**Q5. Which employee has worked the most hours overall**

**✅ Query:**

SELECT e.first_name, e.last_name, SUM(ep.hours_workes) AS total_hours

FROM employees e

JOIN employee_projects ep ON e.emp_id = ep.emp_id

GROUP BY e.emp_id, e.first_name, e.last_name

ORDER BY total_hours DESC

LIMIT 1;

**OUTPUT:**

| first_name | last_name | total_hours |
| ---------- | --------- | ----------- |
| Alice      | BROWn     | 170         |









