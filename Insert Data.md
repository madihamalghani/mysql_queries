### Insert Sample Data

Let’s add some students, courses, and enrollment records:

```sql

-- Add students
INSERT INTO students (student_id, name, age, gender) VALUES
(1, 'Alice', 20, 'Female'),
(2, 'Bob', 22, 'Male'),
(3, 'Charlie', 21, 'Male'),
(4, 'Diana', 23, 'Female');

-- Add courses
INSERT INTO courses (course_id, course_name, teacher_name) VALUES
(101, 'Math', 'Mr. Smith'),
(102, 'Physics', 'Mrs. Johnson'),
(103, 'Computer Science', 'Dr. Brown');

-- Add enrollments
INSERT INTO enrollments (student_id, course_id, enrollment_date) VALUES
(1, 101, '2024-01-10'),
(1, 103, '2024-01-15'),
(2, 102, '2024-01-11'),
(3, 101, '2024-01-12'),
(3, 103, '2024-01-20'),
(4, 102, '2024-01-18');

```

or
```jsx
INSERT INTO table_name (column_names) VALUES (input their values)
***Viualize***:
***INSERT INTO student (id, name, gender) VALUES (1, 'Madiha', 'F');
OR
**Another Method: *(Not Recommended)***

INSERT INTO tablename VALUES(provide column values here)
Visualize:

INSERT INTO student VALUES (1, 'Madiha', 'F');

Explanation:

In the first command, we are defining the order of the columns. And the data is inserted in the same order.
While in second command data is inserted in the way user input it. 

That’s why: **First way is highly recommended*****
```

### Check if Data is Added

Run these queries to confirm:

```sql
SELECT * FROM students;
OR
SELECT * FROM courses;
OR
SELECT * FROM enrollments;

```

Now you will be able to see nice tables with real data 🧑‍🎓📚

