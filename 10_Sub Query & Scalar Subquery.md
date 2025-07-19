# Sub Query & Scalar Subquery :

### What is a **Subquery** in MySQL?

A **subquery** is a query inside another query. It's also called an **inner query** or **nested query**.

### Why use a subquery?

To use the result of one query inside another. For example:

- To find something **based on a condition**
- To **filter data** using values from another table

### Example of Subquery:

Suppose you have two tables:

### `students` table:

| id | name | marks |
| --- | --- | --- |
| 1 | John | 85 |
| 2 | Alice | 92 |
| 3 | Bob | 78 |

```sql
SELECT * 
FROM students 
WHERE marks = (SELECT MAX(marks) FROM students);
```

- The subquery `(SELECT MAX(marks) FROM students)` returns `92`.
- The outer query becomes: `SELECT * FROM students WHERE marks = 92`.

## Scalar Subquery:

### What is a **Scalar Subquery**?

A **scalar subquery** is a type of subquery that **returns only a single value** (one row and one column). It's called "scalar" because it acts like a single value (like a number or string).

### Where can it be used?

- In the `SELECT` clause
- In the `WHERE` clause
- In the `SET` clause (in `UPDATE`)

### Example of Scalar Subquery:

Let’s say you want to show **all students and the highest marks in the class**, side by side.

```sql
SELECT 
  name, 
  marks, 
  (SELECT MAX(marks) FROM students) AS highest_marks 
FROM students;

```

**Result:**

| name | marks | highest_marks |
| --- | --- | --- |
| John | 85 | 92 |
| Alice | 92 | 92 |
| Bob | 78 | 92 |
- The subquery `(SELECT MAX(marks) FROM students)` returns a **single value**, so it's a **scalar subquery**.
