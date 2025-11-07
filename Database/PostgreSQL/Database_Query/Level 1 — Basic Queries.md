**Q1. Select all employees working in the Engineering department**


**✅ Query:**


SELECT e.*
FROM employees e
JOIN departments d
ON e.dept_id = d.dept_id
WHERE d.dept_name = 'Engineering';



**OUTPUT:**
| emp_id | first_name | last_name | dept_id | salary     | hire_date   |
| ------ | ---------- | --------- | ------- | ---------- | ----------- |
| 101    | Alice      | Smith     | 1       | 70000      | 2019-11-15  |
| 103    | Carol      | Lee       | 1       | 75000      | 2022-06-01  |



**🧩 Q2. Find employees hired after 2020-01-01**


✅ Query:

SELECT *
FROM employees
WHERE hire_date > '2020-01-01';


**OUTPUT**

| emp_id | first_name | last_name | dept_id | hire_date  | salary |
| ------ | ---------- | --------- | ------- | ---------- | ------ |
| 102    | Bob        | Johnson   | 2       | 2021-03-12 | 60000  |
| 103    | Carol      | Lee       | 1       | 2022-06-01 | 75000  |
| 104    | David      | Kim       | 3       | 2020-07-21 | 50000  |


**🧩 Q3. Display employee full name and salary for all employees**

**✅ Query:**


SELECT 
    first_name || ' ' || last_name AS full_name,
    salary
FROM employees;


**OUTPUT**

| full_name         | salary |
| -----------       | ------ |
| Alice BROWn       | 60000  |
| Bob Smith         | 75000  |
| Carol Johnson     | 55000  |
| David WHite       | 80000  |
|Emma Davis         | 72000  |



**Q4. List distinct department locations**

**✅ Query:**

SELECT DISTINCT location
FROM departments;

**OUTPUT**

New York
San Francisco
Boston


**🧩 Q5. Find the total number of employees in the company**

**✅ Query:**

SELECT COUNT(*) AS total_employees
FROM employees;

**OUTPUT**


total_employees
---------------

5








