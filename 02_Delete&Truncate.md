# Delete and Truncate:

# `DELETE` – Used to remove **specific rows**

You can delete:

- a **single record**
- some **matching a condition**
- **all records** (if you don’t give a `WHERE`)

But it keeps the table **structure** and also logs each deletion (slower for large data).

**General Syntax:**

```jsx
DELETE FROM table_name WHERE condition;
```

**Delete one student : condition (student_id = 5)**

```jsx
DELETE FROM students WHERE student_id = 5;

```

**Delete all students aged over 2**

```sql
DELETE FROM students WHERE age > 22;
```

**Delete everything (be careful!)**

```sql
DELETE FROM students;
```

***(This removes all rows but the table remains)***

# *Truncate:*

***Be extra careful***

```sql
TRUNCATE TABLE students;
```

This will:

- Remove all data
- Reset any `AUTO_INCREMENT` columns

<aside>
🚫

`TRUNCATE` – Used to remove **all rows very fast**

- Deletes **everything** from a table
- Cannot delete specific rows
- **Cannot use WHERE**
- **Faster** than DELETE
- **Resets auto-increment ID** to 1
- Cannot be rolled back in some DBs (be cautious)
</aside>

## ❓ Does `DELETE` or `TRUNCATE` remove the **table** itself?

### 🔹 **No**, both `DELETE` and `TRUNCATE` only remove the **rows inside the table**, **not the table itself**.
