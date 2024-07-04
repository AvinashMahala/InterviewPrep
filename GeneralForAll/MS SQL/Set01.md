### SQL Interview Questions & Answers

#### Question 1: Explain normalization?
Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves dividing a database into two or more tables and defining relationships between them to ensure that data is stored logically and efficiently. The main goal is to eliminate redundant data and ensure data dependencies make sense to minimize the potential for anomalies during data operations.

#### Question 2: How to implement normalization?
Normalization is implemented through a series of steps known as normal forms (NF). The process involves:
1. **First Normal Form (1NF)**: Ensure that each table column contains atomic (indivisible) values, and each column contains values of a single type.
2. **Second Normal Form (2NF)**: Achieve 1NF, and ensure that all non-key attributes are fully functional dependent on the primary key.
3. **Third Normal Form (3NF)**: Achieve 2NF, and ensure that all attributes are functionally dependent only on the primary key.

#### Question 3: What is denormalization?
Denormalization is the process of combining tables to reduce the number of joins in a query, which can improve read performance. It involves adding redundant data to one or more tables. This is often done in OLAP systems to optimize read-heavy operations at the expense of additional storage and potential data anomalies.

#### Question 4: Explain OLTP vs OLAP?
- **OLTP (Online Transaction Processing)**: 
  - Focuses on managing transactional data.
  - Characterized by a large number of short online transactions.
  - Data is highly normalized.
  - Examples: Banking systems, order entry systems.
- **OLAP (Online Analytical Processing)**: 
  - Focuses on analyzing data.
  - Characterized by a smaller number of complex queries.
  - Data is often denormalized.
  - Examples: Data warehousing, business intelligence applications.

#### Question 5: Explain 1st, 2nd and 3rd Normal form?
- **1st Normal Form (1NF)**: Each column contains atomic values, and each column contains values of a single type. For example, a table of customers should not have multiple phone numbers in one column.
- **2nd Normal Form (2NF)**: Achieve 1NF and ensure that all non-key attributes are fully functionally dependent on the entire primary key. For example, in a table with a composite key, all attributes should depend on both parts of the key.
- **3rd Normal Form (3NF)**: Achieve 2NF and ensure that all attributes are only dependent on the primary key. For example, if a table includes a non-key attribute that depends on another non-key attribute, this dependency should be removed.

#### Question 6: Primary Key vs Unique key?
- **Primary Key**: 
  - Uniquely identifies each record in a table.
  - Cannot contain NULL values.
  - Each table can have only one primary key.
- **Unique Key**: 
  - Ensures all values in a column or a set of columns are unique.
  - Can contain NULL values.
  - Each table can have multiple unique keys.

#### Question 7: Differentiate between Char vs Varchar?
- **Char**:
  - Fixed-length character data type.
  - Faster access since storage size is consistent.
  - Example: `CHAR(10)` always uses 10 bytes of storage.
- **Varchar**:
  - Variable-length character data type.
  - More efficient storage for varying lengths of data.
  - Example: `VARCHAR(10)` uses between 1 to 10 bytes of storage.

#### Question 8: Differentiate between Char vs NChar?
- **Char**: 
  - Fixed-length character data type for non-Unicode characters.
- **NChar**: 
  - Fixed-length character data type for Unicode characters.
  - Uses more storage per character to accommodate multiple languages.

#### Question 9: Whats the size of Char vs NChar?
- **Char(n)**: Uses n bytes of storage.
- **NChar(n)**: Uses 2*n bytes of storage, as each character takes 2 bytes.

#### Question 10: What is the use of Index?
Indexes are used to speed up the retrieval of rows by using pointers. An index can be created on one or more columns of a table to improve the speed of data retrieval. It allows the database to find data without scanning the entire table.

#### Question 11: How does it make search faster?
Indexes make searches faster by creating an internal data structure (like B-trees) that allows the database to quickly locate the data without scanning each row. Instead of looking at each row, the database can use the index to go directly to where the desired data is stored.

#### Question 12: What are the two types of Indexes?
1. **Clustered Index**: 
   - Sorts and stores the data rows of the table or view based on their key values.
   - Only one clustered index per table.
2. **Non-Clustered Index**: 
   - Contains a sorted list of references to the table data.
   - Multiple non-clustered indexes can be created per table.

#### Question 13: Clustered vs Non-Clustered index
- **Clustered Index**: 
  - Alters the way records are stored in a database as it sorts out rows by the column which is set to be a clustered index.
  - Only one clustered index per table.
- **Non-Clustered Index**: 
  - Does not alter the way it is stored but creates a completely separate object within the table which points back to the original table rows after searching.
  - Multiple non-clustered indexes can be created per table.

#### Question 14: Function vs Stored Procedures
- **Function**:
  - Returns a single value or a table.
  - Can be used in SQL statements like SELECT, WHERE, etc.
  - Cannot perform modifications to the database.
- **Stored Procedure**:
  - Can return multiple values and result sets.
  - Used for performing operations and data modifications.
  - Allows for more complex logic and control-of-flow operations.

#### Question 15: What are triggers and why do you need it?
Triggers are special types of stored procedures that automatically execute or fire when certain events occur in a database. They are used to enforce business rules, data integrity, and auditing.

#### Question 16: What are types of triggers?
1. **DML Triggers**: Fire in response to DML events like INSERT, UPDATE, DELETE.
2. **DDL Triggers**: Fire in response to DDL events like CREATE, ALTER, DROP.
3. **Logon Triggers**: Fire in response to LOGON events.

#### Question 17: Differentiate between After trigger vs Instead Of?
- **After Trigger**: Executes after the DML event.
- **Instead Of Trigger**: Executes in place of the DML event, used for complex views.

#### Question 18: What is need of Identity?
An Identity column in SQL Server is used to create an auto-incrementing column that generates unique values automatically. It is often used for primary keys to ensure each row can be uniquely identified.

#### Question 19: Explain transactions and how to implement it?
Transactions are sequences of database operations that are treated as a single unit. A transaction ensures that all operations within it are completed successfully, or none are. This ensures data integrity.
```sql
BEGIN TRANSACTION;
-- SQL Statements
IF @@ERROR != 0
   ROLLBACK TRANSACTION;
ELSE
   COMMIT TRANSACTION;
```

#### Question 20: What are inner joins?
An inner join returns rows when there is a match in both tables being joined. If no match is found, no rows are returned.
```sql
SELECT a.name, b.department_name
FROM employees a
INNER JOIN departments b ON a.department_id = b.department_id;
```

#### Question 21: Explain Left join?
A left join returns all rows from the left table, and the matched rows from the right table. If no match is found, NULLs are returned for columns from the right table.
```sql
SELECT a.name, b.department_name
FROM employees a
LEFT JOIN departments b ON a.department_id = b.department_id;
```

#### Question 22: Explain Right join?
A right join returns all rows from the right table, and the matched rows from the left table. If no match is found, NULLs are returned for columns from the left table.
```sql
SELECT a.name, b.department_name
FROM employees a
RIGHT JOIN departments b ON a.department_id = b.department_id;
```

#### Question 23: Explain Full outer joins?
A full outer join returns all rows when there is a match in one of the tables. If no match is found, NULLs are returned for columns from the table without the match.
```sql
SELECT a.name, b.department_name
FROM employees a
FULL OUTER JOIN departments b ON a.department_id = b.department_id;
```

#### Question 24: Explain Cross joins?
A cross join returns the Cartesian product of the two tables, i.e., it returns all possible combinations of rows from the two tables.
```sql
SELECT a.name, b.department_name
FROM employees a
CROSS JOIN departments b;
```

---

### SQL Interview Questions & Answers - Part 2

#### Question 25: Why do we need UNION?
UNION is used to combine the result sets of two or more SELECT statements. It removes duplicate records between the result sets.

#### Question 26: Differentiate between Union vs Union All?
- **UNION**: Combines result sets and removes duplicates.
- **UNION ALL**: Combines result sets

 but includes duplicates.

#### Question 27: Can we have unequal columns in Union?
No, all SELECT statements within the UNION must have the same number of columns in the result sets with similar data types.

#### Question 28: Can column have different data types in Union?
No, corresponding columns in each SELECT statement within the UNION must have the same data type or be implicitly convertible.

#### Question 29: Which Aggregate function have you used?
Common aggregate functions include SUM, AVG, COUNT, MIN, and MAX.

#### Question 30: When to use Group by?
GROUP BY is used to arrange identical data into groups with the help of aggregate functions. It is used to summarize data.

#### Question 31: Can we select column which is not part of group by?
No, every column in the SELECT list must either be in the GROUP BY clause or be used in an aggregate function.

#### Question 32: What is having clause?
HAVING is used to filter records that work on summarized GROUP BY results. Unlike WHERE, HAVING can filter on aggregate functions.

#### Question 33: Having clause vs Where clause
- **WHERE**: Filters rows before grouping.
- **HAVING**: Filters groups after grouping.

#### Question 34: How can we sort records?
Records can be sorted using the ORDER BY clause.
```sql
SELECT name FROM employees ORDER BY name;
```

#### Question 35: Whats the default sort?
The default sorting order is ascending.

#### Question 36: How can we remove duplicates?
Duplicates can be removed using the DISTINCT keyword.
```sql
SELECT DISTINCT name FROM employees;
```

#### Question 37: Select the first top X records?
Using the TOP clause (in SQL Server) or LIMIT clause (in MySQL).
```sql
SELECT TOP 10 * FROM employees;
```

#### Question 38: How to handle NULLS?
NULLs can be handled using IS NULL, IS NOT NULL, COALESCE, or NULLIF functions.

#### Question 39: What is use of wild cards?
Wildcards are used with the LIKE operator to search for a specified pattern in a column.
- `%` represents zero or more characters.
- `_` represents a single character.
```sql
SELECT name FROM employees WHERE name LIKE 'J%';
```

#### Question 40: What is the use of Alias?
Aliases are used to give a table or a column a temporary name, making the result set easier to read.
```sql
SELECT name AS employee_name FROM employees;
```

#### Question 41: How to write a case statement?
CASE statements allow conditional logic in SQL.
```sql
SELECT name,
       CASE 
         WHEN salary > 50000 THEN 'High' 
         ELSE 'Low' 
       END as salary_range
FROM employees;
```

#### Question 42: What is self reference tables?
Self-referencing tables have a foreign key that references their own primary key. It is used to model hierarchical data.
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    manager_id INT,
    FOREIGN KEY (manager_id) REFERENCES employees(employee_id)
);
```

#### Question 43: What is self join?
A self join is a regular join but the table is joined with itself.
```sql
SELECT e1.name AS employee, e2.name AS manager
FROM employees e1
LEFT JOIN employees e2 ON e1.manager_id = e2.employee_id;
```

#### Question 44: Explain the between clause?
The BETWEEN clause is used to filter the result set within a certain range. It is inclusive.
```sql
SELECT name FROM employees WHERE salary BETWEEN 40000 AND 60000;
```

---

### SQL Interview Questions & Answers - Part 3

#### Question 45: Explain SubQuery?
A subquery is a query within another query. The result of the subquery is used by the outer query.

#### Question 46: Can inner Subquery return multiple results?
Yes, an inner subquery can return multiple results if used with operators like IN, EXISTS, or ANY.

#### Question 47: What is Co-related Query?
A correlated query is a subquery that uses values from the outer query. The subquery is executed once for each row processed by the outer query.

#### Question 48: Differentiate between Joins and SubQuery?
- **Joins**: Combine data from multiple tables into a single result set.
- **Subqueries**: Used to return data that will be used by the main query. Can be nested.

#### Question 49: Performance Joins vs SubQuery?
Joins are generally more efficient than subqueries because they can leverage indexes and optimize the execution plan better. However, subqueries can sometimes be more readable and maintainable.

---

### SQL Server Interview Questions & Answers - Part 4

#### Question 50: Find NTH Highest Salary in SQL.
```sql
SELECT salary
FROM (SELECT salary, 
             ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num
      FROM employees) AS temp
WHERE row_num = N;
```

---

### SQL Server Interview Questions & Answers - Part 5

#### Question 51: Select the top nth highest salary using correlated Queries?
```sql
SELECT salary 
FROM employees e1 
WHERE N-1 = (SELECT COUNT(DISTINCT salary) 
             FROM employees e2 
             WHERE e2.salary > e1.salary);
```

#### Question 52: Select top nth using T-SQL
```sql
SELECT salary 
FROM (SELECT salary, 
             ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num 
      FROM employees) AS temp 
WHERE row_num = N;
```

#### Question 53: Performance comparison of all the methods.
Comparing performance depends on the specific use case and database schema. Generally:
- **Using ROW_NUMBER()**: Efficient for large datasets.
- **Using correlated subqueries**: Less efficient for large datasets due to multiple evaluations.
- **Using LIMIT/OFFSET**: Common in MySQL but may not be the most efficient for very large tables.

---

