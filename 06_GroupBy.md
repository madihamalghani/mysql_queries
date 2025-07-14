# Group by:

`GROUP BY` groups rows that have the **same values** in specified columns, so you can apply **aggregate functions** (like `COUNT`, `SUM`, `AVG`, etc.) **on each group**.

Syntax:

```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name;
```

**Examples:**

1. **Count by Gender**

```sql
SELECT gender, COUNT(*) AS total_students
FROM students
GROUP BY gender;
```

**What’s happening here:**

<aside>
🚫

- SELECT gender⇒  (column)
- COUNT( * ) AS total_students ⇒ means count all rows and name their column as total_students
- FROM students⇒  from table with name students
- GROUP BY gender; ⇒ means group Count by gender

**Result:**

Total gender 2 (M,F) now 2 output records: one with M gender containing  Total_students as count of M records. Other with F gender containing Total_students as count of F records

</aside>

1. **Average Age by Gender:**

```sql
SELECT gender, AVG(age) AS avg_age
FROM students
GROUP BY gender;
```

1. **Total age for each unique age**

```sql
SELECT age, COUNT(*) AS count_of_students
FROM students
GROUP BY age;
```

**Output:**

| **Age** | **count_of_students** |
| --- | --- |
| 20 | 1 |
| 22 | 1 |
| 21 | 2 |
| 23 | 1 |

## Important Points

- Every column in the `SELECT` must either be:
    - Inside an aggregate function (`SUM()`, `COUNT()`, etc.)
    - OR included in the `GROUP BY` clause

```sql
-- ❌ Invalid:
SELECT name, COUNT(*) FROM students GROUP BY gender;
-- Error because `name` is not aggregated or grouped
```

## Now Group By With Where:

**`GROUP BY` with `WHERE`** — this is super useful when you want to **filter rows before grouping**.

### Order of Execution:

1. **`WHERE`** → Filters the raw rows
2. **`GROUP BY`** → Groups the filtered rows
3. **Aggregate functions** → Are applied to each group

**Syntax:**

```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
WHERE condition
GROUP BY column_name;
```

**Example:** Group by `gender`, but only include students **aged 21 or more.**

```sql
SELECT gender, COUNT(*) AS total
FROM students
WHERE age >= 21
GROUP BY gender;
```

Output:

| **gender** | **total** |
| --- | --- |
| Male | 2 |
| Female | 2 |

**Example:** Average age of students **with age > 20**, grouped by gender

```sql
SELECT gender, AVG(age) AS average_age
FROM students
WHERE age > 20
GROUP BY gender;
```

### Thus:

<aside>
🚫

Group by ⇒ provide multi records based on conditions and data

**where⇒ always comes before group by**

</aside>

Means ⇒ first filtering then grouping

---

## How MySQL Grouping Works?

> In grouping:
> 
> 
> **1. sort** → **2. group** → **3. action**
> 
> What does it mean?
> 

It’s actually a simple way to understand **how SQL processes grouped data** step by step! 

## **Sort**

Not always required, but it's how SQL organizes the data **behind the scenes** to make grouping easier.

- Think of SQL scanning your table and organizing it by the `GROUP BY` column.
- Example: If you group by `gender`, SQL may **sort by gender internally**.

📌 You don’t need to manually sort the table, but it's part of how SQL handles it internally.

## 2. **Group**

Now, SQL **groups rows with the same value** in the column you specified.

Example:

```sql
SELECT gender, COUNT(*) FROM students GROUP BY gender;
```

It makes groups like:

- Group 1: All rows where gender = 'M'
- Group 2: All rows where gender = 'F'

## 3. **Action** (Apply Aggregate Functions)

Once grouped, SQL performs **aggregate actions** like:

- `COUNT(*)` → Count of records in each group
- `SUM(marks)` → Total marks for each group
- `AVG(age)` → Average age per group

Each group is processed separately, and only **one row per group** is returned.
