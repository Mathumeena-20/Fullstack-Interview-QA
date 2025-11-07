**Q1. Select all employees working in the Engineering department**


**✅ Query:**


SELECT e.*
FROM employees e
JOIN departments d
ON e.dept_id = d.dept_id
WHERE d.dept_name = 'Engineering';



**OUTPUT:**
emp_id      first_name   last_name    dept_id     salary        hire_date

101         Alice         BROWn       1           60000.00      2019-03-15
103         Carol        Johnson      1           55000.00      2021-01-12



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





