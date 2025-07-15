# Basic Commands

```mysql
CREATE DATABASE myDB;
USE myDB;
DROP DATABASE myDB;
ALTER DATABASE myDB READ ONLY = 1; # makes database read only. 0 Would make not read/write.
CREATE TABLE employees (
                           employee_id int,
                           first_name VARCHAR(50),
                           last_name VARCHAR(50),
                           hourly_pay decimal(5, 2), # 5 is the max number of digits, including decimal. 2 is percision. 2 is 2 decimal places.
                           hire_date DATE # DATETIME includes date & time. Just date here is needed.
);
SELECT * FROM employees;
RENAME TABLE employees TO workers;
RENAME TABLE workers TO employees;
ALTER TABLE employees ADD phone_number VARCHAR(15); # adds phone number to the table`
ALTER TABLE employees RENAME COLUMN phone_number TO email; # renames phone_number to email
ALTER TABLE employees MODIFY COLUMN email VARCHAR(100); # changes the size to 100 characters
ALTER TABLE employees MODIFY email VARCHAR(100) AFTER last_name;
ALTER TABLE employees DROP COLUMN email; # removes the email column
```

## Inserting Data

Problem is that we have duplicate data in the table after this. We need to remove it & make sure duplicate data can't be created.

```mysql
INSERT INTO employees
VALUES (1, "Eugene", "Krabs", 25.50, "2023-01-02"),
       (2, "Squidward", "Tentacles", 15.00, "2023-01-03"),
       (3, "Sandy", "Cheeks", 20.00, "2023-01-04"),
       (4, "Patrick", "Star", 10.00, "2023-01-05"),
       (5, "SpongeBob", "SquarePants", 12.50, "2023-01-06");
SELECT * FROM employees; # shows the table has one row
```

If you want to add data to a table that ommits some columns, you can specify the columns you want to insert data into:

```mysql
INSERT INTO employees (employee_id, first_name, last_name)
VALUES (6, "Gary", "Snail"),
       (7, "Plankton", "Chum");
SELECT * FROM employees; # shows the table has 3 rows without hourly_pay and hire_date. They are null.
```

## Query Data from a Table

```mysql
SELECT * FROM employees; # selects all columns and all rows from the employees table
```

```mysql
SELECT first_name, last_name FROM employees; # selects only first_name and last_name columns from the employees table
```

or

```mysql
SELECT last_name, first_name FROM employees; # selects last_name and first_name columns from the employees table
```

we can filter as well

```mysql
SELECT first_name, last_name FROM employees WHERE hourly_pay > 15.00; # selects only first_name and last_name columns from the employees table where hourly_pay is greater than 15.00
```


