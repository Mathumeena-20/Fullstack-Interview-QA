**1️⃣ Find employees who earn more than the average salary**

**✅ Query**

SELECT first_name, last_name, salary

FROM employees

WHERE salary > (SELECT AVG(salary) FROM employees);

**OUTPUT:**

| first_name | last_name | salary    |
| ---------- | --------- | ------    |
| Bob        | Smith     | 75000.00  |
| David      | WHite     | 80000.00  |
| Emma       | Davis     | 72000.00  |

**2️⃣ List employees who have never worked on any project**

**✅ Query**

SELECT e.first_name, e.last_name

FROM employees e

WHERE e.emp_id NOT IN (
    
    SELECT emp_id FROM employee_projects
);

**OUTPUT:**

No data found

**3️⃣ Show departments where no employees earn below 60000**

**✅ Query**

SELECT d.dept_name

FROM departments d 

WHERE d.dept_id NOT IN(
   
    SELECT e.dept_id
   
    FROM employees e
   
    WHERE e.salary < 60000
);

**OUTPUT:**

| dept_name   |
| ----------- |
| Marketing   |
| HR          |


**4.Get the project name where the highest-paid employee worked**

**✅ Query**

SELECT p.project_name

FROM projects p

JOIN employee_projects ep ON p.project_id = ep.project_id

WHERE ep.emp_id =(

    SELECT emp_id

    FROM employees
    
    ORDER BY salary DESC
    
    LIMIT 1
);

**OUTPUT:**

| project_name  |
| ------------- |
| HR Automation |


**5️⃣ Find the employee who joined most recently**

**✅ Query**

SELECT first_name, last_name, hire_date

FROM employees

WHERE hire_date = (
    
    SELECT MAX(hire_date)
    
    FROM employees
);

**OUTPUT**

| first_name | last_name | hire_date  |
| ---------- | --------- | ---------- |
| Carol      | Johnson   | 2021-01-12 |






