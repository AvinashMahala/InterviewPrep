### Additional SQL Interview Questions & Answers

#### Question 1: How can you select unique records from a table without using the DISTINCT keyword?
You can use the `GROUP BY` clause to select unique records:
```sql
SELECT column1, column2, ...
FROM table_name
GROUP BY column1, column2, ...;
```

#### Question 2: How can you find the second highest salary in a table?
You can use the `DISTINCT` keyword along with the `ORDER BY` and `OFFSET` clauses:
```sql
SELECT DISTINCT salary 
FROM employees 
ORDER BY salary DESC 
OFFSET 1 ROW 
FETCH NEXT 1 ROW ONLY;
```

#### Question 3: How can you find the nth highest salary in a table?
You can use the `DENSE_RANK()` window function:
```sql
SELECT salary 
FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk 
    FROM employees
) AS ranked_salaries 
WHERE rnk = N;
```

#### Question 4: How can you delete duplicate rows in a table while keeping one instance of each duplicate?
You can use a CTE with `ROW_NUMBER()` to identify and delete duplicates:
```sql
WITH CTE AS (
    SELECT *, ROW_NUMBER() OVER (PARTITION BY column1, column2 ORDER BY (SELECT NULL)) AS rn
    FROM table_name
)
DELETE FROM CTE WHERE rn > 1;
```

#### Question 5: How can you update one table based on another table?
You can use the `UPDATE` statement with a `JOIN`:
```sql
UPDATE t1
SET t1.column1 = t2.column2
FROM table1 t1
JOIN table2 t2 ON t1.common_column = t2.common_column;
```

#### Question 6: How can you swap values of two columns in a single UPDATE statement?
You can use a single `UPDATE` statement with a `CASE` expression:
```sql
UPDATE table_name
SET column1 = column2, column2 = column1;
```

#### Question 7: How can you find all employees who have managers?
You can use a `SELF JOIN`:
```sql
SELECT e1.employee_id, e1.name, e2.name AS manager_name
FROM employees e1
JOIN employees e2 ON e1.manager_id = e2.employee_id;
```

#### Question 8: How can you get the cumulative sum of a column in a table?
You can use the `SUM()` window function:
```sql
SELECT column1, 
       column2, 
       SUM(column2) OVER (ORDER BY column1) AS cumulative_sum
FROM table_name;
```

#### Question 9: How can you find the top three highest salaries in each department?
You can use the `DENSE_RANK()` window function with a `PARTITION BY` clause:
```sql
SELECT department_id, employee_id, salary
FROM (
    SELECT department_id, employee_id, salary,
           DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rnk
    FROM employees
) AS ranked_salaries
WHERE rnk <= 3;
```

#### Question 10: How can you retrieve rows where a column's value is null?
You can use the `IS NULL` clause:
```sql
SELECT * FROM table_name WHERE column_name IS NULL;
```

#### Question 11: How can you pivot data from rows to columns?
You can use the `PIVOT` operator in SQL Server:
```sql
SELECT * 
FROM (
    SELECT column1, column2, value
    FROM table_name
) AS SourceTable
PIVOT (
    MAX(value)
    FOR column2 IN ([Value1], [Value2], [Value3])
) AS PivotTable;
```

#### Question 12: How can you unpivot data from columns to rows?
You can use the `UNPIVOT` operator in SQL Server:
```sql
SELECT column1, column2, value
FROM table_name
UNPIVOT (
    value FOR column2 IN (column3, column4, column5)
) AS UnpivotTable;
```

#### Question 13: How can you select the last record from a table?
You can use the `ORDER BY` clause in descending order along with `TOP` or `LIMIT`:
```sql
SELECT TOP 1 * 
FROM table_name 
ORDER BY column_name DESC;
```

#### Question 14: How can you concatenate rows into a single string?
You can use the `STRING_AGG()` function in SQL Server or `GROUP_CONCAT()` in MySQL:
```sql
SELECT STRING_AGG(column_name, ', ') AS concatenated_string
FROM table_name
GROUP BY another_column;
```
For MySQL:
```sql
SELECT GROUP_CONCAT(column_name SEPARATOR ', ') AS concatenated_string
FROM table_name
GROUP BY another_column;
```

#### Question 15: How can you handle NULL values in aggregate functions?
You can use the `COALESCE()` function to replace `NULL` with a default value:
```sql
SELECT SUM(COALESCE(column_name, 0)) AS sum_value
FROM table_name;
```

#### Question 16: How can you find duplicate rows in a table?
```sql
SELECT column1, column2, COUNT(*)
FROM table_name
GROUP BY column1, column2
HAVING COUNT(*) > 1;
```

#### Question 17: How can you delete duplicate rows in a table while keeping the one with the lowest ID?
```sql
WITH CTE AS (
    SELECT *, ROW_NUMBER() OVER (PARTITION BY column1, column2 ORDER BY id) AS rn
    FROM table_name
)
DELETE FROM CTE WHERE rn > 1;
```

#### Question 18: How can you find the number of employees in each department?
```sql
SELECT department_id, COUNT(*) AS num_employees
FROM employees
GROUP BY department_id;
```

#### Question 19: How can you find all employees who have the same job title?
```sql
SELECT job_title, COUNT(*)
FROM employees
GROUP BY job_title
HAVING COUNT(*) > 1;
```

#### Question 20: How can you find the first non-null value in a column?
```sql
SELECT COALESCE(column1, column2, column3) AS first_non_null_value
FROM table_name;
```

#### Question 21: How can you select all employees who were hired in the last 30 days?
```sql
SELECT *
FROM employees
WHERE hire_date >= DATEADD(day, -30, GETDATE());
```

#### Question 22: How can you get the current date and time in SQL Server?
```sql
SELECT GETDATE() AS current_datetime;
```

#### Question 23: How can you get the current date and time in MySQL?
```sql
SELECT NOW() AS current_datetime;
```

#### Question 24: How can you extract the year from a date in SQL Server?
```sql
SELECT YEAR(date_column) AS year
FROM table_name;
```

#### Question 25: How can you extract the month from a date in MySQL?
```sql
SELECT MONTH(date_column) AS month
FROM table_name;
```

#### Question 26: How can you add a new column to an existing table?
```sql
ALTER TABLE table_name
ADD new_column_name datatype;
```

#### Question 27: How can you change the datatype of an existing column?
```sql
ALTER TABLE table_name
ALTER COLUMN column_name new_datatype;
```

#### Question 28: How can you rename a column in SQL Server?
```sql
EXEC sp_rename 'table_name.old_column_name', 'new_column_name', 'COLUMN';
```

#### Question 29: How can you rename a table in MySQL?
```sql
RENAME TABLE old_table_name TO new_table_name;
```

#### Question 30: How can you drop a column from a table?
```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

#### Question 31: How can you add a primary key to an existing table?
```sql
ALTER TABLE table_name
ADD CONSTRAINT pk_name PRIMARY KEY (column_name);
```

#### Question 32: How can you drop a primary key from an existing table?
```sql
ALTER TABLE table_name
DROP CONSTRAINT pk_name;
```

#### Question 33: How can you add a foreign key to an existing table?
```sql
ALTER TABLE table_name
ADD CONSTRAINT fk_name FOREIGN KEY (column_name) REFERENCES other_table(column_name);
```

#### Question 34: How can you drop a foreign key from an existing table?
```sql
ALTER TABLE table_name
DROP CONSTRAINT fk_name;
```

#### Question 35: How can you check the existence of a table?
```sql
IF OBJECT_ID('table_name', 'U') IS NOT NULL
    PRINT 'Table exists';
ELSE
    PRINT 'Table does not exist';
```

#### Question 36: How can you check the existence of a column in a table?
```sql
IF EXISTS (SELECT * FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = 'table_name' AND COLUMN_NAME = 'column_name')
    PRINT 'Column exists';
ELSE
    PRINT 'Column does not exist';
```

#### Question 37: How can you list all tables in a database?
```sql
SELECT table_name
FROM information_schema.tables
WHERE table_schema = 'database_name';
```

#### Question 38: How can you list all columns in a table?
```sql
SELECT column_name
FROM information_schema.columns
WHERE table_name = 'table_name';
```

#### Question 39: How can you list all indexes on a table?
```sql
SELECT * 
FROM sys.indexes 
WHERE object_id = OBJECT_ID('table_name');
```

#### Question 40: How can you calculate the total number of rows in a table?
```sql
SELECT COUNT(*) AS total_rows
FROM table_name;
```

#### Question 41: How can you select rows with even IDs?
```sql
SELECT * 
FROM table_name
WHERE id % 2 = 0;
```

#### Question 42: How can you select rows with odd IDs?
```sql
SELECT * 
FROM table_name
WHERE id % 2 <> 0;
```

#### Question 43: How can you select the nth row in a table?
```sql
SELECT * 
FROM (
    SELECT *, ROW_NUMBER() OVER (ORDER BY column_name) AS rn
    FROM table_name
) AS temp_table
WHERE rn = n;
```

#### Question 44: How can you calculate the difference between two dates?
```sql
SELECT DATEDIFF(day, date1, date2) AS date_difference
FROM table_name;
```

#### Question 45: How can you add a specific number of days to a date?
```sql
SELECT DATEADD(day, number_of_days, date_column) AS new_date
FROM table_name;
```

#### Question 46: How can you subtract a specific number of days from a date?
```sql
SELECT DATEADD(day, -number_of_days, date_column) AS new_date
FROM table_name;
```

#### Question 47: How can you find rows with NULL values in a column?
```sql
SELECT * 
FROM table_name
WHERE column_name IS NULL;
```

#### Question 48: How can you replace NULL values with a default value?
```sql
SELECT ISNULL(column_name, default_value) AS column_name
FROM table_name;
```

#### Question 49: How can you find rows without NULL values in a column?
```sql
SELECT * 
FROM table_name
WHERE column_name IS NOT NULL;
```

#### Question 50: How can you find rows where a column has a specific substring?
```sql
SELECT * 
FROM table_name
WHERE column_name LIKE '%substring%';
```

#### Question 51: How can you count the number of rows that match a specific condition?
```sql
SELECT COUNT(*) AS count
FROM table_name
WHERE condition;
```

#### Question 52: How can you get the average value of a column?
```sql
SELECT AVG(column_name) AS average_value
FROM table_name;
```

#### Question 53: How can you get the minimum value of a column?
```sql
SELECT MIN(column_name) AS minimum_value
FROM table_name;
```

#### Question 54: How can you get the maximum value of a column?
```sql
SELECT MAX(column_name) AS maximum_value
FROM table_name;
```

#### Question 55: How can you calculate the sum of a column?
```sql
SELECT SUM(column_name) AS total_sum
FROM table_name;
```

#### Question 56: How can you join two tables and select all columns from both?
```sql
SELECT *
FROM table1
JOIN table2 ON table1.common_column = table2.common_column;
```

#### Question 57: How can you find the common rows from two tables?
```sql
SELECT *
FROM table1
INTERSECT
SELECT *
FROM table2;
```

#### Question 58: How can you find the different rows between two tables?
```sql
SELECT *
FROM table1
EXCEPT
SELECT *
FROM table2;
```

#### Question 59: How can you find the total number of rows from two tables combined?
```sql
SELECT COUNT(*) AS total_count
FROM (
    SELECT * FROM table1
    UNION
    SELECT * FROM table2
) AS combined_table;
```

#### Question 60: How can you get the rank of rows based on a specific column?
```sql
SELECT column_name, 
       RANK() OVER (ORDER BY column_name) AS rank
FROM table_name;
```

#### Question 61: How can you calculate the running total of a column?
```sql
SELECT column_name,
       SUM(column_name) OVER (ORDER BY column_name) AS running_total
FROM table_name;
```

#### Question 62: How can you calculate the difference between current and previous row's value?
```sql
SELECT column_name,
       column_name - LAG(column_name) OVER (ORDER BY column_name) AS difference
FROM table_name;
```

#### Question 63: How can you calculate the percentage of a column over the total?
```sql
SELECT column_name,
       column_name * 100.0 / SUM(column_name) OVER () AS percentage
FROM table_name;
```

#### Question 64: How can you identify gaps in a sequence?
```sql
SELECT (current_column + 1) AS start_of_gap, 
       (next_column - 1) AS end_of_gap
FROM (
    SELECT column_name AS current_column, 
           LEAD(column_name) OVER (ORDER BY column_name) AS next_column


    FROM table_name
) AS gaps
WHERE next_column - current_column > 1;
```

#### Question 65: How can you generate a series of dates?
```sql
WITH date_series AS (
    SELECT CAST('2023-01-01' AS DATE) AS date
    UNION ALL
    SELECT DATEADD(day, 1, date)
    FROM date_series
    WHERE date < '2023-12-31'
)
SELECT *
FROM date_series;
```

#### Question 66: How can you perform a full outer join?
```sql
SELECT * 
FROM table1
FULL OUTER JOIN table2 ON table1.common_column = table2.common_column;
```

#### Question 67: How can you remove a table?
```sql
DROP TABLE table_name;
```

#### Question 68: How can you truncate a table?
```sql
TRUNCATE TABLE table_name;
```

#### Question 69: How can you back up a database?
```sql
BACKUP DATABASE database_name TO DISK = 'file_path';
```

#### Question 70: How can you restore a database?
```sql
RESTORE DATABASE database_name FROM DISK = 'file_path';
```

#### Question 71: How can you check database size?
```sql
SELECT 
    database_name, 
    SUM(size * 8 / 1024) AS size_in_MB
FROM sys.master_files
GROUP BY database_name;
```

#### Question 72: How can you detect slow running queries?
```sql
SELECT TOP 10 *
FROM sys.dm_exec_query_stats
ORDER BY total_elapsed_time DESC;
```

#### Question 73: How can you optimize a query?
You can optimize a query by:
- Adding indexes
- Writing efficient joins
- Avoiding subqueries in SELECT statements
- Using EXISTS instead of IN
- Avoiding SELECT *

#### Question 74: How can you find the most expensive queries in terms of CPU usage?
```sql
SELECT TOP 10
    query_stats.query_hash AS "Query Hash", 
    SUM(query_stats.total_worker_time) / SUM(query_stats.execution_count) AS "Avg CPU Time", 
    MIN(query_stats.statement_text) AS "Query Text"
FROM (
    SELECT 
        qs.*, 
        SUBSTRING(
            qt.text, 
            (qs.statement_start_offset / 2) + 1, 
            ((CASE qs.statement_end_offset
                WHEN -1 THEN DATALENGTH(qt.text)
                ELSE qs.statement_end_offset
              END - qs.statement_start_offset) / 2) + 1
        ) AS statement_text
    FROM sys.dm_exec_query_stats qs
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) qt
) AS query_stats
GROUP BY query_stats.query_hash
ORDER BY "Avg CPU Time" DESC;
```

#### Question 75: How can you handle a large number of data rows for better performance?
- Use indexing appropriately.
- Consider partitioning large tables.
- Optimize queries and subqueries.
- Use summary tables for complex aggregations.
- Implement caching strategies.

#### Question 76: How can you detect deadlocks?
You can use SQL Server Profiler or Extended Events to detect deadlocks.

#### Question 77: How can you avoid deadlocks?
- Keep transactions short and in one batch.
- Access objects in a consistent order.
- Avoid user interaction during transactions.
- Use the lowest possible isolation level.

#### Question 78: How can you find the number of open transactions?
```sql
DBCC OPENTRAN();
```

#### Question 79: How can you convert data from one type to another?
```sql
SELECT CONVERT(datatype, column_name) AS new_column_name
FROM table_name;
```

#### Question 80: How can you handle case-sensitive searches?
```sql
SELECT * 
FROM table_name
WHERE column_name COLLATE Latin1_General_CS_AS = 'value';
```

#### Question 81: How can you find the length of a string?
```sql
SELECT LEN(column_name) AS string_length
FROM table_name;
```

#### Question 82: How can you convert all characters in a string to uppercase?
```sql
SELECT UPPER(column_name) AS uppercase_string
FROM table_name;
```

#### Question 83: How can you convert all characters in a string to lowercase?
```sql
SELECT LOWER(column_name) AS lowercase_string
FROM table_name;
```

#### Question 84: How can you find the position of a substring within a string?
```sql
SELECT CHARINDEX('substring', column_name) AS position
FROM table_name;
```

#### Question 85: How can you concatenate two strings?
```sql
SELECT CONCAT(string1, string2) AS concatenated_string
FROM table_name;
```

#### Question 86: How can you remove leading and trailing spaces from a string?
```sql
SELECT LTRIM(RTRIM(column_name)) AS trimmed_string
FROM table_name;
```

#### Question 87: How can you replace a substring within a string?
```sql
SELECT REPLACE(column_name, 'old_substring', 'new_substring') AS new_string
FROM table_name;
```

#### Question 88: How can you get the current user's login name?
```sql
SELECT SYSTEM_USER AS current_user;
```

#### Question 89: How can you get the name of the current database?
```sql
SELECT DB_NAME() AS current_database;
```

#### Question 90: How can you count the number of unique values in a column?
```sql
SELECT COUNT(DISTINCT column_name) AS unique_count
FROM table_name;
```

#### Question 91: How can you drop a stored procedure?
```sql
DROP PROCEDURE procedure_name;
```

#### Question 92: How can you create a new schema in a database?
```sql
CREATE SCHEMA schema_name;
```

#### Question 93: How can you change the schema of a table?
```sql
ALTER SCHEMA new_schema_name TRANSFER old_schema_name.table_name;
```

#### Question 94: How can you find the default value of a column?
```sql
SELECT column_default 
FROM information_schema.columns
WHERE table_name = 'table_name' 
AND column_name = 'column_name';
```

#### Question 95: How can you detect memory usage by SQL Server?
```sql
SELECT 
    total_physical_memory_kb, 
    available_physical_memory_kb, 
    total_page_file_kb, 
    available_page_file_kb, 
    system_memory_state_desc 
FROM sys.dm_os_sys_memory;
```

#### Question 96: How can you get the last identity value inserted?
```sql
SELECT SCOPE_IDENTITY() AS last_identity_value;
```

#### Question 97: How can you find the last modified date of a table?
```sql
SELECT 
    name, 
    modify_date 
FROM sys.tables
WHERE name = 'table_name';
```

#### Question 98: How can you list all databases on a SQL Server instance?
```sql
SELECT name 
FROM sys.databases;
```

#### Question 99: How can you disable a trigger?
```sql
DISABLE TRIGGER trigger_name ON table_name;
```

#### Question 100: How can you enable a trigger?
```sql
ENABLE TRIGGER trigger_name ON table_name;
```

These questions and answers cover a wide range of SQL concepts, including query optimization, data manipulation, indexing, stored procedures, and more. Make sure to practice writing and executing these queries to deepen your understanding and prepare thoroughly for your interviews.