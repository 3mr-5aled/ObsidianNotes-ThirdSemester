# 🧠 DBMS Lab 1

**SQL Fundamentals - Lab 1**

---

## 🧾 Lab Rules

- You **MUST** attend in your section.
    
- Please commit to the lab start time.
    
- No attendance exceptions from TAs.
    
- Attendance exceptions only signed from doctors.
    

---

## 🧩 Required Installations

- **Oracle 11g Installation:**
    
    - Refer to **"Installation - Database.ppt"** for database installation.
        
    - Refer to **"Installation - Forms & Reports.ppt"** for developer installation.
        

---

## 📊 Data Retrieval (DRC) Command

### Basic `SELECT` Statement

```sql
SELECT *|{[DISTINCT] column|expression [alias],...}
FROM table;
```

In its simplest form, a SELECT statement must include:

- `SELECT` → identifies which columns
    
- `FROM` → identifies which table
    

---

### Selecting All Columns

```sql
SELECT *
FROM departments;
```

|DEPARTMENT ID|DEPARTMENT NAME|MANAGER ID|LOCATION ID|
|---|---|---|---|
|10|Administration|200|1700|
|20|Marketing|201|1800|
|50|Shipping|124|1500|
|60|IT|103|1400|
|80|Sales|149|2500|
|90|Executive|100|1700|
|110|Accounting|205|1700|
|190|Contracting||1700|

_8 rows selected._

---

### Selecting Specific Columns

```sql
SELECT department_id, location_id
FROM departments;
```

|DEPARTMENT_ID|LOCATION_ID|
|---|---|
|10|1700|
|20|1800|
|50|1500|
|60|1400|
|80|2500|
|90|1700|
|110|1700|
|190|1700|

---

### Using Arithmetic Operators

```sql
SELECT last_name, salary, salary + 300
FROM employees;
```

|LAST_NAME|SALARY|SALARY+300|
|---|---|---|
|King|24000|24300|
|Kochhar|17000|17300|
|De Haan|17000|17300|
|Hunold|9000|9300|
|Ernst|6000|6300|

_Note: The calculated column is for display only, not a permanent field._

---

### Operator Precedence

- Multiplication (`*`) and division (`/`) take priority over addition (`+`) and subtraction (`-`).
    
- Operators with the same priority are evaluated left-to-right.
    
- Use parentheses to enforce specific order.
    

```sql
SELECT last_name, salary, 12*salary+100
FROM employees;
```

---

### Using Parentheses

```sql
SELECT last_name, salary, 12*(salary+100)
FROM employees;
```

---

## 💾 Defining a Null Value

- A **null** is a value that is unavailable, unassigned, or inapplicable.
    
- It is **not** the same as zero or a blank space.
    

```sql
SELECT last_name, job_id, salary, commission_pct
FROM employees;
```

### Nulls in Arithmetic Expressions

```sql
SELECT last_name, 12*salary*commission_pct
FROM employees;
```

Arithmetic expressions containing a null evaluate to **null**.

---

## 🏷️ Defining a Column Alias

A column alias:

- Renames a column heading
    
- Is useful with calculations
    
- Immediately follows the column name
    
- The optional `AS` keyword may be used
    
- Requires double quotes for names with **spaces** or special characters like (# , $)
    

```sql
SELECT last_name "Name", salary*12 "Annual Salary"
FROM employees;
```

---

## 🧮 Duplicate Rows

By default, all rows (including duplicates) are displayed.

```sql
SELECT department_id
FROM employees;
```

To eliminate duplicates:

```sql
SELECT DISTINCT department_id
FROM employees;
```

You can specify multiple columns with `DISTINCT`.

---

## 🔍 Restricting Data

### Limiting Rows

Use the `WHERE` clause to restrict returned rows.

```sql
SELECT column|expression [alias], ...
FROM table
WHERE condition(s);
```

Comparison Operators:

- ` = ` equal
    
- `<` less than
    
- `>` greater than
    
- `<>` not equal
    

Example:

```sql
SELECT employee_id, last_name, job_id, department_id
FROM employees
WHERE department_id = 90;
```

---

### Character Strings and Dates

- Enclose strings and dates in **single quotes**.
    
- Strings are **case-sensitive**.
    
- Dates are **format-sensitive**.
    

```sql
SELECT last_name, job_id, department_id
FROM employees
WHERE last_name = 'Whalen';
```

---

### Other Comparison Operators

|Operator|Meaning|
|---|---|
|`BETWEEN ... AND ...`|Between two values (inclusive)|
|`IN (set)`|Match any value in the list|
|`LIKE`|Match a character pattern|
|`IS NULL`|Is a null value|

---

### `BETWEEN` Condition

```sql
SELECT last_name, salary
FROM employees
WHERE salary BETWEEN 2500 AND 3500;
```

---

### `IN` Condition

```sql
SELECT employee_id, last_name, salary, manager_id
FROM employees
WHERE manager_id IN (100, 101, 201);
```

---

### `LIKE` Condition

Wildcard characters:

- `%` → zero or many characters
    
- `_` → exactly one character
    

```sql
SELECT first_name
FROM employees
WHERE first_name LIKE 'S%';
```

```sql
SELECT last_name
FROM employees
WHERE last_name LIKE '_o%';
```

---

### `IS NULL` Condition

```sql
SELECT last_name, manager_id
FROM employees
WHERE manager_id IS NULL;
```

---

## ⚙️ Logical Conditions

|Operator|Meaning|
|---|---|
|`AND`|True if both are true|
|`OR`|True if either is true|
|`NOT`|True if the condition is false|

Examples:

```sql
SELECT employee_id, last_name, job_id, salary
FROM employees
WHERE salary >= 10000
AND job_id LIKE '%MAN%';
```

```sql
SELECT employee_id, last_name, job_id, salary
FROM employees
WHERE salary >= 10000
OR job_id LIKE '%MAN%';
```

```sql
SELECT last_name, job_id
FROM employees
WHERE job_id NOT IN ('IT_PROG', 'ST_CLERK', 'SA_REP');
```

---

## 📈 Sorting Data

### The `ORDER BY` Clause

- Comes last in the `SELECT` statement.
    
- Default is **ascending**.
    
- You can sort by **column name**, **expression**, or **alias**.
    
- Nulls appear **last** (ascending) or **first** (descending).
    

```sql
SELECT last_name, job_id, department_id, hire_date
FROM employees
ORDER BY hire_date;
```

### Descending Order

```sql
SELECT last_name, job_id, department_id, hire_date
FROM employees
ORDER BY hire_date DESC;
```

---