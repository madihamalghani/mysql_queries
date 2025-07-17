# Join:

A **JOIN** combines rows from **two or more tables** based on a related column between them — usually a **foreign key**.

### Let's take these two tables:

### `students` table:

| student_id | name | age |
| --- | --- | --- |
| 1 | Ali | 22 |
| 2 | Zara | 20 |
| 3 | Danish | 21 |
| 4 | Amna | 19 |

### `enrollments` table:

| enroll_id | student_id | course_id | enroll_date |
| --- | --- | --- | --- |
| 1 | 1 | 101 | 2024-01-10 |
| 2 | 1 | 103 | 2024-01-15 |
| 3 | 2 | 102 | 2024-01-11 |
| 4 | 3 | 101 | 2024-01-12 |

## Inner Join:

Shows only the records that have matching data in **both tables**.

👉 `INNER JOIN` returns only the **matching rows** from **two or more tables** — where the **joined column values are equal**.

If there's **no match**, the row is **not included** in the result.

### 🎓 Think of it like this:

You have two groups:

- 🎒 Students
- 📚 Enrollments

You want to see **only** students **who are enrolled** in at least one course. That’s what `INNER JOIN` gives you.

**Syntax:**

```sql
SELECT students.name, enrollments.course_id
FROM students
INNER JOIN enrollments
ON students.student_id = enrollments.student_id;
```

### 💡 What’s happening here:

- `INNER JOIN` connects the two tables **only where `students.student_id = enrollments.student_id`**
- If a student exists in `students` but not in `enrollments`, they are not shown

**Output of Example Table:**

| name | course_id |
| --- | --- |
| Ali | 101 |
| Ali | 103 |
| Zara | 102 |
| Danish | 101 |
- Amna is **not shown** because she’s not in the `enrollments` table.

<aside>
🚫

- inner join ⇒ Returns only rows where there is a match in **both tables**
- ON ⇒ Defines the condition to match the rows (usually primary key = foreign key)
</aside>

---

## Left Join ( LEFT OUTER JOIN):

## What is `LEFT JOIN`?

👉 `LEFT JOIN` returns:

- **All rows from the LEFT table**
- The **matching rows** from the RIGHT table
- If there’s **no match** in the RIGHT table, it shows **`NULL`** in those columns

## Imagine:

You have a list of **all students**, and you want to see **their enrollments** — even if some students are not enrolled in any course.

### Example:

Using above 2 tables with student as left side and enrollment as right side.

**Query:**

```sql
SELECT students.name, enrollments.course_id
FROM students
LEFT JOIN enrollments
ON students.student_id = enrollments.student_id;
```

**Output:**

| name | course_id |
| --- | --- |
| Ali | 101 |
| Ali | 103 |
| Zara | 102 |
| Danish | 101 |
| Amna | NULL       ← not enrolled |

## What happened?

- All students are shown (from `students` table)
- If they have a course, it's shown
- If they don’t have a course (like **Amna**), `course_id` is **NULL**

---

## What is `RIGHT JOIN`?

👉 `RIGHT JOIN` returns:

- **All rows from the RIGHT table**
- The **matching rows** from the LEFT table
- If there’s **no match** in the LEFT table, you’ll see **`NULL`** for those columns

## When to use:

Use `RIGHT JOIN` when you want to **keep all records from the right-side table**, even if the left table has no matching rows.

**Example:**

Take same tables: students (left), enrollments(right)

```sql
SELECT students.name, enrollments.course_id
FROM students
RIGHT JOIN enrollments
ON students.student_id = enrollments.student_id;
```

**Output:**

| **name** | **course_id** |
| --- | --- |
| Ali | 101 |
| Ali | 103 |
| Zara | 102 |
| Danish | 101 |
| NULL | 105   ← no matching student in `students` |

## What happened?

- All rows from `enrollments` are shown (RIGHT table)
- Matching student names are fetched from `students`
- If student_id `5` is not in `students`, it returns `NULL` for the name

---

**Comparison Table:**

| JOIN Type | Keeps All LEFT Table | Keeps All RIGHT Table |
| --- | --- | --- |
| `INNER JOIN` | ❌ No | ❌ No |
| `LEFT JOIN` | ✅ Yes | ❌ No |
| `RIGHT JOIN` | ❌ No | ✅ Yes |

---

<aside>
🚫

**Full join also exists but it is not supported by MySQL**

</aside>

## Cross Join In SQL:

A **CROSS JOIN** combines **every row of one table** with **every row of another table**.

This is also called a **Cartesian product**.

### Simple Example:

Imagine:

**Table A**

fruit

---

Apple

---

Banana

---

**Table B**

color

---

Red

---

Yellow

---

---

### CROSS JOIN Result:

```sql

SELECT *
FROM TableA
CROSS JOIN TableB;
```

| fruit | color |
| --- | --- |
| Apple | Red |
| Apple | Yellow |
| Banana | Red |
| Banana | Yellow |

 Every fruit is combined with every color.

---

## Syntax of CROSS JOIN

```sql

SELECT *
FROM table1
CROSS JOIN table2;
```

or just:

```sql
SELECT *
FROM table1, table2;
```

(but this form is less readable)

## Key Points:

- It does **not** need any `ON` condition.
- Result = (Number of rows in table1) × (Number of rows in table2)
- ⚠️ Be careful: if both tables are large, the result will be **very large**!

---

## Full Join:

### What is `FULL JOIN` (also called `FULL OUTER JOIN`)?

A **FULL JOIN** returns:

- All rows from the **left table**
- All rows from the **right table**
- And where they match, combines them
- If there’s **no match**, it shows `NULL` in place of missing values.

### Simple Example:

### 🟦 Table A – `students_2024`

name

---

Alice

---

Bob

---

### 🟩 Table B – `students_2025`

name

---

Bob

---

Carol

---

### FULL JOIN Result:

```sql

SELECT *
FROM students_2024
FULL JOIN students_2025
ON students_2024.name = students_2025.name;

```

| students_2024.name | students_2025.name |
| --- | --- |
| Alice | NULL |
| Bob | Bob |
| NULL | Carol |

 It includes:

- Bob (matched in both)
- Alice (only in 2024)
- Carol (only in 2025)

---

