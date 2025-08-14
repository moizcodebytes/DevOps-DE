
Find employees earning more than the average salary.
```sql

SELECT * 
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees)
```


Get departments where the maximum salary exceeds 100000.
```sql

SELECT department_id
FROM employees
GROUP BY department_id
HAVING MAX(salary) > 100000
```


Find employees who earn the highest salary in their department.
```sql

SELECT *
FROM employees e
WHERE salary = (
  SELECT MAX(salary) 
  FROM employees
  WHERE department_id = e.department_id
)
```


Get employees whose department is located in 'New York'.
```sql

SELECT *
FROM employees
WHERE department_id IN (
  SELECT department_id
  FROM departments
  WHERE location_id = (
    SELECT location_id FROM locations WHERE city = 'New York'
  )
)
```


Find employees who joined after the earliest hire date in department 5.
```sql

SELECT *
FROM employees
WHERE hire_date > (
  SELECT MIN(hire_date)
  FROM employees
  WHERE department_id = 5
)
```


Get employees whose salary is greater than all salaries in department 2.
```sql

SELECT *
FROM employees
WHERE salary > ALL (
  SELECT salary
  FROM employees
  WHERE department_id = 2
)
```


Find employees who work in the same department as 'John Doe'.
```sql

SELECT *
FROM employees
WHERE department_id = (
  SELECT department_id
  FROM employees
  WHERE first_name = 'John' AND last_name = 'Doe'
)
```


Get employees who have the same job as employee ID 101.
```sql

SELECT *
FROM employees
WHERE job_id = (
  SELECT job_id
  FROM employees
  WHERE employee_id = 101
)
```


Find employees earning more than the average salary of their department.
```sql

SELECT *
FROM employees e
WHERE salary > (
  SELECT AVG(salary)
  FROM employees
  WHERE department_id = e.department_id
)
```


Get departments that have no employees.
```sql

SELECT *
FROM departments
WHERE department_id NOT IN (
  SELECT DISTINCT department_id FROM employees
)
```


Find employees who have not been assigned to any project.
```sql

SELECT *
FROM employees
WHERE employee_id NOT IN (
  SELECT DISTINCT employee_id FROM employee_projects
)
```


Find the department with the smallest number of employees.
```sql

SELECT department_id
FROM employees
GROUP BY department_id
ORDER BY COUNT(*) ASC
LIMIT 1
```


Get employees earning within 10% of the highest salary in the company.
```sql

SELECT *
FROM employees
WHERE salary >= (
  SELECT MAX(salary) * 0.9 FROM employees
)
```


Find employees who report to a manager earning more than 90000.
```sql

SELECT *
FROM employees
WHERE manager_id IN (
  SELECT employee_id FROM employees WHERE salary > 90000
)
```


Get employees hired before the oldest hire date in department 3.
```sql

SELECT *
FROM employees
WHERE hire_date < (
  SELECT MIN(hire_date) FROM employees WHERE department_id = 3
)
```


Find employees who earn less than the average salary of job title 'Analyst'.
```sql

SELECT *
FROM employees
WHERE salary < (
  SELECT AVG(salary)
  FROM employees
  WHERE job_id = (SELECT job_id FROM jobs WHERE job_title = 'Analyst')
)
```


Get job titles with average salary higher than company average.
```sql

SELECT job_id
FROM employees
GROUP BY job_id
HAVING AVG(salary) > (SELECT AVG(salary) FROM employees)
```


Find locations with more than 50 employees.
```sql

SELECT location_id
FROM departments
WHERE department_id IN (
  SELECT department_id
  FROM employees
  GROUP BY department_id
  HAVING COUNT(*) > 50
)
```


Get employees whose salary equals the second-highest salary.
```sql

SELECT *
FROM employees
WHERE salary = (
  SELECT MAX(salary)
  FROM employees
  WHERE salary < (SELECT MAX(salary) FROM employees)
)
```


Get employees in departments where all employees earn more than 50000.
```sql

SELECT *
FROM employees
WHERE department_id IN (
  SELECT department_id
  FROM employees
  GROUP BY department_id
  HAVING MIN(salary) > 50000
)
```


Find employees who have the same hire date as employee ID 150.
```sql

SELECT *
FROM employees
WHERE hire_date = (
  SELECT hire_date FROM employees WHERE employee_id = 150
)
```


Get projects handled by employees from 'IT' department.
```sql

SELECT DISTINCT project_id
FROM employee_projects
WHERE employee_id IN (
  SELECT employee_id FROM employees WHERE department_id = (
    SELECT department_id FROM departments WHERE department_name = 'IT'
  )
)
```


Find employees earning more than the average salary in their location.
```sql

SELECT *
FROM employees e
WHERE salary > (
  SELECT AVG(salary)
  FROM employees e2
  JOIN departments d ON e2.department_id = d.department_id
  WHERE d.location_id = (
    SELECT location_id
    FROM departments
    WHERE department_id = e.department_id
  )
)
```


Get managers who manage more than 5 employees.
```sql

SELECT manager_id
FROM employees
GROUP BY manager_id
HAVING COUNT(*) > 5
```


Get employees who do not share their job title with anyone else.
```sql

SELECT *
FROM employees
WHERE job_id IN (
  SELECT job_id
  FROM employees
  GROUP BY job_id
  HAVING COUNT(*) = 1
)
```
