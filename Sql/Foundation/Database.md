## DATABASE

#### A database is a structured set of data stored on a computer. Databases should be organized to efficiently store, retrieve, and manage information.

### RELATIONAL DATABASE

The data in database is highly structured. Relational Database is one of the type of database.
Data is organized into tables that contain columns and rows, with a unique key identifying each row. 
The columns represent different variables (or attributes), and the rows are measurements (or instances) of those variables.
In a relational database, data is typically stored in multiple tables. However, data from different tables can be combined. 
This can make the whole database quite flexible.

Example :

Employee_table
|Id|name|salary|
|---|---|------|
|1|john|100|
|2|alex|200|
|3|amit|200|

department_table
|id|dept|
|---|---|
|1|Accounts|
|2|Finance|
|3|Accounts|

There are different tables but they have id as comman which can be used to join the data.


### SQL DATABASE

Relational databases are called SQL databases because SQL is the language designed to talk to relational databases.
This means the SQL language is used to access and modify the data within an SQL database. 

SQL Database Options

1.MYSQL
2.SQLite
3.SQL Server

## Commands

To Create a Database

``` sql
Create database sql_practice;
```

To list databases

``` sql
Show databases;

```

To go into a certain database

``` sql
use sql_practice;
```

To know the working database

``` sql
select database();
```

To Drop database

``` sql
Drop database sql_practice;

```
