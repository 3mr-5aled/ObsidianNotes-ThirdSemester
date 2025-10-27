# 🧠 DBMS Lab 2

**SQL Fundamentals – Lab 2**

---

## 📘 SQL Functions

### 🧩 Single-Row Functions

#### 🔤 Character Functions

These functions are used to convert the case for character strings.

|Function|Result|
|:--|:--|
|`LOWER('SQL Course')`|sql course|
|`UPPER('SQL Course')`|SQL COURSE|
|`INITCAP('SQL Course')`|Sql Course|

---

### 🧪 Using Case Manipulation Functions

Display the employee number, name, and department number for an employee named **Higgins**.

**❌ Initial Query (fails due to case sensitivity):**

```sql
SELECT employee_id, last_name, department_id
FROM employees
WHERE last_name = 'higgins';
```

**Result:**  
`no rows selected`

**✅ Corrected Query (using LOWER function):**

```sql
SELECT employee_id, last_name, department_id
FROM employees
WHERE LOWER(last_name) = 'higgins';
```

**Result:**

|EMPLOYEE_ID|LAST_NAME|DEPARTMENT_ID|
|:--|:--|:--|
|205|Higgins|110|

---

### 📅 Using Arithmetic Operators with Dates

- `SYSDATE` returns the current date and time.
    
- Subtracting two dates returns the number of days between them.
    

**Example Query:**

```sql
SELECT last_name, (SYSDATE - hire_date) / 7 AS weeks
FROM employees
WHERE department_id = 90;
```

**Result:**

|LAST_NAME|WEEKS|
|:--|:--|
|King|744.245395|
|Kochhar|626.102538|
|De Haan|453.245395|

---

### ⚙️ General Functions: NVL

- Converts a **null** value to an actual value.
    
- Can be used with **date**, **character**, and **number** data types.
    
- The replacement value **must match the original column’s data type**.
    

**Examples:**

```sql
NVL(commission_pct, 0)
NVL(hire_date, '01-JAN-97')
NVL(job_id, 'No Job Yet')
```

#### Example: Using the NVL Function

```sql
SELECT last_name, salary, NVL(commission_pct, 0),
(salary*12)+(salary*12*NVL(commission_pct, 0)) AS an_sal
FROM employees;
```

**Result (snippet):**

|LAST_NAME|SALARY|NVL(COMMISSION_PCT,0)|AN_SAL|
|:--|:--|:--|:--|
|King|24000|0|288000|
|Kochhar|17000|0|204000|
|De Haan|17000|0|204000|
|Hunold|9000|0|108000|
|Ernst|6000|0|72000|

---

## 📊 Group Functions

Group functions work on a **set of values** to produce a **single result**.

**Types of Group Functions:**

- `AVG`
    
- `COUNT`
    
- `MAX`
    
- `MIN`
    
- `SUM`
    

**Syntax:**

```sql
SELECT [column,] group_function(column) ...
FROM table
[WHERE condition]
[GROUP BY column]
[ORDER BY column];
```

---

### Examples of Group Functions

#### 1. `AVG` and `SUM`

```sql
SELECT AVG(salary), MAX(salary), MIN(salary), SUM(salary)
FROM employees
WHERE job_id LIKE '%REP%';
```

|AVG(SALARY)|MAX(SALARY)|MIN(SALARY)|SUM(SALARY)|
|:--|:--|:--|:--|
|8150|11000|6000|32600|

---

#### 2. `MIN` and `MAX`

```sql
SELECT MIN(hire_date), MAX(hire_date)
FROM employees;
```

|MIN(HIRE_DATE)|MAX(HIRE_DATE)|
|:--|:--|
|17-JUN-97|29-JAN-00|

---

#### 3. `COUNT`

- `COUNT(*)` → counts **all rows** (including nulls and duplicates)
    
- `COUNT(column)` → counts **non-null** values only
    
- `COUNT(DISTINCT column)` → counts **unique non-null** values
    

```sql
SELECT COUNT(*) FROM employees;

SELECT COUNT(commission_pct)
FROM employees
WHERE department_id = 80;

-- Display number of distinct department values
SELECT COUNT(DISTINCT department_id)
FROM employees;
```

---

### Group Functions and Null Values

- Group functions **ignore nulls** by default.
    

```sql
SELECT AVG(commission_pct)
FROM employees;
```

- To include nulls, use `NVL`:
    

```sql
SELECT AVG(NVL(commission_pct, 0))
FROM employees;
```

---

## 📂 Grouping Data

The `GROUP BY` clause divides rows into groups.  
If the grouping column has nulls, they form a separate group.

**Syntax:**

```sql
SELECT column, group_function(column)
FROM table
[WHERE condition]
GROUP BY group_by_column
ORDER BY column;
```

**Example:**  
Display the average salary for each department.

```sql
SELECT department_id, AVG(salary)
FROM employees
GROUP BY department_id;
```

> Any column in the SELECT list not in a group function **must appear in the GROUP BY clause**.

---

### ❌ Illegal Group Queries

- Invalid:
    

```sql
SELECT department_id, COUNT(last_name)
FROM employees;
```

Error → `ORA-00937: not a single-group group function`

- Invalid:
    

```sql
SELECT department_id, AVG(salary)
FROM employees
WHERE AVG(salary) > 8000;
```

Error → `ORA-00934: group function is not allowed here`

---

## 📋 The HAVING Clause

Used to **filter groups** based on a group function.

**Syntax:**

```sql
SELECT column, group_function
FROM table
[WHERE condition]
[GROUP BY group_by_expression]
[HAVING group_condition]
[ORDER BY column];
```

#EXAM
**Execution Order:**

1. Table is identified due to FROM clause.
	
2. Rows selected via `WHERE`
    
3. Rows grouped via `GROUP BY`
    
4. Group functions applied to each group
    
5. Groups filtered via `HAVING`
    
6. Final results sorted via `ORDER BY`
    
7. `SELECT` is executed
8. 
**Example:**

```sql
SELECT department_id, MAX(salary)
FROM employees
GROUP BY department_id
HAVING MAX(salary) > 10000;
```

**Result:**

|DEPARTMENT_ID|MAX(SALARY)|
|:--|:--|
|20|13000|
|80|11000|
|90|24000|
|110|12000|

---

## 🧠 Practice Section

### Writing SQL Statements

- SQL is **not case-sensitive**.
    
- Statements can span multiple lines.
    
- Keywords **cannot** be abbreviated.
    
- Best practice:
    
    - Put each clause on a separate line.
        
    - Use indentation for readability.
        

---

### Practice Problem

**Task:** Display the minimum, maximum, sum, and average salary for each job type.

```sql
SELECT job_id, MAX(salary), MIN(salary), SUM(salary), AVG(salary)
FROM employees
GROUP BY job_id;
```

**Result:**

| JOB_ID     | MAX(SALARY) | MIN(SALARY) | SUM(SALARY) | AVG(SALARY) |     |
| :--------- | :---------- | :---------- | :---------- | :---------- | --- |
| AC_MGR     | 12008       | 12008       | 12008       | 12008       |     |
| AC_ACCOUNT | 8300        | 8300        | 8300        | 8300        |     |
| IT_PROG    | 9000        | 4200        | 28800       | 5760        |     |
| ST_MAN     | 8200        | 5800        | 36400       | 7280        |     |
| AD_ASST    | 4400        | 4400        | 4400        | 4400        |     |
| PU_MAN     | 11000       | 11000       | 11000       | 11000       |     |
| SH_CLERK   | 4200        | 2500        | 64300       | 3215        |     |
| AD_VP      | 17000       | 17000       | 34000       | 17000       |     |
| FI_ACCOUNT | 9000        | 6900        | 39600       | 7920        |     |
| MK_MAN     | 13000       | 13000       | 13000       | 13000       |     |
| PS_REP     | 10000       | 10000       | 10000       | 10000       |     |
| FI_MGR     | 12008       | 12008       | 12008       | 12008       |     |

---
# Notes
  
* In ordering by two properties it orders the first property we group first property and order the group alone   
* Orclconnhr , Orclconnscott ( college oracle DBMS )  
* Single row function returns data for each row  
* Group returns one value for multiple rows  
* Double quotation for alias only  
* Order by must be last   
* Group function must have group by a column if you selected a column without group  
* FROM , WHERE , GROUP BY, Group functions , HAVING , ORDER BY , SELECT (order of queries)