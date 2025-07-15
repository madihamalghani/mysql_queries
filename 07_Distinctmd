# Distinct:

## What is `DISTINCT`?

`DISTINCT` is used to **remove duplicate values** from the result of a `SELECT` query.

👉 It returns **only unique (different)** values from a column or combination of columns.

**Syntax:**

```sql
SELECT DISTINCT column_name
FROM table_name;
```

**Example 1: Get unique genders:**

```sql
SELECT DISTINCT gender FROM students;
```

**Example 2: Get unique ages**

```sql
SELECT DISTINCT age FROM students;
```

**Example 3: Unique combinations**

```sql
SELECT DISTINCT gender, age FROM students;
```

### What it means:

This query is telling MySQL:

> “Hey! Go to the students table, and show me only the unique combinations of gender and age.”
> 

So, it’s not just checking for unique `gender`, and not just for unique `age`.

It’s checking for **rows where both the `gender` and `age` together are different**.

### Example Table: `students`

| id | name | gender | age |
| --- | --- | --- | --- |
| 1 | Ali | M | 22 |
| 2 | Zara | F | 20 |
| 3 | Danish | M | 21 |
| 4 | Amna | F | 19 |
| 5 | Zain | M | 22 |
| 6 | Sara | F | 20 |

---

### What happens here?

Let’s focus only on `gender` and `age` columns:

| gender | age |
| --- | --- |
| M | 22 |
| F | 20 |
| M | 21 |
| F | 19 |
| M | 22 |
| F | 20 |

So `DISTINCT` removes duplicates and gives:

| gender | age |
| --- | --- |
| M | 22 |
| F | 20 |
| M | 21 |
| F | 19 |

✅ **Only unique gender-age pairs** are shown!

---

### 🧾 Use Case:

This kind of query is useful when you want to:

- See how many **different kinds of people** are in a table (e.g. age-gender-wise).
- Avoid duplicate entries in your result.
- Prepare clean grouped data without needing aggregation.

---

> Even if "gender" and "age" repeat individually, this returns only unique pairs.
> 

### Important Note:

- `DISTINCT` works on **all selected columns together**.
- If you write `SELECT DISTINCT col1, col2`, it treats the combination of `col1 + col2` for uniqueness.
