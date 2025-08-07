## READ 

READ is one of the operations of CRUD. In order to read the data from a table 'SELECT' clause is used.

### Query Mechanics

Each time a query is sent to the server, the server checks the following things prior to statement execution:
* permission to execute the statement?
* permission to access the desired data?
* statement syntax correct?

If the statement passes these three tests, then the query is handed to the query **optimizer**, whose job it is to determine the most efficient way to execute your query. The optimizer will look at such things as the order in which to join the tables named in your from clause and what indexes are available, and then picks an execution plan, which the server uses to execute your query.

### Query Clauses

<img width="793" height="362" alt="image" src="https://github.com/user-attachments/assets/f8689eb5-c316-4bcb-b712-9f2e611ae6dd" />


#### SELECT and FROM

**SELECT** is the first Clause of the statement but it is last one that executes in query.    
**FROM** is the clause which detemines from where to read the data.


*Show me all the columns and all the rows in the department table.*

``` SQL
SELECT * FROM department;
```


*Show me only dept_id, name and all the rows in the department table.*

``` SQL

SELECT dept_id,name FROM department;
```

SELECT STATEMENTs can have below added in SELECT    

* Literals, such as numbers or strings
* Expressions, such as transaction.amount * −1
* Built-in function calls, such as ROUND(transaction.amount, 2)
* User-defined function calls

``` SQL
SELECT emp_id,
'ACTIVE',
emp_id * 3.14159,
UPPER(lname)
FROM employee;

```
 | emp_id | ACTIVE | emp_id * 3.14159 | UPPER(lname) |
 |--------|--------|------------------|--------------|
 |      1 | ACTIVE |          3.14159 | SMITH        |
 |      2 | ACTIVE |          6.28318 | BARKER       |
 |      3 | ACTIVE |          9.42477 | TYLER        |
 |      4 | ACTIVE |         12.56636 | HAWTHORNE    |
 |      5 | ACTIVE |         15.70795 | GOODING      |

 

**Alias** : In order assingn a name to column that will be easily used in further query and displayed in result set.

``` SQL
SELECT emp_id,
'ACTIVE',
emp_id * 3.14159 as empid_x_pi,
UPPER(lname) last_name_upper
FROM employee;

```
 | emp_id | status | empid_x_pi | last_name_upper |
 |--------|--------|------------|-----------------|
 |      1 | ACTIVE |    3.14159 | SMITH           |
 |      2 | ACTIVE |    6.28318 | BARKER          |
 |      3 | ACTIVE |    9.42477 | TYLER           |



 **DISTINCT **  : To select only distinct values from a table.

 ``` sql

Select distinct city from places;

```


