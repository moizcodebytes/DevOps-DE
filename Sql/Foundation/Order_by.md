# ORDER BY

In general, the results are not in particular order. To set a particular order we use ORDER BY Clause on the required column.

**The order by clause is the mechanism for sorting your result set using either raw column data or expressions based on column data **

``` sql
SELECT open_emp_id, product_cd
FROM account
ORDER BY open_emp_id;
```

Sort by multiple columns , the result is sorted by first column followed by second, third.    
``` sql
SELECT open_emp_id, product_cd
FROM account
ORDER BY open_emp_id,product_cd;
```

#### DESC and ASC

By default the result is sorted by ASCENDING order. To change the order type we can use DESC (Descending) and ASC (ASCENDING).   

``` sql
SELECT open_emp_id, product_cd
FROM account
ORDER BY avail_bal DESC;
```
### SORTING NULLS

``` SQL
ORDER BY Date NULLS LAST
ORDER BY Date NULLS FIRST
```

### Sorting based on expressions

