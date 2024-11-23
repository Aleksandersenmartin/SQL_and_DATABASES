## CREATE TABLE

Used to create a new table in the database.

## Basic Syntax
```sql
CREATE TABLE table_name (
  column1 datatype constraints,
  column2 datatype constraints,
  ...
);
```

#### Example:
```sql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  age INT,
  department VARCHAR(50),
  date_joined DATE
);
```
##### Variations:

With Default Values:
```sql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  age INT DEFAULT 30
);
```
#### Temporary Table:
```sql
CREATE TEMPORARY TABLE temp_employees (
  id INT,
  name VARCHAR(100)
);

```

##### As Select Statement (creates a table with data from another table):
```sql
CREATE TABLE new_table AS
SELECT * FROM old_table;
```

## CREATE DATABASE

Used to create a new database.

### Syntax:
```sql
CREATE DATABASE database_name;
```

#### Example:
```sql
CREATE DATABASE company_data;
```
##### Variations:

With Character Set and Collation:
```sql
CREATE DATABASE company_data
CHARACTER SET utf8mb4
COLLATE utf8mb4_general_ci;
```

## CREATE VIEW

Used to create a virtual table based on the result of a query.

### Syntax:
```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
#### Example:
```sql
CREATE VIEW employee_view AS
SELECT id, name, department
FROM employees
WHERE age > 30;
```

## CREATE INDEX

Used to create an index on one or more columns of a table to improve query performance.

### Syntax:
```sql
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```
#### Example:
```sql
CREATE INDEX idx_name
ON employees (name);
```
##### Variations:

##### Unique Index:
```sql
CREATE UNIQUE INDEX idx_unique_name
ON employees (name);
```
##### Composite Index:
```sql
CREATE INDEX idx_composite
ON employees (department, age);
```

##### Full-Text Index (MySQL):
```sql
CREATE FULLTEXT INDEX idx_fulltext_name
ON employees (name);
```

## CREATE SCHEMA

Used to create a schema, which is a logical container for database objects.

### Syntax:
```sql
CREATE SCHEMA schema_name;
```
#### Example:
```sql
CREATE SCHEMA hr;
```
##### Variations:

##### With Authorization (PostgreSQL):
```sql
CREATE SCHEMA hr AUTHORIZATION user_name;
```

## CREATE FUNCTION

Used to create a user-defined function in the database.

### Syntax:
```sql
CREATE FUNCTION function_name(parameters)
RETURNS return_type
AS
BEGIN
  -- Function logic
END;
```
#### Example:
```sql
CREATE FUNCTION calculate_bonus(salary INT)
RETURNS INT
AS
BEGIN
  RETURN salary * 0.1;
END;
```

## CREATE PROCEDURE

Used to create a stored procedure, which is a precompiled set of SQL statements.

## Syntax:
```sql
CREATE PROCEDURE procedure_name(parameters)
AS
BEGIN
  -- Procedure logic
END;
```
#### Example:
```sql
CREATE PROCEDURE add_employee (
  IN emp_name VARCHAR(100), 
  IN emp_age INT
)
AS
BEGIN
  INSERT INTO employees (name, age)
  VALUES (emp_name, emp_age);
END;
```

## CREATE TRIGGER

Used to create a trigger that automatically executes in response to specific events on a table.

### Syntax:
```sql
CREATE TRIGGER trigger_name
AFTER|BEFORE INSERT|UPDATE|DELETE
ON table_name
FOR EACH ROW
BEGIN
  -- Trigger logic
END;
```

#### Example:
```sql
CREATE TRIGGER after_insert_employee
AFTER INSERT ON employees
FOR EACH ROW
BEGIN
  INSERT INTO log_table (action, timestamp)
  VALUES ('Insert', NOW());
END;
```

## CREATE SEQUENCE

Used to create a sequence, which generates unique numbers (often used for auto-incrementing primary keys).

### Syntax:
```sql
CREATE SEQUENCE sequence_name
START WITH start_value
INCREMENT BY increment_value;
```
#### Example:
```sql 
CREATE SEQUENCE employee_id_seq
START WITH 1
INCREMENT BY 1;
```

## CREATE ROLE

Used to create a role for database security and permissions.

### Syntax:
```sql
CREATE ROLE role_name;
```
#### Example:
```sql
CREATE ROLE manager_role;
```
##### Variations:
##### With Permissions:
```sql
CREATE ROLE manager_role WITH LOGIN PASSWORD 'secure_pass';
```

## CREATE USER

Used to create a new database user.

### Syntax:
```sql
CREATE USER user_name IDENTIFIED BY password;
```

#### Example:
```sql
CREATE USER john IDENTIFIED BY 'secure_password';
```
#### Variations:
#### With Host Restrictions (MySQL):
```sql
CREATE USER 'john'@'localhost' IDENTIFIED BY 'secure_password';
```

## CREATE TABLESPACE

Used to create a tablespace for organizing and managing storage.

### Syntax:
```sql
CREATE TABLESPACE tablespace_name
DATAFILE 'file_path' SIZE size;
```
#### Example:
```sql
CREATE TABLESPACE employee_data
DATAFILE '/data/employee_data.dbf' SIZE 50M;
```

##CREATE EVENT (MySQL)

Used to create a scheduled task in MySQL.

### Syntax:
```sql
CREATE EVENT event_name
ON SCHEDULE schedule
DO
event_body;
```
#### Example:
```sql 
CREATE EVENT daily_cleanup
ON SCHEDULE EVERY 1 DAY
DO
DELETE FROM log_table WHERE timestamp < NOW() - INTERVAL 30 DAY;
```

## CREATE AGGREGATE FUNCTION (PostgreSQL)

Used to create a custom aggregate function.

### Syntax:
```sql
CREATE AGGREGATE aggregate_name (
  SFUNC = state_function,
  STYPE = state_data_type,
  FINALFUNC = final_function
);
```
#### Example:
```sql
CREATE AGGREGATE array_concat_agg (
  SFUNC = array_append,
  STYPE = anyarray
);
```
