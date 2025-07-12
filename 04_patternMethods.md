# Pattern Methods:

Mainly done by **LIKE** operator.

```sql
SELECT * FROM table_name WHERE column_name LIKE 'pattern';

```

### Concept of `LIKE`:

- **`LIKE` allows pattern matching** using **wildcards**

There are mainly two wildcards used with `LIKE`: %, _

<aside>
🚫

- %  ⇒ Represents zero, one or many characters
- _ ⇒ Represents a single character
</aside>

**Examples:**

1. **Find names starting with "A":**

```sql
SELECT * FROM students WHERE name LIKE 'A%';
```

→ Matches: `Ali`, `Adeel`, `Amna`

1. **Find names ending with "a":**

```sql
SELECT * FROM students WHERE name LIKE '%a';
```

→ Matches: `Mona`, `Nadia`

1. **Find names that contain "an":**

```sql
SELECT * FROM students WHERE name LIKE '%an%';
```

→ Matches: `Zain`, `Danish`, `Anam`

1. **Find names with second letter as 'a':**

```sql
SELECT * FROM students WHERE name LIKE '_a%';
```

→ Matches: `Sara`, `Nadia`, `Haris`

1. **Case Sensitive:**

Yes! `LIKE` is **not case-sensitive** by default in MySQL (unless the collation of the column is case-sensitive).

1. **Not LIKE:**

```sql
SELECT * FROM students WHERE name NOT LIKE 'A%';
```

→ Will give all names **not starting with A**.

## 🙅‍♂️ What about ?

> - is not a pattern character in SQL LIKE queries.
> 
> 
> It **does nothing special** in pattern matching unless you're using **Regular Expressions** (which is a separate topic — not used with `LIKE`, but with `REGEXP`).
> 

So this will not work

```sql
SELECT * FROM students WHERE name LIKE 'A-Z%'; -- ❌ Not valid
```

Instead, use:

```sql
SELECT * FROM students WHERE name REGEXP '^[A-Z]'; --  Starts with capital letter
```

| Pattern | Matches |
| --- | --- |
| `'_a%'` | Any string where 2nd letter is **a** |
| `'S__'` | Any 3-letter string starting with **S** |
| `'___a%'` | 4th character is **a** |
| `'S%l'` | Starts with **S** and ends with **l** (e.g., `Sahil`) |

