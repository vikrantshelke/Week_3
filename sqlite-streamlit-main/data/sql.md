# SQL languages

**DDL** is short name of Data Definition Language, which deals with database schemas and descriptions, of how the data should reside in the database.

**DML** is short name of Data Manipulation Language which deals with data manipulation, and includes most common SQL statements such SELECT, INSERT, UPDATE, DELETE etc, and it is used to store, modify, retrieve, delete and update data in database.

**DCL** is short name of Data Control Language which includes commands such as GRANT, and mostly concerned with rights, permissions and other controls of the database system.
# Commands 
Command | Syntax | Description
--- | --- | ---
ALTER table | `ALTER TABLE table_name ADD column_name datatype;` | It is used to add columns to a table in a database
AND | `SELECT column_name(s)FROM table_nameWHERE column_1 = value_1  AND column_2 = value_2;` | It is an operator that is used to combine two conditions
AS | `SELECT column_name AS ‘Alias’FROM table_name;` | It is a keyword in SQL that is used to rename a column or table using an alias name
AVG | `SELECT AVG(column_name)FROM table_name;` | It is used to aggregate a numeric column and return its average
BETWEEN | `SELECT column_name(s)FROM table_nameWHERE column_name BETWEEN value_1 AND value_2;` | It is an operation used to filter the result within a certain range
CASE | `SELECT column_name,CASEWHEN condition THEN ‘Result_1’WHEN condition THEN ‘Result_2’ELSE ‘Result_3’ENDFROM table_name;` | It is a statement used to create different outputs inside a SELECT statement
COUNT | `SELECT COUNT(column_name)FROM table_name;` | It is a function that takes the name of a column as an argument and counts the number of rows when the column is not NULL
Create TABLE | `CREATE TABLE table_name (  column_1 datatype,   column_2 datatype,   column_3 datatype);` | It is used to create a new table in a database and specify the name of the table and columns inside it
DELETE | `DELETE FROM table_nameWHERE some_column = some_value;` | It is used to remove the rows from a table
GROUP BY | `SELECT column_name, COUNT(*)FROM table_nameGROUP BY column_name;` | It is a clause in SQL used for aggregate functions in collaboration with the SELECT statement
HAVING | `SELECT column_name, COUNT(*)FROM table_nameGROUP BY column_nameHAVING COUNT(*) > value;` | It is used in SQL because the WHERE keyword cannot be used in aggregating functions
INNER JOIN | `SELECT column_name(s)FROM table_1JOIN table_2  ON table_1.column_name = table_2.column_name;` | It is used to combine rows from different tables if the Join condition goes TRUE
INSERT | `INSERT INTO table_name (column_1, column_2, column_3) VALUES (value_1, ‘value_2’, value_3);` | It is used to add new rows to a table
IS NULL/ IS NOT NULL | `SELECT column_name(s)FROM table_nameWHERE column_name IS NULL;` | It is an operator used with the WHERE clause to check for the empty values
LIKE | `SELECT column_name(s)FROM table_nameWHERE column_name LIKE pattern;` | It is a special operator used with the WHERE clause to search for a specific pattern in a column
LIMIT | `SELECT column_name(s)FROM table_nameLIMIT number;` | It is a clause to specify the maximum number of rows the result set must |


# Datatypes
### Text types

| Data type        | Description                                                                                                                                                                                                                                                                                      |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CHAR(size)       | Holds a fixed length string (can contain letters, numbers, and special characters). The fixed size is specified in parenthesis. Can store up to 255 characters                                                                                                                                   |
| VARCHAR(size)    | Holds a variable length string (can contain letters, numbers, and special characters). The maximum size is specified in parenthesis. Can store up to 255 characters. Note: If you put a greater value than 255 it will be converted to a TEXT type                                               |
| TINYTEXT         | Holds a string with a maximum length of 255 characters                                                                                                                                                                                                                                           |
| TEXT             | Holds a string with a maximum length of 65,535 characters                                                                                                                                                                                                                                        |
| BLOB             | For BLOBs (Binary Large OBjects). Holds up to 65,535 bytes of data                                                                                                                                                                                                                               |
| MEDIUMTEXT       | Holds a string with a maximum length of 16,777,215 characters                                                                                                                                                                                                                                    |
| MEDIUMBLOB       | For BLOBs (Binary Large OBjects). Holds up to 16,777,215 bytes of data                                                                                                                                                                                                                           |
| LONGTEXT         | Holds a string with a maximum length of 4,294,967,295 characters                                                                                                                                                                                                                                 |
| LONGBLOB         | For BLOBs (Binary Large OBjects). Holds up to 4,294,967,295 bytes of data                                                                                                                                                                                                                        |
| ENUM(x,y,z,etc.) | Let you enter a list of possible values. You can list up to 65535 values in an ENUM list. If a value is inserted that is not in the list, a blank value will be inserted.Note: The values are sorted in the order you enter them.You enter the possible values in this format: ENUM('X','Y','Z') |
| SET              | Similar to ENUM except that SET may contain up to 64 list items and can store more than one choice                                                                                                                                                                                               |

### Number types

| Data type       | Description                                                                                                                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| TINYINT(size)   | -128 to 127 normal. 0 to 255 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                                                                  |
| SMALLINT(size)  | -32768 to 32767 normal. 0 to 65535 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                                                            |
| MEDIUMINT(size) | -8388608 to 8388607 normal. 0 to 16777215 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                                                     |
| INT(size)       | -2147483648 to 2147483647 normal. 0 to 4294967295 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                                             |
| BIGINT(size)    | -9223372036854775808 to 9223372036854775807 normal. 0 to 18446744073709551615 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                 |
| FLOAT(size,d)   | A small number with a floating decimal point. The maximum number of digits may be specified in the size parameter. The maximum number of digits to the right of the decimal point is specified in the d parameter                     |
| DOUBLE(size,d)  | A large number with a floating decimal point. The maximum number of digits may be specified in the size parameter. The maximum number of digits to the right of the decimal point is specified in the d parameter                     |
| DECIMAL(size,d) | A DOUBLE stored as a string , allowing for a fixed decimal point. The maximum number of digits may be specified in the size parameter. The maximum number of digits to the right of the decimal point is specified in the d parameter |

### Date types

| Data type   | Description                                                                                                                                                                                                                              |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DATE()      | A date. Format: YYYY-MM-DDNote: The supported range is from '1000-01-01' to '9999-12-31'                                                                                                                                                 |
| DATETIME()  | *A date and time combination. Format: YYYY-MM-DD HH:MI:SSNote: The supported range is from '1000-01-01 00:00:00' to '9999-12-31 23:59:59'                                                                                                |
| TIMESTAMP() | *A timestamp. TIMESTAMP values are stored as the number of seconds since the Unix epoch ('1970-01-01 00:00:00' UTC). Format: YYYY-MM-DD HH:MI:SSNote: The supported range is from '1970-01-01 00:00:01' UTC to '2038-01-09 03:14:07' UTC |
| TIME()      | A time. Format: HH:MI:SSNote: The supported range is from '-838:59:59' to '838:59:59'                                                                                                                                                    |
| YEAR()      | A year in two-digit or four-digit format.Note: Values allowed in four-digit format: 1901 to 2155. Values allowed in two-digit format: 70 to 69, representing years from 1970 to 2069                                                     |

# Database
Create
```sql
create database dbname;
```
Drop
```sql
drop database dbname;
```

