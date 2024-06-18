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

# Select

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





