List employees with their department names.
```sql

SELECT e.first_name, e.last_name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id
```


List all employees and their department names (include employees without departments).
```sql

SELECT e.first_name, e.last_name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id
```


List all departments and the employees in them (include empty departments).
```sql

SELECT d.department_name, e.first_name, e.last_name
FROM departments d
LEFT JOIN employees e ON d.department_id = e.department_id
```


Find employees who work in the same city as their department location.
```sql

SELECT e.first_name, e.last_name, l.city
FROM employees e
JOIN departments d ON e.department_id = d.department_id
JOIN locations l ON d.location_id = l.location_id
WHERE e.city = l.city
```


Get employees and their managers’ names.
```sql

SELECT e.first_name AS employee_first, e.last_name AS employee_last,
       m.first_name AS manager_first, m.last_name AS manager_last
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.employee_id
```


Find employees and their job titles.
```sql

SELECT e.first_name, e.last_name, j.job_title
FROM employees e
JOIN jobs j ON e.job_id = j.job_id
```


Get employees and their salary grades.
```sql

SELECT e.first_name, e.last_name, sg.grade_level
FROM employees e
JOIN salary_grades sg 
ON e.salary BETWEEN sg.min_salary AND sg.max_salary
```


List employees with their project names.
```sql

SELECT e.first_name, e.last_name, p.project_name
FROM employees e
JOIN employee_projects ep ON e.employee_id = ep.employee_id
JOIN projects p ON ep.project_id = p.project_id
```


Find employees who do not have a project assigned.
```sql

SELECT e.first_name, e.last_name
FROM employees e
LEFT JOIN employee_projects ep ON e.employee_id = ep.employee_id
WHERE ep.project_id IS NULL
```


Get departments without employees.
```sql

SELECT d.department_name
FROM departments d
LEFT JOIN employees e ON d.department_id = e.department_id
WHERE e.employee_id IS NULL
```


List employees along with country they work in.
```sql

SELECT e.first_name, e.last_name, c.country_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id
JOIN locations l ON d.location_id = l.location_id
JOIN countries c ON l.country_id = c.country_id
```


Find all employee–department–manager combinations.
```sql

SELECT e.first_name, e.last_name, d.department_name,
       m.first_name AS manager_first, m.last_name AS manager_last
FROM employees e
JOIN departments d ON e.department_id = d.department_id
LEFT JOIN employees m ON e.manager_id = m.employee_id
```


List employees working in ‘IT’ department and their job titles.
```sql

SELECT e.first_name, e.last_name, j.job_title
FROM employees e
JOIN departments d ON e.department_id = d.department_id
JOIN jobs j ON e.job_id = j.job_id
WHERE d.department_name = 'IT'
```


Get employees with department and location info.
```sql

SELECT e.first_name, e.last_name, d.department_name, l.city
FROM employees e
JOIN departments d ON e.department_id = d.department_id
JOIN locations l ON d.location_id = l.location_id
```


Get employees with their manager’s department.
```sql

SELECT e.first_name, e.last_name, md.department_name AS manager_department
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.employee_id
LEFT JOIN departments md ON m.department_id = md.department_id
```


Find projects and number of employees in each.
```sql

SELECT p.project_name, COUNT(ep.employee_id) AS employee_count
FROM projects p
LEFT JOIN employee_projects ep ON p.project_id = ep.project_id
GROUP BY p.project_name
```


Get employees with same job title as ‘John Doe’.
```sql

SELECT e.first_name, e.last_name
FROM employees e
WHERE e.job_id = (
  SELECT job_id FROM employees WHERE first_name = 'John' AND last_name = 'Doe'
)
```


List employees whose manager works in a different department.
```sql

SELECT e.first_name, e.last_name
FROM employees e
JOIN employees m ON e.manager_id = m.employee_id
WHERE e.department_id <> m.department_id
```


Find employees who share the same department with at least one other employee.
```sql

SELECT DISTINCT e.first_name, e.last_name
FROM employees e
JOIN employees e2 ON e.department_id = e2.department_id
WHERE e.employee_id <> e2.employee_id
```


Get employees who work in the same city as ‘Mary Smith’.
```sql

SELECT e.first_name, e.last_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id
JOIN locations l ON d.location_id = l.location_id
WHERE l.city = (
  SELECT l2.city
  FROM employees e2
  JOIN departments d2 ON e2.department_id = d2.department_id
  JOIN locations l2 ON d2.location_id = l2.location_id
  WHERE e2.first_name = 'Mary' AND e2.last_name = 'Smith'
)
```


List employees and their training courses.
```sql

SELECT e.first_name, e.last_name, t.course_name
FROM employees e
JOIN employee_training et ON e.employee_id = et.employee_id
JOIN training t ON et.course_id = t.course_id
```


List employees and their benefits.
```sql

SELECT e.first_name, e.last_name, b.benefit_name
FROM employees e
JOIN employee_benefits eb ON e.employee_id = eb.employee_id
JOIN benefits b ON eb.benefit_id = b.benefit_id
```


Find departments with average salary > 60000.
```sql

SELECT d.department_name, AVG(e.salary) AS avg_salary
FROM departments d
JOIN employees e ON d.department_id = e.department_id
GROUP BY d.department_name
HAVING AVG(e.salary) > 60000
```


Get employees with their latest performance review date.
```sql

SELECT e.first_name, e.last_name, MAX(pr.review_date) AS last_review
FROM employees e
JOIN performance_reviews pr ON e.employee_id = pr.employee_id
GROUP BY e.first_name, e.last_name
```


Find employees who have never taken any training.
```sql

SELECT e.first_name, e.last_name
FROM employees e
LEFT JOIN employee_training et ON e.employee_id = et.employee_id
WHERE et.course_id IS NULL
```
