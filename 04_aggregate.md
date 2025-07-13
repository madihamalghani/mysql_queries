# Aggregate:

## What Are Aggregate Functions?

Aggregate functions **perform calculations on multiple rows** and return a **single result**.

<aside>
🚫

- COUNT( )⇒ Counts number of rows
- SUM( )⇒ Adds up numeric values
- AVG( )⇒ Calculates average value
- MAX( )⇒ Finds the maximum value
- MIN( )⇒ Finds the minimum value
- GROUP_CONCAT( )⇒ Combines values into a single string (optional, extra feature)
</aside>

## Examples:

1. **Count: Total rows**

```sql
SELECT COUNT(*) FROM students;
-- Count all the rows in students 
```

**Count non-null values in a specific column**

```sql
SELECT COUNT(email) FROM users;
```

This counts only the rows where the `email` column is **not NULL**.

**Count rows with a condition:**

```sql

SELECT COUNT(*) FROM orders WHERE status = 'completed';

```

This counts all rows in the `orders` table where `status` is `'completed'`.

1. **Count grouped data:**

```sql

SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

This counts the number of employees in each department.

1. **SUM: Total of numeric column**

```sql
SELECT SUM(age) FROM students;
-- Result: It will sum the age of all students
```

1. **AVG: Average of Column**

```sql
SELECT AVG(age) FROM students;
```

1. `MAX()` / `MIN()`: Largest / Smallest value

```sql
SELECT MAX(age) FROM students; -- 22
SELECT MIN(age) FROM students; -- 19
```

### **Aggregate With Where:**

```sql
SELECT AVG(age) FROM students WHERE gender = 'M';
```

→ Average age of male students only.
