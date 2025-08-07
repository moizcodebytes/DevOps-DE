# TABLES

``` sql
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    column3 datatype constraint,
    ...
);
```

## Data types 

1. Character Data    
    char(20) : It is fixed length data type and is right padded with spaces and always consume same number of bytes specified. Max : 255 bytes    
    varchar(20) : It is variable length data type and will not be right padded with spaces and do not consume same number of bytes. Max : 65355 bytes 

2. Character Sets : To store large number of chars for languages other than english requires multiple bytes of storage. Such characters are called Multibyte Character set.
    ``` sql
    Show CHARACTER SET;
    ```

    To Choose  character set
    ```sql
    varchar(20) character set utf8
    ```
    To set the default character set for entire DB
   ```sql
   Create database <dbname> character set utf8;
   ```

3.  Text :  To store the data that might exceeds 64KB storage for varchar coloumns. Then below text data types should be used.

      |Text type|Maximum number of bytes |
      |-------------|-------------------|
      |Tinytext|255|
      |Text|65,535|
      |Mediumtext |16,777,215|
      |Longtext|4,294,967,295|

    **NOTE :  Varchar would be adequate for any length of data but for storing documents choose either the mediumtext or longtext type.**

4. Numeric :  To store any numeric data.
       Int and Float are basically used for numeric values.

5.  Temporal :  To store date and time values.

      |  Type|Default format|
      |------------|------------|
      |Date| YYYY-MM-DD|
      |Datetime|YYYY-MM-DD HH:MI:SS|
      |Timestamp|YYYY-MM-DD HH:MI:SS|
      |Year|YYYY|
      |Time|HH:MM:SS|


## Constraints   

Are rules to limit the type of data that can go into table. This ensures the accuracy and reliability of data mainitained.

1. **NOT NULL** : Ensures Columns cannot have a NULL value.
2. **Unique** : To Ensure Column values are unique.
3. **Primary Key**: To uniquely identify each record in table. Combines not NUll and Unique. Each table can have only one primary key but one primary key can be combination of multiple columns "composite key".
4. **Foreign Key** : Establishes a relationship between two tables by linking a column in one table to the primary key in another. FK constraint is used to prevent actions that would destroy links between two tables. FK is a field that refers to PK of another table. The table with FK is called child table and the table with PK is called parent or refereced table.
5. **Check** : Ensures that all values in a column satisfy a specific condition. (NOT SUPPORTED IN MYSQL)
```
gender varchar(1) Check ('M','F") ;
```
6. **Default** : Assigns a default value to a column if no value is provided .
   









