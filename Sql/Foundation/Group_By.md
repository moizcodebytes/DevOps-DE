# GROUP BY

GROUP BY is a clause used to group the data in table based column specified. The output is one row for each distinct value of specified column.

``` sql
SELECT open_emp_id
FROM account
WHERE open_emp_id > 1
GROUP BY open_emp_id
```
## Group Filter Conditions
The order of execution while using GROUP BY is first WHERE is Executed then GROUP BY . In order to filter out the grouped data we use **HAVING**. 

```sql
SELECT open_emp_id, COUNT(*) how_many
FROM account
GROUP BY open_emp_id
HAVING COUNT(*) > 4;

SELECT product_cd, SUM(avail_balance) prod_balance
WHERE status = 'ACTIVE'
 GROUP BY product_cd
 HAVING SUM(avail_balance) >= 10000
```


# Aggregate Functions

Max() Returns the maximum value within a set
Min() Returns the minimum value within a set
Avg() Returns the average value across a set
Sum() Returns the sum of the values across a set
Count() Returns the number of values in a set

``` sql
SELECT MAX(avail_balance) max_balance,
MIN(avail_balance) min_balance,
AVG(avail_balance) avg_balance,
SUM(avail_balance) tot_balance,
COUNT(*) num_accounts
FROM account
WHERE product_cd = 'CHK'
```


## Single-Column Grouping

Grouping by single column.

```sql
SELECT product_cd, SUM(avail_balance) prod_balance
FROM account
GROUP BY product_cd;
```

## Mutiple-Column Grouping

Grouping by multiple columns. 

``` sql
SELECT product_cd, open_branch_id,
SUM(avail_balance) tot_balance
FROM account
GROUP BY product_cd, open_branch_id;
```


## Grouping via Expressions

```sql
SELECT EXTRACT(YEAR FROM start_date) year,
COUNT(*) how_many
FROM employee
GROUP BY EXTRACT(YEAR FROM start_date)
```

## Generating Rollups

For instance we need to aggregated output of columns and total aggregated value of grouped.

```sql
SELECT product_cd, open_branch_id,
SUM(avail_balance) tot_balance
FROM account
 GROUP BY product_cd, open_branch_id WITH ROLLUP
```

The output has new record which is total of grouped columns

| product_cd | open_branch_id | tot_balance |
|-------------|-----------------|----------|
 | BUS        |              2 |     9345.55 |
 | BUS        |              4 |        0.00 |
 | BUS        |           NULL |     9345.55 |
 | CD         |              1 |    11500.00 |
 | CD         |              2 |     8000.00 |
 | CD         |           NULL |    19500.00 |
 | CHK        |              1 |      782.16 |
 | CHK        |              2 |     3315.77 |
 | CHK        |              3 |     1057.75 |
 | CHK        |              4 |    67852.33 |
 | CHK        |           NULL |    73008.01 |
 
 
## HANDLING NULLS

Null values are ignored by aggregate functions. 
