
---

### 🔷 DBMS

| Q# | Question                                                                                                                                  | Answer                                                                                                                                                  | Concept(s) Tested                  | Difficulty |
| -- | ----------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- | ---------- |
| 1  | You’re designing a system where users can add products to a wishlist. How would you organize your tables to avoid duplicate product info? | Use normalization, separate product info into a `Product` table, and reference it in a `Wishlist` table with user-product mapping to avoid duplication. | Normalization, Schema Design       | Medium     |
| 2  | Imagine your app’s queries are slow because it scans the entire table every time. What could you add to improve performance?              | Add indexes on columns frequently used in WHERE, JOIN, or ORDER BY clauses to speed up lookups.                                                         | Indexing                           | Medium     |
| 3  | You notice your database has redundant data causing inconsistency. How would you approach fixing this?                                    | Apply normalization rules (1NF, 2NF, 3NF) to eliminate redundancy and maintain data integrity.                                                          | Normalization, Data Integrity      | Medium     |
| 4  | How would you handle a scenario where a student can enroll in many courses and a course has many students?                                | Use a many-to-many relationship implemented via a join table, e.g., `StudentCourse(student_id, course_id)`.                                             | Many-to-many relationships         | Medium     |
| 5  | You want to ensure that no two users have the same email but still allow some fields to be optional. How would you design constraints?    | Use a UNIQUE constraint on the `email` column while allowing NULLs for optional fields.                                                                 | Keys, Constraints                  | Medium     |
| 6  | While inserting data, you get an error related to a foreign key. What might be causing this?                                              | The foreign key value doesn't exist in the referenced table, violating referential integrity constraints.                                               | Referential Integrity, Constraints | Easy       |
| 7  | You have a report that aggregates sales data but it runs very slowly on large data. What trade-offs could you consider to speed it up?    | Use denormalization to reduce JOINs, or create summary tables/materialized views for faster aggregation at the cost of data redundancy.                 | Denormalization, Performance       | Medium     |
| 8  | Your app crashes when two users try to update the same record at once. How do transactions help here?                                     | Transactions ensure atomicity and isolation (ACID), so concurrent updates do not cause inconsistent states via locks or rollbacks.                      | ACID properties, Transactions      | Medium     |
| 9  | When should you use a view instead of querying the base tables directly?                                                                  | Use views to simplify complex queries, provide abstraction, or restrict access to sensitive data by exposing limited columns.                           | Views, Query abstraction           | Medium     |
| 10 | How do you protect your database from malicious input that tries to manipulate queries?                                                   | Use parameterized queries/prepared statements to avoid SQL Injection attacks by separating code and data.                                               | SQL Injection, Security Practices  | Medium     |
| 12 | A developer suggests deleting old logs with `DELETE` but you want to avoid long locks. What else can you do?                              | Use `TRUNCATE` for fast bulk deletion (if you want to remove all rows), or partition tables to drop partitions easily without locks.                    | DELETE vs TRUNCATE, Locking        | Medium     |
| 13 | Explain what happens when you create a composite primary key and why you might use one.                                                   | A composite key uses multiple columns to uniquely identify a row, useful when no single column is unique alone (e.g., in join tables).                  | Composite Keys, Primary Key        | Medium     |
| 14 | How do you decide between using an index and adding more server resources when performance degrades?                                      | First optimize queries with indexes; adding hardware helps but may be costly. Indexes give better performance gains for read-heavy loads.               | Indexing, Performance Tuning       | Hard       |
| 15 | In your database, some queries need fast inserts and others need fast reads. How can you balance this?                                    | Balance normalization and denormalization. Normalize for inserts and data integrity; denormalize for faster reads and aggregation.                      | Denormalization vs Normalization   | Hard       |

---

### 🔷 DBMS

---

### ✅ Q1. Write a query to find all users with email ending in `@gmail.com`.

**Answer:**

```sql
SELECT * FROM Users WHERE email LIKE '%@gmail.com';
```

**Concept(s):** SQL `LIKE` operator, pattern matching
**Difficulty:** Easy

---

### ✅ Q2. Write a query to get the total number of orders placed by each user.

**Answer:**

```sql
SELECT user_id, COUNT(*) AS total_orders
FROM Orders
GROUP BY user_id;
```

**Concept(s):** Aggregation, `GROUP BY`
**Difficulty:** Easy

---

### ✅ Q3. Write a query to fetch all courses that have no students enrolled.

**Answer:**

```sql
SELECT c.course_id, c.course_name
FROM Courses c
LEFT JOIN StudentCourse sc ON c.course_id = sc.course_id
WHERE sc.student_id IS NULL;
```

**Concept(s):** `LEFT JOIN`, filtering for non-matches
**Difficulty:** Medium

---

### ✅ Q4. Write a query to update the salary of employees in department 10 by 10%.

**Answer:**

```sql
UPDATE Employees
SET salary = salary * 1.10
WHERE department_id = 10;
```

**Concept(s):** `UPDATE` statement
**Difficulty:** Easy

---

### ✅ Q5. Create a table `Student` with columns `id`, `name`, `age` where `id` is the primary key.

**Answer:**

```sql
CREATE TABLE Student (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

**Concept(s):** Table creation, primary key
**Difficulty:** Easy

---

### ✅ Q6. Write a query to delete all records from the `Logs` table.

**Answer:**

```sql
DELETE FROM Logs;
```

**Concept(s):** `DELETE` statement
**Difficulty:** Easy

---

### ✅ Q7. Write a query to find the second highest salary in `Employees`.

**Answer:**

```sql
SELECT MAX(salary) AS second_highest_salary
FROM Employees
WHERE salary < (SELECT MAX(salary) FROM Employees);
```

**Concept(s):** Subquery, aggregate functions
**Difficulty:** Medium

---

### ✅ Q8. Write a query to add a new column `email` to the `Users` table.

**Answer:**

```sql
ALTER TABLE Users ADD email VARCHAR(255);
```

**Concept(s):** `ALTER TABLE`
**Difficulty:** Easy

---

### ✅ Q9. Write a query to create an index on the `username` column of the `Users` table.

**Answer:**

```sql
CREATE INDEX idx_username ON Users(username);
```

**Concept(s):** Index creation
**Difficulty:** Medium

---

### ✅ Q10. Write a query to join `Orders` and `Users` to show orders along with user names.

**Answer:**

```sql
SELECT o.order_id, u.username, o.order_date
FROM Orders o
JOIN Users u ON o.user_id = u.user_id;
```

**Concept(s):** `JOIN` operation
**Difficulty:** Medium

---
