# Use of : Select, Where, In:

## 1. SELECT:

To filter rows:

```sql
SELECT column1, column2 FROM table_name;

```

Example:

```sql
SELECT name,age FROM students;
```

→ This will show `name` and `age` of **all students**.

***To select Everything:***

```sql
SELECT * FROM students;
```

## 2. `WHERE` – To filter rows (add conditions):

Filters which **rows** should be shown based on a condition.

```sql
SELECT * FROM table_name WHERE condition;
```

Example: Filter students with age above 20

```sql
SELECT * FROM students WHERE age > 20;
```

Only show female students

```sql
SELECT * FROM students WHERE gender = 'Female';
```

## 3. `IN` – To match **multiple values**

Used inside **WHERE ,** you can match values in a column. **IN** operator can be used to check choice values

```sql
SELECT * FROM table_name WHERE column_name IN (value1, value2, ...);
```

→ Shows students who are **exactly 18, 20, or 22 years old:**

```sql
SELECT * FROM students WHERE age IN (18, 20, 22);
```

→ This means:

- Look at each **row**
- Show it if the **`age` column value is 18, 20, or 22`**

It’s like writing:

```sql
WHERE age = 18 OR age = 20 OR age = 22;
```

## Combine `SELECT`, `WHERE`, and `IN`

→ Shows names and ages of **male students who are 20, 22, or 24 years old:**

```sql
SELECT name, age FROM students WHERE gender = 'Male' AND age IN (20, 22, 24);

```

