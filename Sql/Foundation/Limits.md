# LIMIT

To limit the number of rows in Result set. We use LIMIT and OFFSET Clauses.

* The LIMIT row_count determines the number of rows (row_count) returned by the query.    
* The OFFSET row_to_skip clause skips the row_to_skip rows before beginning to return the rows.    

```sql

Select * 
FROM employee
LIMIT 5

```

**OFFSET** skips the rows before results

Below Query will give 4th Highest Salary from table.
``` SQL
SELECT *
FROM employee
order by salary desc
Limit 1 
OFFSET 3
```
