# 📘 SQL Practice: Selecting Data from Relational Databases

Welcome! In this assignment you will practice writing **SELECT queries** in PostgreSQL.  
You'll use the [Crunchy Data Playground](https://www.crunchydata.com/developers/playground) to write and test your SQL.

---

## 🎯 Goal

Practice selecting data using:
- SELECT
- WHERE
- ORDER BY
- Aggregate functions (AVG, COUNT, SUM)
- GROUP BY, HAVING
- Subqueries
- Window functions

---

## 🗂️ 1️⃣ Table Schema

We will work with an **employees** table:

| Column     | Type    | Example              |
|------------|---------|---------------------|
| id         | SERIAL  | 1                    |
| name       | TEXT    | 'Alice'              |
| department | TEXT    | 'Engineering'        |
| salary     | NUMERIC | 70000.00             |

---

## 🌱 2️⃣ Setup: Create Table and Insert Data

### ▶️ 2.1 Create the Table

```sql
CREATE TABLE employees (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  department TEXT NOT NULL,
  salary NUMERIC NOT NULL
);
````

---

### ▶️ 2.2 Insert Sample Data

```sql
INSERT INTO employees (name, department, salary) VALUES
  ('Alice', 'HR', 55000),
  ('Bob', 'Engineering', 75000),
  ('Charlie', 'Engineering', 72000),
  ('Diana', 'Sales', 60000),
  ('Eve', 'HR', 58000),
  ('Frank', 'Sales', 64000),
  ('Grace', 'Engineering', 80000),
  ('Heidi', 'Marketing', 52000),
  ('Ivan', 'Marketing', 54000),
  ('Judy', 'HR', 50000);
```

---

## 🧭 3️⃣ Practice Questions

Below are the **plain-English questions** for you to solve in SQL.

### ✅ SELECT Basics

* 1️⃣ Show all data about all employees.
* 2️⃣ Show only `name` and `salary` of all employees.
* 3️⃣ List all distinct department names.
* 4️⃣ Count all employees in the company.
* 5️⃣ Count employees in Engineering.

---

### ✅ Filtering with WHERE

* 6️⃣ Show employees with salary greater than 60000.
* 7️⃣ List all employees in the Sales department.
* 8️⃣ Show employees in HR or Sales.
* 9️⃣ Show employees not in HR.
* 🔟 Find employees with salary between 50000 and 70000.
* 1️⃣1️⃣ List employees whose names start with 'A'.

---

### ✅ Sorting with ORDER BY

* 1️⃣2️⃣ Show all employees sorted by salary (lowest to highest).
* 1️⃣3️⃣ Show all employees sorted by salary (highest to lowest).
* 1️⃣4️⃣ Show all employees sorted by department and then salary descending.
* 1️⃣5️⃣ Show the top 3 highest-paid employees.

---

### ✅ Aggregates (AVG, SUM, COUNT)

* 1️⃣6️⃣ What is the average salary of all employees?
* 1️⃣7️⃣ What is the total of all salaries?
* 1️⃣8️⃣ How many employees are in each department?
* 1️⃣9️⃣ What is the average salary per department?
* 2️⃣0️⃣ What is the highest salary per department?
* 2️⃣1️⃣ What is the lowest salary per department?

---

### ✅ GROUP BY + HAVING

* 2️⃣2️⃣ Which departments have more than 2 employees?
* 2️⃣3️⃣ Which departments have an average salary above 60000?
* 2️⃣4️⃣ Which departments have a total salary cost above 150000?

---

### ✅ Subqueries

* 2️⃣5️⃣ Which employees have a salary above the overall average?
* 2️⃣6️⃣ Which employees earn above their department average?
* 2️⃣7️⃣ Which departments have at least one employee with salary over 80000?
* 2️⃣8️⃣ Find the top earner in each department. *(Hint: this may need multiple queries)*

---

### ✅ Window Functions

* 2️⃣9️⃣ Show employees with their rank within their department based on salary.
* 3️⃣0️⃣ Show employees with their dense rank within department based on salary.
* 3️⃣1️⃣ Show employees with a running total of salary ordered by salary.
* 3️⃣2️⃣ For each employee, show the average salary in their department.

---

### ✅ Challenge Queries

* 3️⃣3️⃣ Show Engineering employees who earn above the Engineering department average.
* 3️⃣4️⃣ Show each employee along with the difference between their salary and the department average.
* 3️⃣5️⃣ Show the top 2 earners in each department.
* 3️⃣6️⃣ Which department has the highest average salary?
* 3️⃣7️⃣ List employees who have the same salary as someone in a different department.

---

## 💡 4️⃣ SQL Tips and Hints

✅ Use `SELECT * FROM employees` to see all the data first.
✅ Use `WHERE` to filter rows by conditions.
✅ Use `ORDER BY salary DESC` to sort highest to lowest.
✅ Use `DISTINCT` to get unique values.
✅ Use aggregate functions like `AVG()`, `SUM()`, `COUNT()`.
✅ Combine `GROUP BY` with aggregates to get stats per department.
✅ Use `HAVING` to filter after grouping.
✅ Use subqueries in `WHERE` clauses for comparisons.
✅ Use window functions like `RANK()` OVER (PARTITION BY ... ORDER BY ...).

---

## 🔗 Resources


## 🔗 Resources

- 📌 **PostgreSQL Tutorial Home**  
  [https://www.w3schools.com/postgresql/index.php](https://www.w3schools.com/postgresql/index.php)



* Crunchy Data Playground: [https://www.crunchydata.com/developers/playground](https://www.crunchydata.com/developers/playground)

---

## ✅ 5️⃣ How to Use This

1. Copy the **CREATE TABLE** and **INSERT** commands into Crunchy Playground.
2. Paste and run them to create your test data.
3. Work through the questions one by one in SQL.
4. Save your favorite queries for sharing!

---

Happy SQL hacking! 🧑‍💻🎯
