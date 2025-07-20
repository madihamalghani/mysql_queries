# Union, Intersect, Except:

## Union:

The `UNION` operator is used **to combine the result of two or more `SELECT` queries** into a single result set.

**Rules for Using `UNION`:**

- Structure Same
- Order of column same
- Number of column same

**Note:** It means schema must be same.

**Syntax**

```sql
SELECT column1, column2 FROM table1
UNION
SELECT column1, column2 FROM table2;
```

### Example:

Let’s say you have two tables:

### Table: `students_2024`

| name | city |
| --- | --- |
| Alice | New York |
| Bob | Chicago |

### Table: `students_2025`

| name | city |
| --- | --- |
| Carol | Miami |
| Bob | Chicago |

---

### Query with `UNION`:

```sql

SELECT name, city FROM students_2024
UNION
SELECT name, city FROM students_2025;

```

### Result:

| name | city |
| --- | --- |
| Alice | New York |
| Bob | Chicago |
| Carol | Miami |

(Duplicate "Bob, Chicago" is removed)

---

## Intersect:

### What is `INTERSECT` in SQL?

The **`INTERSECT` operator** returns **only the rows that are common** (i.e., appear in **both** `SELECT` queries).

### Syntax:

```sql

SELECT column1, column2 FROM table1
INTERSECT
SELECT column1, column2 FROM table2;

```

Just like `UNION`, both `SELECT` queries must:

- Have the same number of columns
- Have matching data types
- The columns must be in the same order

### ❗But... in MySQL ❗

> MySQL does NOT support INTERSECT directly 😮
> 

---

## Except:

The **`EXCEPT`** operator returns the **rows from the first query** that **do NOT exist in the second query**.

### Syntax (standard SQL):

```sql
SELECT column1, column2 FROM table1
EXCEPT
SELECT column1, column2 FROM table2;

```

---

