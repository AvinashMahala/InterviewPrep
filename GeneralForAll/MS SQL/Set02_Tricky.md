Sure! Here are some tricky SQL interview questions along with comprehensive answers that you might encounter:

### Tricky SQL Interview Questions & Answers

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

