# 🧩 DBMS Lab 3 – SQL Fundamentals (Oracle Syntax)
---
## 📘 Overview

> [!summary]
> This lab covers **Subqueries**, **Joins**, and **Data Manipulation Language (DML)** operations in Oracle SQL. You’ll learn how subqueries execute within other queries, how to combine data from multiple tables, and how to modify table data using `INSERT`, `UPDATE`, and `DELETE` statements.

---
## **1. Subqueries**

> [!definition]
> A **subquery** (or inner query) is a **SELECT statement inside another SQL statement**. The inner query runs first, and its result is used by the outer (main) query.

> [!tip]
> Subqueries can appear in **WHERE**, **HAVING** clauses.
  

### **General Syntax**
```sql
SELECT select_list
FROM   table
WHERE  column operator
       (SELECT select_list
        FROM   table);
```

> [!flowchart]
> ```mermaid
> flowchart TD
>     A[Inner Query Executes First] --> B[Result Set Returned]
>     B --> C[Main Query Uses Result Set]
>     C --> D[Final Output Returned to User]
> ```
### **Rules**

- Always **enclose** subqueries in parentheses.  
- Place subquery on the **right side** of the comparison operator.  
- The `ORDER BY` clause **cannot** be used inside a subquery.  
- Subqueries are useful when you must compare data **within the same table** or **across tables**.

---

### **Example 1 – Using a Subquery**
**Question:** Display employees earning more than employee 141.

```sql
SELECT last_name
FROM   employees
WHERE  salary >
       (SELECT salary
        FROM   employees
        WHERE  employee_id = 141);
```

**Explanation:**  
- The inner query retrieves the salary of employee 141.  
- The outer query lists employees earning more than that salary.  

> [!note]
> This is a **single-row subquery** since it returns only one value.

---
### **Example 2 – Subquery with Another Table**
**Question:** Display employees who work in the **Sales** department.
```sql
SELECT last_name, job_id
FROM   employees
WHERE  department_id =
       (SELECT department_id
        FROM   departments
        WHERE  department_name = 'Sales');
```

> [!summary]
> The result from the `departments` table is used to filter rows from `employees`.

---
### **Types of Subqueries**

| Type             | Description           | Operators Used                    | Visuals                              |
| ---------------- | --------------------- | --------------------------------- | ------------------------------------ |
| **Single-row**   | Returns **one row**   | ` = `, `<`, `>`, `<=`, `>=`, `<>` | ![[Pasted image 20251021170651.png]] |
| **Multiple-row** | Returns **many rows** | `IN`, `ANY`, `ALL`, `EXISTS`      | ![[Pasted image 20251021170658.png]] |

> [!example]
> ```sql
> SELECT department_id, MIN(salary)
> FROM   employees
> GROUP BY department_id
> HAVING MIN(salary) >
>        (SELECT MIN(salary)
>         FROM   employees
>         WHERE  department_id = 50);
> ```
> **Purpose:** Displays departments whose minimum salary exceeds that of department 50.

---  
### **Common Subquery Error**
```sql
SELECT employee_id, last_name
FROM   employees
WHERE  salary =
       (SELECT MIN(salary)
        FROM   employees
        GROUP BY department_id);
```

> [!warning]
> ⚠️ ORA-01427: single-row subquery returns more than one row  
> **Fix:** Change ` = ` to `IN`.
  
---
## **2. Joining Tables**

> [!definition]
> A **JOIN** is used to combine data from **two or more tables** based on a related column.
  
> [!tip]
> To join `n` tables, you need **at least (n−1)** join conditions.
  
### **Basic Syntax**
```sql
SELECT t1.column, t2.column
FROM   table1 t1, table2 t2
WHERE  t1.column = t2.column;
```

> [!mermaid]
> ```mermaid
> erDiagram
>     EMPLOYEES ||--o{ DEPARTMENTS : belongs_to
>     EMPLOYEES {
>         int EMPLOYEE_ID
>         string LAST_NAME
>         int DEPARTMENT_ID
>     }
>     DEPARTMENTS {
>         int DEPARTMENT_ID
>         string DEPARTMENT_NAME
>     }
> ```
### **Example – Equi Join**
```sql
SELECT e.employee_id, e.last_name, e.department_id, d.department_name
FROM   employees e, departments d
WHERE  e.department_id = d.department_id;
```

> [!summary]
> This **equijoin** combines data using the equality operator ` = `.

---
### **Cartesian Product (No Join Condition)**

> [!warning]
> If you forget the join condition, every row from one table joins with every row from the other → **Cartesian Product**.

```sql
SELECT employee_id, department_name
FROM   employees, departments;
```

**Result:** If there are 10 employees and 8 departments → 80 rows.

---
### **Outer Joins (Oracle Syntax)**

> [!definition]
> Use **outer joins** to include rows that do **not meet** the join condition.

```sql
SELECT e.last_name, e.department_id, d.department_name
FROM   employees e, departments d
WHERE  e.department_id(+) = d.department_id;
```
  
> [!tip]
> The `(+)` symbol is used on the **table missing data** (the “deficient side”).

> [!example]
> Displays all departments, even those without employees.

---
### **Table Aliases**

```sql
SELECT e.employee_id, e.last_name, d.department_name
FROM   employees e, departments d
WHERE  e.department_id = d.department_id
AND    e.last_name = 'Matos';
```

> [!summary]
> Table aliases simplify long queries and **improve readability and performance**.

---
## **3. Data Manipulation Language (DML)**

> [!definition]
> DML statements modify data in tables:  
> - `INSERT` → add new rows  
> - `UPDATE` → modify existing rows  
> - `DELETE` → remove rows

---
### **INSERT Statement**

```sql
INSERT INTO departments (department_id, department_name, manager_id, location_id)
VALUES (70, 'Public Relations', 100, 1700);
```

> [!tip]
> Use **single quotes** around text and date values.

> [!example]
> ```sql
> INSERT INTO departments (department_id, department_name)
> VALUES (30, 'Purchasing');
> ```

> [!note]
> If you omit a column, it gets a **NULL** value.

---
### **UPDATE Statement**

```sql
UPDATE employees
SET    department_id = 70
WHERE  employee_id = 113;
```

> [!summary]
> Updates can affect one or many rows. Always use a `WHERE` clause to prevent unintended updates.

> [!example]
> ```sql
> UPDATE employees
> SET    job_id = 'SALES_MAN', salary = 2000
> WHERE  employee_id = 114;
> ```

---
### **DELETE Statement**

```sql
DELETE FROM departments
WHERE  department_name = 'Finance';
```

> [!warning]
> If you omit the `WHERE` clause, **all rows are deleted**.


> [!example]
> ```sql
> DELETE FROM departments WHERE department_id = 60;
> ```
> ⚠️ **ORA-02292:** Integrity constraint violated – child record found.  
> The record can’t be deleted because a foreign key in another table references it.

---

## **4. Best Practices & Optimization Tips**
  
> [!tip]
> - Use **JOINs** instead of correlated subqueries when possible — they’re faster.  
> - Avoid **SELECT \***; list only needed columns.  
> - Always alias tables when joining.  
> - Create **indexes** on columns used in join conditions.  
> - For performance-critical queries, use **EXPLAIN PLAN** to inspect execution flow.

> [!flowchart]
> ```mermaid
> flowchart TD
> A[Subquery] -->|Executes First| B[Temporary Result]
> B --> C[Outer Query Uses Result]
> C --> D[Final Filtered Output]
> ```

---
## **5. Glossary**

| Term                     | Definition                                |
| ------------------------ | ----------------------------------------- |
| **Subquery**             | Query nested inside another SQL statement |
| **Equijoin**             | Join using the equality ` = ` operator    |
| **Outer Join (+)**       | Includes unmatched rows                   |
| **DML**                  | Data Manipulation Language                |
| **Integrity Constraint** | Rule enforcing valid data relationships   |
| **Cartesian Product**    | Result when no join condition is given    |

---
## **6. Mnemonics**
> [!tip]
> - **SRO** → Subquery Runs Once (before main query).  
> - **MOP** → Modify, Observe, Protect (use WHERE for updates/deletes).  
> - **JOC** → Join, Outer join, Cartesian (join types).  

---
## **7. Potential Exam Questions**
1. What is a subquery and where can it appear in an SQL statement?  
2. Differentiate between single-row and multiple-row subqueries.  
3. Explain the purpose of outer joins and provide an example.  
4. What happens if you omit a WHERE clause in an UPDATE or DELETE statement?  
5. Describe the Oracle outer join syntax using `(+)`.  
6. Write a query to list employees who earn more than the minimum salary of their department.  
7. Explain ORA-01427 and how to correct it.  

---
## **8. Real-World Application**
- Subqueries are used in payroll systems to compare employee salaries.  
- Joins link customer and transaction tables in banking systems.  
- DML operations are fundamental for CRUD (Create, Read, Update, Delete) in applications.
---
> [!quote]
> “A good SQL query is like a clear thought – structured, optimized, and precise.” – Anonymous


## Notes
- Brackets in subqueries are essential for **exam grades**
- null keys and uncommon keys **isn't taken** in joined tables
- n - 1 data of n data in join