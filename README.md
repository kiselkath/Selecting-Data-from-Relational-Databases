# 📘 SQL Practice: Relational Modeling, SELECT Queries, Foreign Keys, Indexes

Welcome! In this assignment you will practice **relational modeling** and **SELECT queries** in PostgreSQL.  
You'll use the [Crunchy Data Playground](https://www.crunchydata.com/developers/playground) to write and test your SQL.

---

## 🎯 Goal

Practice:

✅ Creating related tables with foreign keys  
✅ Adding sample data  
✅ Creating indexes (B-Tree, Hash)  
✅ Writing SELECT queries using:
- SELECT
- WHERE
- ORDER BY
- Aggregate functions
- GROUP BY, HAVING
- Subqueries
- Window functions

---

## 🗂️ 1️⃣ Table Schema

We will work with **HR Services** data modeling employees, departments, and salaries.

### 🗄️ Tables

#### 🧩 departments
| Column       | Type    | Example        |
|--------------|---------|----------------|
| id           | SERIAL  | 1              |
| name         | TEXT    | 'Engineering'  |

---

#### 🧩 employees
| Column       | Type    | Example        |
|--------------|---------|----------------|
| id           | SERIAL  | 1              |
| name         | TEXT    | 'Alice'        |
| department_id| INT     | 1 (FK)         |
| salary       | NUMERIC | 70000.00       |

---

#### 🧩 salaries
| Column       | Type    | Example        |
|--------------|---------|----------------|
| id           | SERIAL  | 1              |
| employee_id  | INT     | 1 (FK)         |
| amount       | NUMERIC | 70000.00       |
| effective_date | DATE  | '2024-01-01'   |

---

## 🌱 2️⃣ Setup: Create Tables with Foreign Keys

### ▶️ 2.1 Create Departments Table

```sql
CREATE TABLE departments (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL UNIQUE
);
````

---

### ▶️ 2.2 Create Employees Table with Foreign Key

```sql
CREATE TABLE employees (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  department_id INT REFERENCES departments(id),
  salary NUMERIC NOT NULL
);
```

---

### ▶️ 2.3 Create Salaries Table with Foreign Key

```sql
CREATE TABLE salaries (
  id SERIAL PRIMARY KEY,
  employee_id INT REFERENCES employees(id),
  amount NUMERIC NOT NULL,
  effective_date DATE NOT NULL
);
```

---

## 🏗️ 3️⃣ Add Indexes

✅ B-Tree index (default for PK) is created automatically.
✅ Add additional indexes:

```sql
-- B-Tree index on salary for employees
CREATE INDEX idx_employees_salary ON employees (salary);

-- Hash index on department name
CREATE INDEX idx_departments_name_hash ON departments USING HASH (name);
```

---

## 🍀 4️⃣ Insert Sample Data

### Departments

```sql
INSERT INTO departments (name) VALUES
  ('HR'),
  ('Engineering'),
  ('Sales'),
  ('Marketing');
```

---

### Employees

```sql
INSERT INTO employees (name, department_id, salary) VALUES
  ('Alice', 1, 55000),
  ('Bob', 2, 75000),
  ('Charlie', 2, 72000),
  ('Diana', 3, 60000),
  ('Eve', 1, 58000),
  ('Frank', 3, 64000),
  ('Grace', 2, 80000),
  ('Heidi', 4, 52000),
  ('Ivan', 4, 54000),
  ('Judy', 1, 50000);
```

---

### Salaries

```sql
INSERT INTO salaries (employee_id, amount, effective_date) VALUES
  (1, 55000, '2024-01-01'),
  (2, 75000, '2024-01-01'),
  (3, 72000, '2024-01-01'),
  (4, 60000, '2024-01-01'),
  (5, 58000, '2024-01-01'),
  (6, 64000, '2024-01-01'),
  (7, 80000, '2024-01-01'),
  (8, 52000, '2024-01-01'),
  (9, 54000, '2024-01-01'),
  (10, 50000, '2024-01-01');
```

---

## 🧭 5️⃣ Practice Questions

### ✅ SELECT Basics

1️⃣ Show all employees with their department name.
2️⃣ Show only `name` and `salary` of all employees.
3️⃣ List all distinct department names.
4️⃣ Count all employees.
5️⃣ Count employees per department.

---

### ✅ Filtering with WHERE

6️⃣ Employees with salary > 60000.
7️⃣ Employees in Sales department.
8️⃣ Employees in HR or Sales.
9️⃣ Employees not in HR.
🔟 Employees with salary between 50000 and 70000.

---

### ✅ Sorting

1️⃣1️⃣ Employees sorted by salary (lowest to highest).
1️⃣2️⃣ Employees sorted by department and salary descending.
1️⃣3️⃣ Top 3 highest-paid employees.

---

### ✅ Aggregates

1️⃣4️⃣ Average salary of all employees.
1️⃣5️⃣ Total salary cost.
1️⃣6️⃣ Number of employees per department.
1️⃣7️⃣ Average salary per department.
1️⃣8️⃣ Highest salary per department.

---

### ✅ GROUP BY + HAVING

1️⃣9️⃣ Departments with more than 2 employees.
2️⃣0️⃣ Departments with avg salary > 60000.
2️⃣1️⃣ Departments with total salary cost > 150000.

---

### ✅ Subqueries

2️⃣2️⃣ Employees above overall avg salary.
2️⃣3️⃣ Employees earning above department average.
2️⃣4️⃣ Departments with at least one employee > 80000.
2️⃣5️⃣ Top earner in each department.

---

### ✅ Window Functions

2️⃣6️⃣ Employees with rank in department by salary.
2️⃣7️⃣ Dense rank of salary within department.
2️⃣8️⃣ Running total of salary ordered by salary.
2️⃣9️⃣ For each employee, show avg salary in their department.

---

### ✅ Challenge Queries

3️⃣0️⃣ Engineering employees earning above Engineering average.
3️⃣1️⃣ Each employee with difference from department avg.
3️⃣2️⃣ Top 2 earners in each department.
3️⃣3️⃣ Department with highest avg salary.
3️⃣4️⃣ Employees with same salary as someone in a different department.

---

### ✅ Foreign Keys and Joins

3️⃣5️⃣ List all employees with department name using JOIN.
3️⃣6️⃣ List all salaries with employee names.
3️⃣7️⃣ List employees and their salary history.

---

### ✅ Index Usage

3️⃣8️⃣ Check which indexes exist.
3️⃣9️⃣ Explain how query plan uses index on employees.salary.
4️⃣0️⃣ Test hash index on departments.name with an equality filter.

---

## 💡 6️⃣ SQL Tips and Hints

✅ Use `JOIN` to combine tables.

✅ Use `WHERE` to filter rows.

✅ Use `ORDER BY salary DESC` to sort.

✅ Use `DISTINCT` for unique values.

✅ Use aggregate functions like `AVG()`, `SUM()`, `COUNT()`.

✅ Combine `GROUP BY` with aggregates.

✅ Use `HAVING` to filter after grouping.

✅ Use subqueries in `WHERE`.

✅ Use window functions like `RANK() OVER`.

✅ Check existing indexes with `\di` in psql.


---

## 🔗 Resources

* 📌 **PostgreSQL Tutorial Home**
  [https://www.w3schools.com/postgresql/index.php](https://www.w3schools.com/postgresql/index.php)

* 🌐 **Crunchy Data Playground**
  [https://www.crunchydata.com/developers/playground](https://www.crunchydata.com/developers/playground)

---

## ✅ 7️⃣ How to Use This

1. Copy the **CREATE TABLE** and **INSERT** commands into Crunchy Playground.
2. Paste and run them to set up your database.
3. Work through the questions one by one.
4. Use the tips and resources to help you solve them.
5. Save your queries to share with the group!

---

Happy SQL hacking! 🧑‍💻🎯

