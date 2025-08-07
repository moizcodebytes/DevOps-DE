## WHERE

**WHERE** is one of the clause from READ OPERATIONS which contains *Filter Condition*.        
The **WHERE** clause is the mechanism for filtering out unwanted rows from your result set.

``` SQL
SELECT emp_id, fname, lname, start_date, title
FROM employee
WHERE title = 'Head Teller';

```

There can be one or more filter condition seperated by operators AND,OR,NOT.    

``` SQL
SELECT emp_id, fname, lname, start_date, title
FROM employee
WHERE title = 'Head Teller'
 AND start_date > '2006-01-01';


SELECT emp_id, fname, lname, start_date, title
FROM employee
WHERE title = 'Head Teller'
 OR start_date > '2006-01-01';
```

Combination of Operators can also be used for better filtering

``` SQL
SELECT emp_id, fname, lname, start_date, title
FROM employee
WHERE (title = 'Head Teller' AND start_date > '2006-01-01')
 OR (title = 'Teller' AND start_date > '2007-01-01');
```

NOT

``` SQL
SELECT * FROM EMPLOYEE
WHERE end_date IS NULL
  AND NOT (title = 'Teller' OR start_date < '2007-01-01')
```

## Condition building 
A condition is made up of one or more **expressions** coupled with one or more **operators**.

An Expression can be
* Number
* Column in table or view
* String literal as 'Teller'
* Built in function as Concat('learning',' ','SQL')
* Subquery
* A list of expressions as ('Teller','Head Teller','Operations Manager')

Operators Can be
* Comparison operators, such as =, !=, <, >, <>, LIKE, IN, and BETWEEN
* Arithmetic operators, such as +, −, *, and /

## Condition types
* EQUALITY    
Column =  Expression
    
```SQL
 title = 'Teller'  # String
 fed_id = '111-11-1111' # Number
 amount = 375.25 # Number
 dept_id = (SELECT dept_id FROM department WHERE name = 'Loans' #subquery

```

* INEQUALITY   
Column <> Expression   
Column != Expression   

``` SQL
WHERE pt.name <> 'Customer Accounts
```

* RANGE
To check if the expression falls under particular range.    

Column > expression      Greater than      
Column < expression      Less than      
Column >= expression     Greater than or equal to      
Column <= expression     less than or equal to      

```SQL
SELECT emp_id, fname, lname, start_date
FROM employee
WHERE start_date < '2007-01-01';

SELECT emp_id, fname, lname, start_date
FROM employee
WHERE start_date < '2007-01-01'
AND start_date >= '2005-01-01';

```

* BETWEEN and AND
  When we have both upper limit and lower limit we use **BETWEEN**  and **AND** operator rather than two seperate condition like above.

``` SQL
SELECT emp_id, fname, lname, start_date
FROM employee
WHERE start_date BETWEEN '2007-01-01' AND  '2005-01-01';

### NUMBERS
SELECT account_id, product_cd, cust_id, avail_balance
WHERE avail_balance BETWEEN 3000 AND 5000;

### STRINGS

SELECT cust_id, fed_id
FROM customer
WHERE cust_type_cd = 'I'
AND fed_id BETWEEN '500-00-0000' AND '999-99-9999';

```
**NOTE : Always give lower limit after BETWEEN and Upper limit after AND.**

* IN
When we want to check if the expression exists in the set of expressions we use IN operator to check.

``` sql
 SELECT account_id, product_cd, cust_id, avail_balance
 FROM account
 WHERE product_cd IN ('CHK','SAV','CD','MM');
```
* NOT IN

When we want to check if the expression does not exists in the set of expressions we use NOT IN operator to check.

```sql
SELECT account_id, product_cd, cust_id, avail_balance
FROM account
WHERE product_cd NOT IN ('CHK','SAV','CD','MM');
```

* SUB QUERIES
Rather than writing the set of expression we can use subquery to generate the set.

``` sql
SELECT account_id, product_cd, cust_id, avail_balance
FROM account
WHERE product_cd IN (SELECT product_cd FROM product WHERE product_type_cd = 'ACCOUNT');
```

* LIKE
When we want to filter the data based on partial string matches we use LIKE operator with WildCards

<img width="824" height="259" alt="image" src="https://github.com/user-attachments/assets/bf4e4405-73a8-4a32-b69c-2e2b8b3f9237" />    



``` sql
SELECT lname
FROM employee
WHERE lname LIKE '_a%e%';

```

 | lname     |
 |-----------|
 | Barker    |
 | Hawthorne |
 | Parker    |
 | Jameson   |
 

``` sql
SELECT emp_id, fname, lname
FROM employee
WHERE lname LIKE 'F%' OR lname LIKE 'G%';
```

 | emp_id | fname | lname    |
 |--------|-------|----------|
 |      5 | John  | Gooding  |
 |      6 | Helen | Fleming  |
 |      9 | Jane  | Grossman |
 |     17 | Beth  | Fowler   |

 REGEX

 ``` SQL
SELECT emp_id, fname, lname
FROM employee
WHERE lname REGEXP '^[FG]';
```

 | emp_id | fname | lname    |
 |--------|-------|----------|
 |      5 | John  | Gooding  |
 |      6 | Helen | Fleming  |
 |      9 | Jane  | Grossman |
 |     17 | Beth  | Fowler   |

 ## NULL

* NULL is absesce of value
* An expression can be null, but it can never equal null.
* Two nulls are never equal to each other

**IS NULL**

``` SQL
SELECT emp_id, fname, lname, superior_emp_id
FROM employee
WHERE superior_emp_id IS NULL;
```

**IS NOT NULL**

``` sql
SELECT emp_id, fname, lname, superior_emp_id
FROM employee
WHERE superior_emp_id IS NOT NULL;
