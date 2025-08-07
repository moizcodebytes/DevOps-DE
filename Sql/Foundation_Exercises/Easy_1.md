Write a query to output all the columns from the Products table.

```sql
select *
from products;
```

Write a query to find all product_name and category that have a price greater than 100.00 from the Products table.

``` sql
select product_name,category
from products
where price > 100.00;
```

Write a query to calculate the average salary across all companies combined. Rename the column as avg_salary.

```sql
select avg(salary) as avg_salary
from works;
```

Write a query to retrieve the department_name and location of people who live in location that starts with 'S'.

```sql
select department_name,location
from departments
where location like 'S%';
```

Write a query to select all the distinct companies (company_name) in the Works table.

```sql
select distinct company_name
from works;
```

Write a query to find the total count of books whose genre is Fiction.
Note: Output column name should be fiction_count.

```sql
select count(*) as fiction_count
from books
where genre = "Fiction";

```

Write a query to select only the movie names where the ratings are greater than 7 but less than 9.

``` sql
SELECT movie_name
FROM cinema
WHERE rating > 7 AND rating < 9;

```


Write a query to retrieve book_id, title, author and published_year of the books which have NULL rating for their books.

``` sql
select book_id,title,author, published_year
from library
where rating is null;
```

Create a query to retrieve the employee_name, company, and salary for employees in the full-time category, ordered by salary in descending order
``` sql
select employee_name, company, salary
from employees
where category = 'Full-Time'
order by salary desc;

```

Write a query to group the employees by their department and display the total number of employees (as total_employees) in each department.

``` sql
select department,count(*) as total_employees
from employees
group by department;
```

Write a query to retrieve the author_id, author_name, and publication_name for authors whose articles got zero views. The result should be sorted by author_id in ascending order.
Return the result table sorted by id in ascending order.


```sql
select author_id, author_name, publication_name
from views
where view_count = 0
order by author_id ;

```

Write a query to find the names of the top 3 distinct players by highest score who have won matches, including their scores.

Table 1: Players

player_id	player_name	score	rank
1	Alice	1200	5
2	Bob	1500	2
3	Charlie	1300	4
4	David	1600	1
5	Eve	1100	6

Table 2: Matches

match_id	player1	player2	winner	match_date
101	Alice	Bob	Bob	2024-01-15
102	Charlie	David	David	2024-01-16
103	Eve	Bob	Bob	2024-01-17
104	Alice	David	David	2024-01-18
105	Charlie	Eve	Charlie	2024-01-19


``` sql
select distinct player_name,score
from players p
join matches m
on p.player_name = m.winner
order by p.score desc
limit 3;
```

Write a query to retrieve the details of the last five matches played, including the match ID, the names of the players who participated, the name of the winning player, match date, and the final score of the winner.

There are two tables named Players and Matches.
Tables
<img width="761" height="641" alt="image" src="https://github.com/user-attachments/assets/a7bb0aa5-a997-49eb-84e6-cf69b82fcf65" />


``` sql
select m.*,p.score
from 
players p
join matches m 
ON p.player_name = m.winner
order by match_date desc 
limit 5;

```
