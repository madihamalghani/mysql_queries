# Having:

### What is `HAVING`?

- `HAVING` is used **to filter groups** after `GROUP BY`.
- It’s **similar to `WHERE`**, but `WHERE` filters **rows before grouping**, and `HAVING` filters **groups after aggregation**.

### Syntax:

```sql
SELECT column, AGG_FUNC(column)
FROM table
GROUP BY column
HAVING condition;
```

**Let’s Understand With Example Table:**

### Example Table: `students`

| **id** | **name** | **gender** | **age** |
| --- | --- | --- | --- |
| 1 | Ali | M | 22 |
| 2 | Zara | F | 20 |
| 3 | Danish | M | 21 |
| 4 | Amna | F | 19 |
| 5 | Zain | M | 22 |
| 6 | Sara | F | 20 |

### Example 1: How many students per gender?

```sql
SELECT gender, COUNT(*) AS total_students
FROM students
GROUP BY gender;
```

**Simple Group By : Output**

| **gender** | **total_students** |
| --- | --- |
| M | 3 |
| F | 3 |

### 💡 Now use `HAVING` to show only genders with more than 2 students:

```sql
SELECT gender, COUNT(*) AS total_students
FROM students
GROUP BY gender
HAVING COUNT(*) > 2;
-- this will show the gender(M or F) containing more than 2 students. If both genders contain more than 2 students then it will show records for both M and F. 
```

## WHERE vs HAVING — Key Difference

| **Clause** | **Works on** | **Used for** |
| --- | --- | --- |
| `WHERE` | individual rows | Filtering rows **before** grouping |
| `HAVING` | grouped data | Filtering groups **after** aggregation |

**Example with Both:**

```sql
SELECT gender, AVG(age) AS avg_age
FROM students
WHERE age >= 20
GROUP BY gender
HAVING AVG(age) > 20;
```

- `WHERE age >= 20` → filter rows before grouping
- `GROUP BY gender` → group those filtered rows
- `HAVING AVG(age) > 20` → only show groups with average age > 20
