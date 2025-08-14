Window Functions (25 Questions)

Get each employee's salary and the average salary in their department.
```sql

SELECT employee_id, department_id, salary,
       AVG(salary) OVER (PARTITION BY department_id) AS dept_avg_salary
FROM employees
```


Rank employees by salary within each department.
```sql

SELECT employee_id, department_id, salary,
       RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS salary_rank
FROM employees
```


Number employees in the company ordered by hire date.
```sql

SELECT employee_id, hire_date,
       ROW_NUMBER() OVER (ORDER BY hire_date) AS row_num
FROM employees
```


Get cumulative salary sum for each department ordered by salary.
```sql

SELECT employee_id, department_id, salary,
       SUM(salary) OVER (PARTITION BY department_id ORDER BY salary) AS running_total
FROM employees
```


Show each employee's salary and the highest salary in their department.
```sql

SELECT employee_id, department_id, salary,
       MAX(salary) OVER (PARTITION BY department_id) AS max_salary_in_dept
FROM employees
```


Show each employee’s salary difference from the department average.
```sql

SELECT employee_id, department_id, salary,
       salary - AVG(salary) OVER (PARTITION BY department_id) AS diff_from_avg
FROM employees
```


Get employees with salary percent rank within their department.
```sql

SELECT employee_id, department_id, salary,
       PERCENT_RANK() OVER (PARTITION BY department_id ORDER BY salary) AS pct_rank
FROM employees
```


Get employees with salary quartile in the company.
```sql

SELECT employee_id, salary,
       NTILE(4) OVER (ORDER BY salary DESC) AS quartile
FROM employees
```


Show previous employee’s salary in salary order.
```sql

SELECT employee_id, salary,
       LAG(salary) OVER (ORDER BY salary) AS prev_salary
FROM employees
```


Show next employee’s salary in salary order.
```sql

SELECT employee_id, salary,
       LEAD(salary) OVER (ORDER BY salary) AS next_salary
FROM employees
```


Get each department’s cumulative employee count by hire date.
```sql

SELECT department_id, hire_date,
       COUNT(*) OVER (PARTITION BY department_id ORDER BY hire_date) AS running_count
FROM employees
```


Get each employee’s salary as a percentage of the department total.
```sql

SELECT employee_id, department_id, salary,
       salary / SUM(salary) OVER (PARTITION BY department_id) * 100 AS pct_of_dept
FROM employees
```


Get employees ranked by hire date company-wide.
```sql

SELECT employee_id, hire_date,
       DENSE_RANK() OVER (ORDER BY hire_date) AS dense_rank_hire
FROM employees
```


Get top 3 highest salaries per department.
```sql

SELECT *
FROM (
  SELECT employee_id, department_id, salary,
         DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rnk
  FROM employees
) t
WHERE rnk <= 3
```


Show each employee’s hire date and earliest hire date in their department.
```sql

SELECT employee_id, department_id, hire_date,
       MIN(hire_date) OVER (PARTITION BY department_id) AS earliest_in_dept
FROM employees
```


Show each employee’s salary compared to highest in company.
```sql

SELECT employee_id, salary,
       salary / MAX(salary) OVER () * 100 AS pct_of_max
FROM employees
```


Get average salary per department and company-wide average on each row.
```sql

SELECT employee_id, department_id, salary,
       AVG(salary) OVER (PARTITION BY department_id) AS dept_avg,
       AVG(salary) OVER () AS company_avg
FROM employees
```


Show the last hire date in each department alongside each employee.
```sql

SELECT employee_id, department_id, hire_date,
       MAX(hire_date) OVER (PARTITION BY department_id) AS last_hire_in_dept
FROM employees
```


Number employees by job title in order of salary.
```sql

SELECT employee_id, job_id, salary,
       ROW_NUMBER() OVER (PARTITION BY job_id ORDER BY salary DESC) AS job_salary_rank
FROM employees
```


Get employees with salary difference from the previous employee in same department.
```sql

SELECT employee_id, department_id, salary,
       salary - LAG(salary) OVER (PARTITION BY department_id ORDER BY salary) AS diff_prev
FROM employees
```


Show cumulative average salary by hire date company-wide.
```sql

SELECT hire_date, salary,
       AVG(salary) OVER (ORDER BY hire_date) AS running_avg_salary
FROM employees
```


Get employees who are in top 10% salary in their department.
```sql

SELECT *
FROM (
  SELECT employee_id, department_id, salary,
         CUME_DIST() OVER (PARTITION BY department_id ORDER BY salary DESC) AS cum_dist
  FROM employees
) t
WHERE cum_dist <= 0.1
```


Show each employee’s tenure in days from the earliest hire in company.
```sql

SELECT employee_id, hire_date,
       DATEDIFF(hire_date, MIN(hire_date) OVER ()) AS days_from_first
FROM employees
```


Get employees with their department’s median salary.
```sql
(MySQL doesn’t have MEDIAN, so using PERCENTILE_CONT in 8.0+)

SELECT employee_id, department_id, salary,
       PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
       OVER (PARTITION BY department_id) AS dept_median
FROM employees
```


Show each department’s salary standard deviation alongside each employee.
```sql

SELECT employee_id, department_id, salary,
       STDDEV(salary) OVER (PARTITION BY department_id) AS dept_stddev
FROM employees
```
