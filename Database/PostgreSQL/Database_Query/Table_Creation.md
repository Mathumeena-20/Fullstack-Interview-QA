**🏗️ Step 1: Create Database and Use It**

CREATE DATABASE company_db;
\c company_db;
-----------------------------------------------------------------------------------------------------------------------------------
**🧑‍💼 Step 2: Create Tables**

**1️⃣ employees**

CREATE TABLE employees (
    emp_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    dept_id INT,
    salary NUMERIC(10,2),
    hire_date DATE
);

**2️⃣ departments**

CREATE TABLE departments (
    dept_id SERIAL PRIMARY KEY,
    dept_name VARCHAR(50) NOT NULL,
    location VARCHAR(50)
);

**3️⃣ projects**

CREATE TABLE projects (
    project_id SERIAL PRIMARY KEY,
    project_name VARCHAR(100) NOT NULL,
    start_date DATE,
    end_date DATE,
    budget NUMERIC(12,2)
);


**4️⃣ employee_projects (many-to-many relation)**

CREATE TABLE employee_projects (
    emp_id INT REFERENCES employees(emp_id) ON DELETE CASCADE,
    project_id INT REFERENCES projects(project_id) ON DELETE CASCADE,
    hours_worked INT,
    PRIMARY KEY (emp_id, project_id)
);

------------------------------------------------------------------------------------------------------------------------------------
**📥 Step 3: Insert Sample Data**

**departments**

INSERT INTO departments (dept_id, dept_name, location) VALUES
(1, 'Engineering', 'New York'),
(2, 'Marketing', 'San Francisco'),
(3, 'HR', 'Boston');

**employees**

INSERT INTO employees (emp_id, first_name, last_name, dept_id, salary, hire_date) VALUES
(101, 'Alice', 'Brown', 1, 60000.00, '2019-03-15'),
(102, 'Bob', 'Smith', 2, 75000.00, '2018-07-20'),
(103, 'Carol', 'Johnson', 1, 55000.00, '2021-01-12'),
(104, 'David', 'White', 3, 80000.00, '2017-05-05'),
(105, 'Emma', 'Davis', 2, 72000.00, '2020-08-11');

**projects**

INSERT INTO projects (project_id, project_name, start_date, end_date, budget) VALUES
(201, 'Website Redesign', '2022-01-01', '2022-06-30', 150000.00),
(202, 'Ad Campaign', '2022-03-01', '2022-05-30', 80000.00),
(203, 'HR Automation', '2021-09-15', '2022-03-15', 120000.00);

**employee_projects**

INSERT INTO employee_projects (emp_id, project_id, hours_worked) VALUES
(101, 201, 120),
(102, 202, 90),
(103, 201, 100),
(104, 203, 150),
(105, 202, 110),
(101, 203, 50);

**✅ Step 4: Verify Data**

SELECT * FROM employees;
SELECT * FROM departments;
SELECT * FROM projects;
SELECT * FROM employee_projects;
