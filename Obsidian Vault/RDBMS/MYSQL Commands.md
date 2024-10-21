- **Logging In:** You can connect to MySQL using the `mysql -u root -p` command.
- **Basic Commands:** 
    - **Creating a Database:** `CREATE DATABASE database_name`
    - **Using a Database:** `USE database_name` 
    - **Creating a Table:** Use `CREATE TABLE table_name (varname1 type1 property, varname2 type2 property)`
    - **Inserting Data:** Use `INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...` 
    - **Querying Data:** `SELECT * FROM table_name` 
    - **Updating Data:** `UPDATE table_name SET column = value WHERE column2 = value2`
    - **Deleting Data:** `DELETE FROM table_name WHERE column1 = value1` 
    - **Dropping a Table:** `DROP TABLE table_name` 
    - **Dropping a Database:**  `DROP DATABASE db_name`
- **MySQL Tools:** 
    - **MySQL Workbench:** A graphical user interface for designing and managing databases.
    - **phpMyAdmin:** A web-based interface for managing MySQL databases.
    - **Command Line Client:** Allows direct interaction with MySQL using text commands.

### SQL SELECT
- SELECT 
- SELECT DISTINCT

### SQL WHERE
- used to filter records
- return only those who fulfil condition
```SQL
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE _condition_;
```
```
=
>
<
>=
<=
<>
BETWEEN
LIKE
IN
```

### SQL ORDER BY
sort result-set in ascending/descending

``` SQL
SELECT _column1_, _column2, ..._  
FROM _table_name_  
ORDER BY _column1, column2, ..._ ASC|DESC;
```

### SQL AND and OR
filter records based on more than one condition

```SQL
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE _condition1_ AND _condition2_ AND _condition3 ..._;

SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE _condition1_ OR _condition2_ OR _condition3 ..._;
```

### SQL NOT
give opposite result/ negative result

```SQL
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE NOT _condition_;
```

### SQL INSERT INTO
```SQL
INSERT INTO _table_name_ (_column1_, _column2_, _column3_, ...)  
VALUES (_value1_, _value2_, _value3_, ...);

//adding values for all columns of the table
INSERT INTO _table_name_  
VALUES (_value1_, _value2_, _value3_, ...);
```

### SQL Null Values

```SQL
SELECT *
FROM table_name
WHERE column_name IS NULL;
```

### SQL Update
```SQL
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

omitting where clause updates all records in the table
```

### SQL DELETE
delete existing records in the table

```SQL
DELETE FROM _table_name_ WHERE _condition_;

//to delete all records
DELETE FROM table_name;

//to delete table completely, use DROP
DROP TABLE table_name;
```

### SQL SELECT TOP
specify number of records to return

```SQL
SELECT _column_name(s)_  
FROM _table_name  
_WHERE _condition_  
LIMIT _number_;
```
