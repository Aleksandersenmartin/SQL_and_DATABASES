
## Alter Table: 

Used to modify the structure of a table, such as adding, dropping, or modifying columns, and adding constraints. 

### Add, Drop, Modify Columns: 


#### Add a column
```sql 
ALTER TABLE table_name ADD column_name data_type; 
```
#### Drop a column
```sql
ALTER TBALE table_name DROP COLUMN column_name; 
```

#### Modify a column's data type 
```sql
ALTER TABLE table_name ALTER COLUMN column_name data type; 
```

### Rename columns or tables

#### Rename a qolumn (PostgreSQL, MySQL)
```sql
ALTER TABLE table_name RENAME COLUMN old_name TO new_name
```

#### Rename a table: 
```sql
ALTER TABLE old_table_name RENAME to new_table_name;
```

### Add or Drop Constraints 

#### Add a primary key: 
```sql
ALTER TABLE table_name ADD CONSTRAINT pk_name PRIMARY KEY (column_name); 
```

#### Drop a primary key 
```sql
ALTER TABLE table_name DROP CONSTRAINT pk_name; 
```

#### Add a foreign key
```sql
ALTER TABLE table_name DROP CONSTRAINT fk_name; 
```

### Add or Dropp indexes 

#### Add an index
```sql
CREATE INDEX index_name ON table_name(column_name);
```

#### Drop an index 
```sql
DROP INDEX index_name;
```

### Alter Database 
used to modify properties of a database, such as its name or settings 

#### Rename a database (PostgreSQL, MySQL)
```sql
ALTER DATABASE old_name RENAME to new_name; 
```

#### Change Database Settings: 
#### Set default character set:
```sql
ALTER  DATABASE database_name CHARACTER SET utf8mb4; 
```

#### SET default collation
```sql
ALTER DATABASE database_name COLLATE utf8md4_general_ci;
```

### Alter view 
used to modify an existing view 

#### Change the SELECT statement
```sql
CREATE or REPLACE VIEW view_name as SELECT column1, column2 FROM table_name; 
```

#### Add a WITH CHECK OPTION
```sql
ALTER VIEW view_name WITH CHECK OPTION; 
```

### Alter Index 

#### Rename an index
```sql
ALTER INDEX old_index_name RENAME to new_index_name; 
```

Rebuild or reorganize and index (SQL SERVER)

#### Rebuild an index 
```sql
ALTER INDEX index_name ON table_name REBUILD; 
```

#### Reorganize and index 
```sql
ALTER INDEX index_name ON table_name REORGNAIZE; 
```

### ALTER SCHEMA 
Used to modify a schema's properties 


#### Rename Schema (PostgreSQL)
```sql
ALTER SCHEMA oled_schema_name RENAME to new_schema_name; 
```

#### Change owner 
```sql
ALTER SCHEMA schema_name OWNER TO new_owner; 
```

### ALTER SEQUENCE 
Used to modify the properties of a sequence (used for auto-increment)

#### Change Start Value
```sql
ALTER SEQUENCE sequence_name RESTART WITH start_value; 
```

#### Change increment value
```sql
ALTER SEQUENCE sequence_name INCREMENT BY value;
```

### ALTER USER / ROLE 
Used to modify user or role properties 

#### Change a user's password 
```sql
ALTER USER username IDENTIFIED BY new_password;
```
Change User Privelieges 
#### Grant a role 
```sql
ALTER USER username GRANT role_name;
```

#### Revoke a role: 
```sql
ALTER USER username REVOKE role_name; 
```

### ALTER TRIGGER 
Used to modify triggers 

#### Rename a trigger
```sql
ALTER TRIGGER ole_trigger_name RENAME to new_trigger_name;
```

#### Disable a trigger 
```sql
ALTER TABLE table_name DISABLE TRIGGER trigger_name; 
```
