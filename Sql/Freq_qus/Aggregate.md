Find the total number of employees.
```sql

SELECT COUNT(*) AS total_employees FROM employees
```


Find the average salary of all employees.
```sql

SELECT AVG(salary) AS avg_salary FROM employees
```


Get the maximum salary in the company.
```sql

SELECT MAX(salary) AS max_salary FROM employees
```


Get the minimum salary in the company.
```sql

SELECT MIN(salary) AS min_salary FROM employees
```


Count employees per department.
```sql

SELECT department_id, COUNT(*) AS emp_count
FROM employees
GROUP BY department_id
```


Find the total salary paid per department.
```sql

SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id
```


Find average salary per department.
```sql

SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id
```


Get department with highest total salary.
```sql

SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id
ORDER BY total_salary DESC
LIMIT 1
```


Get job title with most employees.
```sql

SELECT job_id, COUNT(*) AS emp_count
FROM employees
GROUP BY job_id
ORDER BY emp_count DESC
LIMIT 1
```


Find departments with more than 10 employees.
```sql

SELECT department_id, COUNT(*) AS emp_count
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 10
```


Get average salary of employees hired after 2015.
```sql

SELECT AVG(salary) AS avg_salary
FROM employees
WHERE hire_date > '2015-01-01'
```


Find the earliest hire date per department.
```sql

SELECT department_id, MIN(hire_date) AS earliest_hire
FROM employees
GROUP BY department_id
```


Find the latest hire date per department.
```sql

SELECT department_id, MAX(hire_date) AS latest_hire
FROM employees
GROUP BY department_id
```


Count employees per location.
```sql

SELECT l.location_id, COUNT(e.employee_id) AS emp_count
FROM employees e
JOIN departments d ON e.department_id = d.department_id
JOIN locations l ON d.location_id = l.location_id
GROUP BY l.location_id
```


Find total salary per job title.
```sql

SELECT job_id, SUM(salary) AS total_salary
FROM employees
GROUP BY job_id
```


Get top 3 highest-paid employees per department.
```sql

SELECT department_id, employee_id, salary
FROM (
  SELECT e.*, 
         ROW_NUMBER() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rn
  FROM employees e
) ranked
WHERE rn <= 3
```


Find percentage of employees in each department.
```sql

SELECT department_id,
       COUNT(*) * 100.0 / (SELECT COUNT(*) FROM employees) AS percentage
FROM employees
GROUP BY department_id
```


Get department with lowest average salary.
```sql

SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id
ORDER BY avg_salary ASC
LIMIT 1
```


Find total projects assigned to each employee.
```sql

SELECT e.employee_id, COUNT(ep.project_id) AS project_count
FROM employees e
LEFT JOIN employee_projects ep ON e.employee_id = ep.employee_id
GROUP BY e.employee_id
```


Get year-wise count of hires.
```sql

SELECT YEAR(hire_date) AS hire_year, COUNT(*) AS emp_count
FROM employees
GROUP BY YEAR(hire_date)
ORDER BY hire_year
```


Find average salary for employees with more than 5 years in company.
```sql

SELECT AVG(salary) AS avg_salary
FROM employees
WHERE TIMESTAMPDIFF(YEAR, hire_date, CURDATE()) > 5
```


Find highest salary per location.
```sql

SELECT l.location_id, MAX(e.salary) AS max_salary
FROM employees e
JOIN departments d ON e.department_id = d.department_id
JOIN locations l ON d.location_id = l.location_id
GROUP BY l.location_id
```


Count distinct job titles per department.
```sql

SELECT department_id, COUNT(DISTINCT job_id) AS distinct_jobs
FROM employees
GROUP BY department_id
```


Get cumulative salary per department ordered by hire date.
```sql

SELECT department_id, hire_date,
       SUM(salary) OVER (PARTITION BY department_id ORDER BY hire_date) AS cumulative_salary
FROM employees
```


Find median salary per department (approximation using percentile).
```sql

SELECT department_id,
       PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary) 
       OVER (PARTITION BY department_id) AS median_salary
FROM employees
```
