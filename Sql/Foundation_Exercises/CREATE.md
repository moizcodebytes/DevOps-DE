# Table Creation

### Step1 : Design

Before creating a table it is important to uderstand what type of information table will hold and what type columns we need.

Ex : To create person table, we need below information that describes a person.
* Name
* Gender
* Birth data
* Address
* Favorite foods .....

Next step to understand data types needed and any constraints.

Person Table
Column | Type| Constraints|
|------|------|----------|
|Name|Varchar(40)||
|Gender|Char(1)|M,F|
|Birth date|Date||
|Address|Varcha(100)||
|Favorite Food|Varchar(200)||


### Step2 :  Refinement

Issue with Step 1:  
      1. Name is actually compound object having firstname and lastename.    
      2. No uniqueness in table.
      3. Address is also compound as street,city,pincode.
      4. Favourite food can be big list of items.
Fix :
      1. Seperate column for firstname and lastname.
      2. New column as primary key for uniqueness.
      3. Seperate column for address.
      4. Seprate table for favorite food with foreign key.

Person Table   

  |Column | Type| Constraints|
  |------|------|----------|
  |Person_id|Smallint| primary key
  |First_Name|Varchar(20)||
  |Last_Name|Varchar(20)||
  |Gender|Char(1)|M,F|
  |Birth date|Date||
  |Street|Varcha(30)||
  |City|Varchar(20)||
  |State|Varchar(20)||
  |Country|Varchar(20)||
  |Postal_code|Varchar(20)||

Favorite Food Table

 |Column | Type| Constraints|
  |------|------|----------|
  |Person_id|Smallint| Foreign key
  |Food|Varchar(20)||

The person_id and food columns comprise the primary key of the favorite_food table, and the person_id column is also a foreign key to the person table.

## Create Table 

``` SQL

 CREATE TABLE IF NOT EXISTS person
 (person_id SMALLINT ,
  fname VARCHAR(20) NOT NULL,
  lname VARCHAR(20) NOT NULL,
  gender ENUM('M','F'),
  birth_date DATE NOT NULL,
  street VARCHAR(30) NOT NULL,
  city VARCHAR(20) NOT NULL,
  state VARCHAR(20) NOT NULL,
  country VARCHAR(20) NOT NULL,
  postal_code VARCHAR(20) NOT NULL,
  CONSTRAINT pk_person PRIMARY KEY (person_id)
 );

CREATE TABLE favorite_food
(person_id SMALLINT NOT NULL ,
food VARCHAR(20),
 CONSTRAINT pk_favorite_food PRIMARY KEY (person_id, food),
 CONSTRAINT fk_fav_food_person_id FOREIGN KEY (person_id)
 REFERENCES person (person_id)
 );

```

## INSERT

``` SQL

INSERT INTO person (person_id, fname, lname, gender, birth_date,street, city, state, country, postal_code) VALUES (null, 'Susan','Smith', 'F', '1975-11-02','23 Maple St.', 'Arlington', 'VA', 'USA', '20220');

INSERT INTO favorite_food (person_id, food) VALUES (1, 'pizza');
INSERT INTO favorite_food (person_id, food) VALUES (1, 'cookies');
INSERT INTO favorite_food (person_id, food) VALUES (1, 'nachos')
```

If there are only limited values to be inserted

``` SQL
INSERT INTO person (person_id, fname, lname, gender, birth_date) VALUES (null, 'William','Turner', 'M', '1972-05-27');
```
