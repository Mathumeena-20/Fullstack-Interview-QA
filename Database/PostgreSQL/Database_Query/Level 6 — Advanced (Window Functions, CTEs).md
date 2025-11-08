**1️⃣ Rank employees by salary (highest → lowest)**

**✅ Query**

SELECT 

   emp_id,
   
   first_name,
   
   last_name,
   
   salary,
   
   Rank() OVER (ORDER BY salary DESC) AS salary_rank

FROM employees;

**OUTPUT:**

| emp_id | first_name | last_name | salary    | salary_rank |
| ------ | ---------- | --------- | ------    | ----------- |
| 104    | David      | WHitw     | 80000.00  | 1           |
| 102    | Bob        | Smith     | 75000.00  | 2           |
| 105    | Emma       | Davis     | 72000.00  | 2           |
| 101    | Alice      | BROWn     | 60000.00  | 4           |
| 103    | Carol      | Johson    | 55000.00  | 5           |


**2️⃣ Calculate the running total of salaries by department**

**✅ Query**

SELECT
  
    dept_id,
    
    emp_id,
    
    first_name,
    
    salary,
    
    SUM(salary) OVER (PARTITION BY dept_id ORDER BY salary DESC) AS running_total 

from employees;

**OUTPUT:**

| dept_id | emp_id | first_name | salary    | running_total    |
| ------- | ------ | ---------- | ------    | -------------    |
| 1       | 101    | Alice      | 60000.00  | 60000.00         |
| 1       | 103    | Carol      | 55000.00  | 115000.00        |
| 2       | 102    | Bob        | 75000.00  | 75000.00         |
| 2       | 105    | Emma       | 72000.00  | 147000.00        |
| 3       | 104    | David      | 80000.00  | 80000.00         |

**3️⃣ Find second highest salary using RANK() or DENSE_RANK()**

**✅ Query (using DENSE_RANK)**

SELECT first_name, last_name, salary

FROM (
  
    SELECT
     
       first_name,
      
       last_name,
      
       salary,
      
       DENSE_RANK() OVER (ORDER BY salary DESC) AS salary_rank
   
    FROM employees

)ranked

WHERE salary_rank = 2;

**OUTPUT:**

| first_name | last_name | salary    |
| ---------- | --------- | ------    |
| Bob        | Smith     | 75000.00  |

**4️⃣ Use a CTE to show total hours worked per employee, then filter for those > 100 hours**

**✅ Query**

WITH total_hours AS(
   
    SELECT
        
         e.emp_id,
        
         e.first_name,
        
         e.last_name,
        
         SUM(ep.hours_workes) AS total_hours
   
    FROM employees e
    
    JOIN employee_projects ep ON e.emp_id = ep.emp_id
    
    GROUP BY e.emp_id, e.first_name, e.last_name
)

SELECT *

FROM total_hours

WHERE total_hours > 100;

**OUTPUT**

| emp_id | first_name | last_name | total_hours |
| ------ | ---------- | --------- | ----------- |
| 104    | David      | WHite     | 150         |
| 105    | Emma       | Davis     | 110         |
| 101    | Alice      | BROWn     | 170         |

**5️⃣ Use a CTE to show each department’s highest-paid employee**

**✅ Query**

WITH dept_highest AS (
   
    SELECT 
    
        e.emp_id,
        
        e.first_name,
        
        e.last_name,
        
        e.dept_id,
        
        e.salary,
        
        RANK() OVER (PARTITION BY e.dept_id ORDER BY e.salary DESC) AS dept_rank
    
    FROM employees e
)

SELECT 

    d.dept_name,
    
    dh.first_name,
    
    dh.last_name,
    
    dh.salary

FROM dept_highest dh

JOIN departments d ON dh.dept_id = d.dept_id

WHERE dept_rank = 1;

**OUTPUT:**

| dept_name   | first_name  | last_name | salary    |
| ----------- | ----------  | --------- | ------    |
| Engineering | Alice       | BROWn     | 60000.00  |
| Marketing   | Bob         | Smith     | 75000.00  |
| HR          | David       | WHite     | 80000.00  |



