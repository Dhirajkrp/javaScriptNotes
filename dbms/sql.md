**1. What is SQL, and what does it stand for?**

- SQL stands for Structured Query Language. It is a domain-specific language used for managing and manipulating relational databases. SQL allows users to perform tasks such as querying data, updating records, and defining database structures.

**2. What are the different types of SQL commands, and what do they do (e.g., SELECT, INSERT, UPDATE, DELETE)?**

- SQL commands are broadly categorized into four types:
  - SELECT: Retrieves data from one or more tables.
  - INSERT: Adds new records to a table.
  - UPDATE: Modifies existing records in a table.
  - DELETE: Removes records from a table.

**3. What is a relational database, and how does it differ from other types of databases?**

- A relational database is a type of database that organizes data into structured tables with rows and columns. It uses relationships between tables to establish connections. Unlike other types of databases (e.g., NoSQL), relational databases have a predefined schema, ensuring data integrity and consistency.

**4. Explain the difference between a primary key and a foreign key in a database.**

- A primary key is a column (or combination of columns) in a table that uniquely identifies each row. It enforces data uniqueness and is used to create relationships between tables. A foreign key is a column in a table that refers to the primary key of another table, establishing referential integrity between them.

**5. What is normalization, and why is it important in database design?**

- Normalization is the process of organizing data in a database to eliminate redundancy and reduce data anomalies. It involves breaking down tables into smaller, related tables and defining relationships between them. Normalization helps maintain data consistency and reduces the risk of data anomalies like insertion, update, or deletion anomalies.

**6. What is an SQL JOIN, and what are the different types of JOINs?**

- An SQL JOIN is used to combine rows from two or more tables based on a related column between them. Common types of JOINs include INNER JOIN, LEFT JOIN (or LEFT OUTER JOIN), RIGHT JOIN (or RIGHT OUTER JOIN), and FULL JOIN (or FULL OUTER JOIN).

**7. Explain the differences between INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN.**

- INNER JOIN returns only the rows where there is a match in both tables.
- LEFT JOIN returns all rows from the left table and the matched rows from the right table.
- RIGHT JOIN returns all rows from the right table and the matched rows from the left table.
- FULL JOIN returns all rows when there is a match in either the left or right table.

**8. What is an index in a database, and why is it useful?**

- An index in a database is a data structure that improves the speed of data retrieval operations on a table. It allows the database management system to quickly locate specific rows in a table without scanning the entire table. Indexes are essential for optimizing query performance.

**9. How do you retrieve all records from a table named "Customers" in SQL?**

- You can retrieve all records from the "Customers" table using the SQL SELECT statement as follows:
  ```sql
  SELECT * FROM Customers;
  ```

**10. What is SQL injection, and how can you prevent it in your SQL queries?** - SQL injection is a security vulnerability that occurs when malicious SQL code is inserted into user inputs and executed by the database. To prevent SQL injection, use parameterized queries or prepared statements, validate and sanitize user inputs, and limit database user privileges.

**11. What is the difference between a stored procedure and a function in SQL?** - A stored procedure is a precompiled set of one or more SQL statements that can perform tasks like data manipulation, transaction management, and more. Stored procedures can have input and output parameters but do not return a value directly. A function, on the other hand, is a database object that returns a single value and can be used within SQL queries as part of an expression.

**12. How do you add a new column to an existing table in SQL?** - You can add a new column to an existing table using the ALTER TABLE statement. For example:
`sql
      ALTER TABLE TableName
      ADD NewColumnName DataType;
      `

**13. What is a subquery in SQL, and when would you use it?** - A subquery, also known as a nested query or inner query, is a query nested within another SQL statement (usually within parentheses). Subqueries are used to retrieve data that will be used by the main query for filtering, comparison, or inclusion/exclusion conditions. Subqueries are commonly used in WHERE, FROM, and SELECT clauses.

**14. Explain the concept of ACID properties in database transactions.** - ACID stands for Atomicity, Consistency, Isolation, and Durability, which are essential properties of a database transaction: - Atomicity ensures that a transaction is treated as a single, indivisible unit, either fully completed or fully rolled back in case of failure. - Consistency ensures that a transaction brings the database from one valid state to another, maintaining data integrity. - Isolation ensures that concurrent transactions do not interfere with each other. - Durability ensures that once a transaction is committed, its changes are permanent and will survive system failures.

**15. What is a view in SQL, and how is it different from a table?** - A view in SQL is a virtual table derived from one or more base tables. Views allow users to query and manipulate data as if it were stored in a table, but the data is not physically stored in the database. Views are typically used to simplify complex queries, control access to data, and present a customized view of the data.

**16. How can you group and aggregate data in SQL using GROUP BY and aggregate functions (e.g., SUM, COUNT, AVG)?** - You can group and aggregate data in SQL using the GROUP BY clause to group rows based on one or more columns. Aggregate functions like SUM, COUNT, AVG, MAX, and MIN can then be used to calculate summary statistics for each group.

**17. What is the purpose of the HAVING clause in SQL, and when would you use it?** - The HAVING clause in SQL is used in conjunction with the GROUP BY clause to filter the results of grouped data based on aggregate conditions. It is applied after grouping and aggregation, allowing you to filter groups that meet specific criteria.

**18. Describe the differences between UNION and UNION ALL in SQL.** - UNION combines the result sets of two or more SELECT statements, removing duplicate rows. UNION ALL also combines result sets but retains all rows, including duplicates. UNION ALL is faster than UNION because it does not remove duplicates.

**19. What is the role of the DISTINCT keyword in SQL queries?** - The DISTINCT keyword is used to remove duplicate rows from the result set of a SELECT query. It ensures that only unique values are returned in the query result.

**20. How do you create an SQL query to find the nth highest (or lowest) value in a table?** - To find the nth highest value, you can use a subquery with the LIMIT clause (or equivalent syntax depending on the database system). For example, to find the 3rd highest value:
`sql
      SELECT DISTINCT column_name
      FROM table_name
      ORDER BY column_name DESC
      LIMIT 2, 1; -- Skip the first 2 rows and limit to 1 row
      `

## Questions on mapping:

**1. What is a 1:1 relationship in a relational database, and when would you use it?**

- **Answer:** A 1:1 (one-to-one) relationship is a type of database relationship where one record in one table is related to one record in another table. It is used when two entities have a one-to-one correspondence, and you want to store data for each entity in separate tables to avoid data redundancy.
- **Example:** Consider a database for employees where each employee has one passport. Instead of storing passport details in the employee table, you create a separate passport table with a foreign key referencing the employee.

**2. What is a 1:m relationship in a relational database, and when would you use it?**

- **Answer:** A 1:m (one-to-many) relationship is a type of database relationship where one record in one table is related to multiple records in another table. It is used when one entity can have multiple related entities in another table.
- **Example:** In a library database, each book can have multiple copies. The relationship between books and copies is a 1:m relationship. One book (e.g., "Harry Potter") can have multiple copies available.

**3. What is an m:n relationship in a relational database, and when would you use it?**

- **Answer:** An m:n (many-to-many) relationship is a type of database relationship where multiple records in one table can be related to multiple records in another table. It is used when multiple entities from one table can be associated with multiple entities from another table.
- **Example:** In a university database, students can enroll in multiple courses, and each course can have multiple students. The relationship between students and courses is an m:n relationship.

**4. How do you represent a 1:1 relationship in a database schema?**

- **Answer:** To represent a 1:1 relationship, you can use a foreign key column in one of the related tables. This foreign key column refers to the primary key of the other table.
- **Example:** In a 1:1 relationship between employees and passports, the passport table may have an "employee_id" column as a foreign key referencing the "employee_id" primary key in the employee table.

**5. How do you represent a 1:m relationship in a database schema?**

- **Answer:** To represent a 1:m relationship, you can add a foreign key column in the "many" side (the table with multiple related records) that references the primary key in the "one" side (the table with one record).
- **Example:** In a 1:m relationship between authors and books, the "books" table may have an "author_id" column as a foreign key referencing the "author_id" primary key in the authors table.

**6. How do you represent an m:n relationship in a database schema?**

- **Answer:** To represent an m:n relationship, you typically create a junction table (also known as a bridge or linking table) that contains foreign keys referencing both tables involved in the relationship.
- **Example:** In an m:n relationship between students and courses, you would create a "student_courses" junction table with "student_id" and "course_id" columns, both as foreign keys referencing the respective primary keys.

## Comparision between sql and nosql

**1. What are SQL and NoSQL databases, and how do they differ in terms of data storage and retrieval?**

- **Answer:** SQL databases are relational databases that store structured data in tables with predefined schemas, supporting SQL query language for data retrieval. NoSQL databases, on the other hand, store unstructured or semi-structured data in flexible formats and use various query languages or APIs for data access.

**2. When would you choose a SQL database over a NoSQL database, and vice versa?**

- **Answer:** You might choose a SQL database when your data is structured and requires ACID transactions, complex queries, and joins. NoSQL databases are suitable for unstructured or rapidly changing data, horizontal scalability, and use cases where flexibility and speed are prioritized over strict consistency.

**3. What are the advantages of using a SQL database?**

- **Answer:** Advantages of SQL databases include data consistency, ACID transactions, strong support for complex queries and joins, well-defined schemas, and mature technology.

**4. What are the disadvantages of using a SQL database?**

- **Answer:** Disadvantages of SQL databases include limited scalability (vertically), difficulty handling unstructured data, and potential performance bottlenecks in read-heavy or write-heavy scenarios.

**5. What are the advantages of using a NoSQL database?**

- **Answer:** Advantages of NoSQL databases include horizontal scalability, flexibility to handle unstructured data, high performance in read-heavy or write-heavy scenarios, and support for distributed data storage.

**6. What are the disadvantages of using a NoSQL database?**

- **Answer:** Disadvantages of NoSQL databases include eventual consistency (compared to strong consistency in SQL databases), lack of standardized query language (varies by NoSQL type), and potentially increased complexity in application logic.

**7. Can you provide examples of popular SQL database systems?**

- **Answer:** Examples of popular SQL databases include MySQL, PostgreSQL, Oracle Database, Microsoft SQL Server, and SQLite.

**8. Can you provide examples of popular NoSQL database systems and their use cases?**

- **Answer:** Examples of popular NoSQL databases include MongoDB (document store for JSON-like data), Cassandra (wide-column store for time-series data), Redis (key-value store for caching), and Neo4j (graph database for relationships).

**9. What are the typical use cases for SQL databases?**

- **Answer:** Typical use cases for SQL databases include financial systems, e-commerce platforms, content management systems (CMS), traditional relational data, and applications requiring strict data consistency.

**10. What are the typical use cases for NoSQL databases?** - **Answer:** Typical use cases for NoSQL databases include real-time analytics, social media platforms, IoT data storage, content delivery, and applications where scalability and flexibility are critical.

**11. In which situations might you consider a hybrid approach, using both SQL and NoSQL databases together?** - **Answer:** A hybrid approach can be considered when an application has both structured and unstructured data requirements. For example, using SQL for transactional data and NoSQL for log or user-generated content storage can provide a balanced solution.
