## Basic SQL 

Get all employees from the employees table.
```sql

SELECT * FROM employees;
```
Get all distinct job titles from the employees table.
```sql
SELECT DISTINCT job_title FROM employees;

```
Retrieve first 10 records from employees table.

```sql
SELECT * FROM employees LIMIT 10;

```
Get employee names sorted by last name ascending.
```sql
SELECT first_name, last_name FROM employees ORDER BY last_name ASC;
```

Get all employees hired after 2020-01-01.
```sql

SELECT * FROM employees WHERE hire_date > '2020-01-01';
```

Get employees with salary greater than 50000.
```sql

SELECT * FROM employees WHERE salary > 50000;
```

Get employees whose name starts with 'A'.
```sql

SELECT * FROM employees WHERE first_name LIKE 'A%';
```

Get employees whose name contains 'son'.
```sql

SELECT * FROM employees WHERE last_name LIKE '%son%';
```

Get employees hired between 2015 and 2020.
```sql

SELECT * FROM employees WHERE hire_date BETWEEN '2015-01-01' AND '2020-12-31';
```

Get total number of employees.
```sql

SELECT COUNT(*) FROM employees;

```
Get the maximum salary from employees.
```sql

SELECT MAX(salary) FROM employees;
```

Get the minimum salary from employees.
```sql

SELECT MIN(salary) FROM employees;
```

Get average salary of all employees.
```sql

SELECT AVG(salary) FROM employees;
```

Get sum of all salaries.
```sql

SELECT SUM(salary) FROM employees;
```

Get employees from department 3.
```sql

SELECT * FROM employees WHERE department_id = 3;
```

Get employees not assigned to any department.
```sql

SELECT * FROM employees WHERE department_id IS NULL;
```

Get unique department IDs from employees table.
```sql

SELECT DISTINCT department_id FROM employees;
```

Get employees whose salary is between 40000 and 60000.
```sql

SELECT * FROM employees WHERE salary BETWEEN 40000 AND 60000;
```

Get employee details ordered by hire_date descending.
```sql

SELECT * FROM employees ORDER BY hire_date DESC;
```

Get employees working in 'Sales' department.
```sql

SELECT * FROM employees WHERE department_id = (
  SELECT department_id FROM departments WHERE department_name = 'Sales'
);
```

Get employees with job title 'Manager'.
```sql

SELECT * FROM employees WHERE job_title = 'Manager';
```

Get first name and last name combined as full name.
```sql

SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;
```

Get employees with email ending in '@company.com'.
```sql

SELECT * FROM employees WHERE email LIKE '%@company.com';

```
Get all employees except those from department 5.
```sql

SELECT * FROM employees WHERE department_id <> 5;

```
Get the 5 highest-paid employees.
```sql

SELECT * FROM employees ORDER BY salary DESC LIMIT 5;
```
