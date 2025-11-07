**1. Show employee names with their department name**

**✅ Query:**

SELECT e.first_name || ' ' || e.last_name AS employee_name, d.dept_name

FROM employees e

JOIN departments d ON e.dept_id = d.dept_id;

**OUTPUT**

| employee_name | dept_name   |
| ------------- | ----------- |
| Alice Brown   | Engineering |
| Bob Smith     | Marketing   |
| Carol Johnson | Engineering |
| David White   | HR          |
| Emma Davis    | Marketing   |


** 2. Display project names and the employees working on them**

**✅ Query:**

SELECT p.project_name,e.first_name || ' ' || e.last_name AS employee_name

FROM employee_projects ep

JOIN employees e ON ep.emp_id = e.emp_id

JOIN projects p ON ep.project_id = p.project_id

ORDER BY p.project_name;

**OUTPUT**

| project_name     | employee_name |
| ---------------- | ------------- |
| Website Redesign | Alice Brown   |
| Website Redesign | Carol Johnson |
| Ad Campaign      | Bob Smith     |
| Ad Campaign      | Emma Davis    |
| HR Automation    | David White   |
| HR Automation    | Alice Brown   |


**3️⃣ Find employees who worked on multiple projects**

**✅ Query:**

SELECT 
    e.first_name || ' ' || e.last_name AS employee_name,
    COUNT(ep.project_id) AS project_count

FROM employee_projects ep

JOIN employees e
    ON ep.emp_id = e.emp_id

GROUP BY e.emp_id, e.first_name, e.last_name

HAVING COUNT(ep.project_id) > 1;

**OUTPUT:**

| employee_name | project_count |
| ------------- | ------------- |
| Alice Brown   | 2             |


**Show department name and total salary of employees in that department**

**✅ Query:**


SELECT 
    d.dept_name,
    SUM(e.salary) AS total_salary

FROM employees e

JOIN departments d 
    ON e.dept_id = D.dept_id

GROUP BY d.dept_name;

**OUTPUT:**

| dept_name   | total_salary |
| ----------- | ------------ |
| Engineering | 115000       |
| Marketing   | 147000       |
| HR          | 80000        |

**5️⃣ Find all employees who worked on a project with a budget > 100000**

**✅ Query:**

SELECT DISTINCT
   e.first_name || ' ' || e.last_name AS employee_name,
   p.project_name,
   p.budget

FROM employees e

JOIN employee_projects ep
    ON e.emp_id = ep.emp_id

JOIN projects p
    ON ep.project_id = p.project_id

WHERE p.budget > 100000

**OUTPUT:**

| employee_name | project_name     | budget |
| ------------- | ---------------- | ------ |
| Alice Brown   | Website Redesign | 150000 |
| Carol Johnson | Website Redesign | 150000 |
| David White   | HR Automation    | 120000 |
| Alice Brown   | HR Automation    | 120000 |






