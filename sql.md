# Databases

Create Databases

CREATE DATABASE endrisql;
USE DATABASES;
Read Only in SQL
    ALTER DATABASE mydb READ ONLY = 1;
    ALTER DATABASE mydb READ ONLY = 0;

# Rows and Columns

Create Tables
Inside of tables we have Columns
Next to Columns we have Data Types
Select Columns
Rename Tables
Drop Tables
Alter Tables, adding Columns
Select Tables
Rename Columns
    Dont forget to set the datatype for the column
Moving Columns
Select
We can run multiple SQL Statement
Drop Column

COMMANDS USED:

    - CREATE, TABLE, ADD, COLUMN, specify data types such as INT, VARCHAR, DECIMAL, DATE, RENAME, DROP, ALTER, MODIFY

# Insert Rows

Now lets Insert a ROW in a table

COMMANDS USED:

    - INSERT, INTO, VALUES (data goes here), make sure to list in order and specify the data types
    - INSERT MULTIPLE VALUES , INSERT INTO employees VALUES (), (), (), ();
    - Attempt to insert with missing data (will face issue)
    - Attempt to insert with empty fields (no issues, we will have null on the fields)

# SELECT
## WHERE, HAVING
    HAVING clause is similar to the WHERE clause, but it can only be used with aggregate functions while WHERE can’t. For example, in the below query, we are choosing all the movie genres that have at least 50 movies in their category

    - Query all data from tables
    - SELECT with specific colums
        SELECT, first_name, last_name
    - WHERE clause
        SELECT * FROM employees WHERE employee_id = 2; 
        SELECT * FROM employees WHERE first_name = "endri";
    - Operators
        greater than , less than, equal, not equal
        SELECT * FROM employees WHERE hourly_pay >= 15;
    - IS keyword
    - IS NOT keyword
        SELECT * FROM employees WHERE hire_date is NULL;



# Update and Delete

    -UPDATE, SET, WHERE (single columns)
    -UPDATE, SET, WHERE (multiple columns columns)
    -UPDATE ALL ROWS IN one COLUMN, use only SET without WHERE CLAUSE
        UPDATE employees
        SET hourly_pay = 10.25;
    -DELETE A ROW FROM A TABLE
        DELETE FROM employees; (wrong approach, will delete all the rows)
        DELETE FROM employees WHERE employee_id = 6; (done)

# Autocommit, commit, rollback
    Autocommit is ON by default
    Lets turn it to OFF, after we turn it off we have to manually save each transaction, creates a save point
        SET AUTOCOMMIT = OFF;
    Lets create a SAVE POINT using COMMIT keyword
        COMMIT;
    Now delete all info within the table
        DELETE FROM employees;
    Now lets undo the changes
        ROLLBACK; (COMMIT the last one)
        SELECT * FROM employees

# Current Date and Current Time

    - DATE
    - TIME
    - DATETIME
    - CURRENT_DATE() , +1 or -1
    - CURRENT_TIME() , NOW()

# Unique Constraint

    All Values in a COLUMN are different
    - We set that the data type in UNIQUE and cannot be assigned anywhere
    - Can be created during the TABLE creation
    - or can be added later after the TABLE is been created, ADD CONSTRAINT UNIQUE
    - duplicate index/duplicate entry

# NOT NULL

    NOT NULL is a constraint
    - Can be created during the Table creation
    - Can be added after the Table has been created
    - Will be applied on COLUMN
    ALTER TABLE products MODIFY price DECIMAL (4,2) NOT NULL
    - Lets test that NULL CONSTRAINT
        - Cant be null

# CHECK

    CHECK IS CONSTRAINT
    Can be used to limit what values can be placed in a column
    - CHECK can be renamed CONSTRAINT chk_hourly_pay CHECK (hourly_pay >= 10.00)
    - Can be created during the TABLE creation
    - Can be added after the TABLe has been created
    - Try to add a column with hourly_pay less than 5 dollars, check_hourly_pay is violated
    - Delete a CHECK
        - DROP CHECK 'name that you gave before'

# DEFAULT 
## Note: Safe Mode
## Note: Explicit with DEFAULT

    Default is a constraint
    Default is used to specify the same VALUE for all the column 
    We have a TABLE called products
    Lets add some data there
    - Can be created during the TABLE creation
    - Can be added after the TABLe has been created
    - Transaction TABLE, combined with DEFAULT, DATETIME, NOW  (we dont need explicit) (at 1h)

# PRIMARY KEY
# AUTO_INCREMENT

    - PRIMAY KEY is used only in one table and is used for ID mostly
    - AUTO_INCREMENT is combined with PRIMARY KEY, they will be applied on ID mostly, after you entered data the ID will be auto incremented automatically , will be UNIQUE and NOT NULL

# FOREIGN KEY

Note: We will use JOINS and FOREIGN KEY together 

    FOREIGN KEY is used two TABLES, for example transaction_id and customer_id
    FOREIGN KEY IS THE PRIMARY KEY IN ONE TABLE AND FOREIGN KEY ON THE OTHER TABLE
    Connect TABLE 1 with TABLE 2 using FOREIGN KEY
    Rename the FOREIGN KEY during the CONNECTION between two tables
    Delete the FOREIGN KEY

# JOINS

    JOIN is a CLAUSE that is used to combine rows from two or more tables
    We are going to discuss, INNER JOIN, LEFT JOIN, RIGHT JOIN

    Lets see the INNER JOIN
    We select all data between dy tables and connect them by the FOREIGN KEY
    We are telling to the SQL , select all the data between this two tables that have matching customer ids (FOREIGN KEY)

    Lest see the LEFT JOIN
    We will retrieve all data from the LEFT table and all the matching data from the RIGHT table by the FOREIGN KEY

    Lest see the RIGHT JOIN
    We will retrieve all data from the RIGHT table and all the matching data from the LEFT table by the FOREIGN KEY

# FUNCTIONS on MySQL
## Check the documentation for more

    Functions are store programs that allows us to pass params and return data
    We can use ALIAS for our functions
    We can use 'space' during the CONCATENATION

    COUNT function
    MAX function
    MIN function
    AVG function
    SUM function
    CONCAT function, combine two columns

# AND, OR, NOT, BETWEEN, IN

    Logical operators, used to combine more than one condition
    We will write queries to satisfies conditions
    Logical operators usually are used after the WHERE clause
        Now we can use , AND/OR
        with AND, the condition must be true in both statements
        while OR, the condition only one must be true
        NOT, reverse all the conditions 

# Wildcars, $ and _ , used to substitute one or more characters in a string

    To use wildcards, we have to use the LIKE operator, example
    SELECT * FROM employees
        WHERE first_name = LIKE "s%"  (we are looking in a employees table, in the first name, what is starting with the s letter) 
    SELECT * FROM employees
        WHERE first_name = LIKE "%s"  (we are looking in a employees table, in the first name, what is ending with the s letter) 
    SELECT * FROM employees
        WHERE job = LIKE "_ook"  (we are looking in a employees table, in the job for a random character that end with 'ook') 
    SELECT * FROM employees
        WHERE job = LIKE "_ook_"  (we are looking in a employees table, in the job for a random character with 5 letter length and have 'ook') 

    Lets combine these wildcards together
        Lets find a job where the second character is 'a'

    SELECT * FROM employees WHERE job LIKE "_a%" (second is 'a' and after that we have random letters)

# ORBER BY, ASCENDNG, DESCENDING

    We can order by more than two column (ORDER BY amount, customer_id)
    ASCENDNG ordering alphabetically order
    DESCENDING ordering reverse alphabetically order

# LIMIT 

    Limit clause is used to limit the number of records
    Useful if you are working with a lot of data
    Can be used to display a large data on pages (pagination)
    We can use Offset to combine ORDER BY and LIMIT
        LIMIT 1, 1
        LIMIT 2, 1
        LIMIT 3, 1
    Retrieve to much data
            LIMIT 10 - display first 10
            LIMIT 10, 10 - display next  10
            LIMIT 20, 10 - display next 10

# UNION

    UNION WILL NOT DISPLAY DUPLICATES
    Combines the results of two or more SELECT statements
    Join Two tables together

    SELECT * FROM customers
    UNION
    SELECT * FROM employees

    In order to join two tables, tables must have the same number of columns
    but we can specify what to join

    SELECT first_name, last_name FROM customers
    UNION
    SELECT first_name, last_name FROM employees

## UNION ALL

    Will return the duplicate values

# SELF JOINS

    Join another copy of a table to itself
    Used to compare rows of the same table
    Helps to display a hierarchy of data

    Scenario for JOINS:
        We have 4 Employees that they've to report at the Supervisor and the Supervisor has to report to the Boss
        Display only the first_name and last_name and concat the result as 'report to'
        Utilize the SELF JOIN and careful with the Ambiguous

    We have to set a common column, in order to join and compare together.
    The Common Column might be a Name or another ID
    Connect all 4 Employees with the Supervisor using THE COMMON COLUMN, in this case we have supervisor_id
    And the Supervisor connect to the Boss
    Lets utilize SELF JOIN
    
    SELECT everything from our table and ALIAS as 'a'
    INNER join our table and ALIAS as 'b'
    Now connect both using ON using a.supervisor_id with b.employee_id
    Its done
    Now display only the first_name and last_name

    SELECT FIRST_NAME, LAST_NAME from our table and ALIAS from a.first_name, a.last_name
    Concat b.first_name and b.last_name as 'report to'
    INNER join our table and ALIAS as 'b' 
    Now connect both using ON using a.supervisor_id with bemployee_id
    Its done

# VIEWS

    A virtual table based on a result-set of an SQL statement
    The field on VIEWS are real data from our real tables in the database
    They're not real tables, but can be interacted with as if they were
    CREATE VIEW customer AS (the customer table view has been created)

# INDEXES

    Lets understand the BTree Indexes first
    Let's understand what to index and what not to index in SQL

    INDEX (BTree data structure)
    Indexes are used to find values within a specific column more quickly
    MySQL normally searches sequentially through a column
    The longer the column, the more expensive the operation is
    UPDATE takes more time, SELECT takes less time

    SHOW INDEXES FROM customers
    CREATE INDEX index_name ON column(column field)
    SHOW INDEXES FROM customers
    SELECT * FROM customers
    WHERE last_name = "Puff"

    MULTI COLUMN INDEX
    CREATE INDEX index_name
    ON table_name (field1, field2) (careful with the order, how you will search in the future)

# SUBQUERIES
# DISTINCT (REMOVES ALL DUPLICATES)

    A query within another query
    Query(subquery)

    Try to understand the actions
    What are you comparing and how are you displaying these data using subquery
    Try to understand outerquery and how they can be used
    Schema: Main Query -> Outquery/Subquery

# GROUP BY
## WHERE, HAVING
    GROUP BY = aggregate all rows by a specific column often used with aggregate functions:
        example: SUM(), MAX(), MIN(), AVG(), COUNT()
    
    We can use these functions and at the end we will group them for a specific column
    WHERE clause doesnt work with GROUP BY
    We have to use HAVING CLAUSE

# ROLLUP CLAUSE

    ROLLUP , extension for GROUP BY clause
    Produces another row and show the GRAND TOTAL (super-aggregate value)
    WITH ROLLUP

# ON DELETE

    ON DELETE SET NULL = When a FK is deleted, replace FK with NULL
    ON DELETE CASCADE = When a FK is deleted, delete the row

    Syntax:
        SET foreign_key_checks = 0;
        SET foreign_key_checks = 1;
    By default is set to 1, so you cannot delete records that are used as FK in other records.
    Must be added after FOREIGN KEY
        ON DELETE SET NULL
    Now delete that record

    ON DELETE CASCADE, to set the cascade follow the steps as ON DELETE SET NULL

# STORED PROCEDURE

    It's prepared SQL code that you can save, great if there is a query that you write often
    It's like a component, that you can you use it where you want
    Reduces network traffic
    Increases performance
    Secure, admin can grant permission to use
    Increases memory usage of every connection

    Change the delimiter temporary from ';' to '$$' or '//'
    We create that STORED PROCEDURE and CALL it
    
    We can create STORED PROCEDURE and pass a param (single or more params)
    Now CALL it and pass a param

    CALL name_of_procedure
    DROP name_of_procedure

    DELIMITER $$ 
    CREATE PROCEDURE name_of_procedure
    BEGIN
        SELECT * FROM customers;
    END $$
    DELIMITER ;

    CALL name_of_procedure();



    Multiple STORED PROCEDURE

        DELIMITER $$ 
    CREATE PROCEDURE name_of_procedure (param1, param2, param n...,)
    BEGIN
        SELECT * FROM customers
        WHERE colum = param1 AND colum = param2;
    END $$
    DELIMITER ;

        CALL name_of_procedure(param1, param2);

# TRIGGERS

    Trigger, when an event happens, do something
    Example, INSERT, UPDATE, DELETE
    Checks data, handle errors, auditing tables
    COLUMNS ARE UPDATED AUTOMATICALLY AFTER WE DO SOMETHING

    CREATE TRIGGER first
    BEFORE UPDATE/INSERT/DELETE ON
    LOOP THROUGH rows using FOR EACH ROW
    AFTER, SET NEW.something = action goes here (prefix our new things)
    SHOW TRIGGERS

    Note:
    Updating all rows at once
    set hourly_pay = hourly_pay + 1;

# Roadmap for Learning SQL

    https://www.youtube.com/watch?v=yMqldbY2AAg&t=34s

First Part:
    Introduction


Second Part:
    SQL Operations


Third Part:
    SQL Functions



Conclusion




