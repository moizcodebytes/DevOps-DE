Advanced & Performance (25 Questions)

Create an index on last_name in employees.
```sql

CREATE INDEX idx_last_name ON employees(last_name)
```


Create a composite index on department_id and salary.
```sql

CREATE INDEX idx_dept_salary ON employees(department_id, salary)
```


Show indexes on employees table.
```sql

SHOW INDEXES FROM employees
```


Get the query execution plan for a query.
```sql

EXPLAIN SELECT * FROM employees WHERE last_name = 'Smith'
```


Create a view of high salary employees (>100k).
```sql

CREATE VIEW high_salary_employees AS
SELECT * FROM employees WHERE salary > 100000
```


Drop a view named high_salary_employees.
```sql

DROP VIEW high_salary_employees
```


Create a stored procedure to get employees by department.
```sql

DELIMITER //
CREATE PROCEDURE GetEmployeesByDept(IN dept INT)
BEGIN
  SELECT * FROM employees WHERE department_id = dept;
END //
DELIMITER 
```


Call the stored procedure above for department 2.
```sql

CALL GetEmployeesByDept(2)
```


Create a trigger to update updated_at column on update.
```sql

CREATE TRIGGER update_timestamp
BEFORE UPDATE ON employees
FOR EACH ROW
SET NEW.updated_at = NOW()
```


Create a function to return annual salary from monthly salary.
```sql

DELIMITER //
CREATE FUNCTION AnnualSalary(monthly DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
RETURN monthly * 12;
//
DELIMITER 
```


Create a partitioned table by year of hire_date.
```sql

CREATE TABLE employees_partitioned (
  employee_id INT,
  hire_date DATE
)
PARTITION BY RANGE (YEAR(hire_date)) (
  PARTITION p0 VALUES LESS THAN (2015),
  PARTITION p1 VALUES LESS THAN (2020),
  PARTITION p2 VALUES LESS THAN MAXVALUE
)
```


Optimize a query fetching top salaries per department using index.
```sql

CREATE INDEX idx_dept_salary_desc ON employees(department_id, salary DESC)
```


Get total rows in a large table quickly (estimate).
```sql

SELECT TABLE_ROWS
FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_NAME = 'employees'
```


Get slow queries log file location.
```sql

SHOW VARIABLES LIKE 'slow_query_log_file'
```


Enable slow query logging.
```sql

SET GLOBAL slow_query_log = 'ON'
```


Create a temporary table from employees earning >80k.
```sql

CREATE TEMPORARY TABLE temp_high_salary
SELECT * FROM employees WHERE salary > 80000
```


Drop a temporary table.
```sql

DROP TEMPORARY TABLE temp_high_salary
```


Create a table with foreign key constraint.
```sql

CREATE TABLE orders (
  order_id INT PRIMARY KEY,
  employee_id INT,
  FOREIGN KEY (employee_id) REFERENCES employees(employee_id)
)
```


Alter a table to add a new column.
```sql

ALTER TABLE employees ADD COLUMN phone_number VARCHAR(15)
```


Alter a table to modify a column type.
```sql

ALTER TABLE employees MODIFY COLUMN salary DECIMAL(12,2)
```


Drop a column from a table.
```sql

ALTER TABLE employees DROP COLUMN phone_number
```


Create a unique constraint on email.
```sql

ALTER TABLE employees ADD CONSTRAINT unique_email UNIQUE (email)
```


Create a full-text index on job_description.
```sql

CREATE FULLTEXT INDEX idx_job_desc ON jobs(job_description)
```


Backup a MySQL database.
```sql

mysqldump -u root -p mydatabase > backup.sql

```
Restore a MySQL database from backup.
```sql

mysql -u root -p mydatabase < backup.sql

```
