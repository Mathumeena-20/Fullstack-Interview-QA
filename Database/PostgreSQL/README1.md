## 🗄️ Sample Database: `company_db`

### 1️⃣ **Table: employees**

| emp_id | first_name | last_name | dept_id | salary | hire_date  |
| ------ | ---------- | --------- | ------- | ------ | ---------- |
| 101    | Alice      | Brown     | 1       | 60000  | 2019-03-15 |
| 102    | Bob        | Smith     | 2       | 75000  | 2018-07-20 |
| 103    | Carol      | Johnson   | 1       | 55000  | 2021-01-12 |
| 104    | David      | White     | 3       | 80000  | 2017-05-05 |
| 105    | Emma       | Davis     | 2       | 72000  | 2020-08-11 |

---

### 2️⃣ **Table: departments**

| dept_id | dept_name   | location      |
| ------- | ----------- | ------------- |
| 1       | Engineering | New York      |
| 2       | Marketing   | San Francisco |
| 3       | HR          | Boston        |

---

### 3️⃣ **Table: projects**

| project_id | project_name     | start_date | end_date   | budget |
| ---------- | ---------------- | ---------- | ---------- | ------ |
| 201        | Website Redesign | 2022-01-01 | 2022-06-30 | 150000 |
| 202        | Ad Campaign      | 2022-03-01 | 2022-05-30 | 80000  |
| 203        | HR Automation    | 2021-09-15 | 2022-03-15 | 120000 |

---

### 4️⃣ **Table: employee_projects**

| emp_id | project_id | hours_worked |
| ------ | ---------- | ------------ |
| 101    | 201        | 120          |
| 102    | 202        | 90           |
| 103    | 201        | 100          |
| 104    | 203        | 150          |
| 105    | 202        | 110          |
| 101    | 203        | 50           |

---

## ✅ Practice Sections

---

### 🔹 **Level 1 — Basic Queries**

1. Select all employees working in the **Engineering** department.
2. Find employees hired after **2020-01-01**.
3. Display **employee full name and salary** for all employees.
4. List **distinct department locations**.
5. Find the **total number of employees** in the company.

---

### 🔹 **Level 2 — Filtering & Sorting**

6. Find employees with a **salary greater than 70000**, sorted by salary descending.
7. Find employees in **New York or Boston**.
8. List employees whose last name **starts with ‘D’**.
9. Show employees **not assigned** to any project.
10. Show top **2 highest-paid employees**.

---

### 🔹 **Level 3 — Aggregations (GROUP BY, HAVING)**

11. Find the **average salary per department**.
12. List departments where **average salary > 65000**.
13. Count how many employees work in each location.
14. Find the **total hours worked** on each project.
15. Which employee has worked **the most hours overall**?

---

### 🔹 **Level 4 — JOINs**

16. Show **employee names with their department name**.
17. Display **project names** and the **employees working on them**.
18. Find employees who worked on **multiple projects**.
19. Show **department name** and **total salary** of employees in that department.
20. Find all employees who worked on a project **with a budget > 100000**.

---

### 🔹 **Level 5 — Subqueries**

21. Find employees who earn **more than the average salary**.
22. List employees who have **never worked on any project**.
23. Show departments where **no employees** earn below 60000.
24. Get the **project name** where the **highest-paid employee** worked.
25. Find the employee who joined **most recently**.

---

### 🔹 **Level 6 — Advanced (Window Functions, CTEs)**

26. Rank employees by salary (highest → lowest).
27. Calculate the **running total of salaries** by department.
28. Find **second highest salary** using `RANK()` or `DENSE_RANK()`.
29. Use a CTE to show **total hours worked per employee**, then filter for those > 100 hours.
30. Use a CTE to show each department’s **highest-paid employee**.

