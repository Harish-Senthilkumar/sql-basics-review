-- SQL Basics Review Project
-- This file reviews beginner SQL concepts using simple example tables.

-- Example tables used in this file:
-- students(student_id, student_name, major, year_level)
-- grades(student_id, course_name, score)

-- 1. SELECT and FROM
-- SELECT chooses the columns.
-- FROM chooses the table.

SELECT student_name, major
FROM students;

-- Plain English:
-- Show each student's name and major from the students table.


-- 2. SELECT *
-- SELECT * shows all columns from a table.

SELECT *
FROM students;

-- Plain English:
-- Show every column from the students table.


-- 3. DISTINCT
-- DISTINCT removes duplicate values.

SELECT DISTINCT major
FROM students;

-- Plain English:
-- Show each major only once.


-- 4. WHERE
-- WHERE filters rows before the results are shown.

SELECT student_name, major
FROM students
WHERE major = 'Data Science';

-- Plain English:
-- Show only students whose major is Data Science.


-- 5. COUNT
-- COUNT(*) counts rows.

SELECT COUNT(*) AS student_count
FROM students;

-- Plain English:
-- Count how many students are in the students table.


-- 6. GROUP BY
-- GROUP BY puts rows into groups.

SELECT major, COUNT(*) AS students_per_major
FROM students
GROUP BY major;

-- Plain English:
-- Group students by major and count how many students are in each major.


-- 7. HAVING
-- HAVING filters groups after GROUP BY.

SELECT major, COUNT(*) AS students_per_major
FROM students
GROUP BY major
HAVING COUNT(*) >= 2;

-- Plain English:
-- Show only majors that have at least 2 students.


-- 8. ORDER BY
-- ORDER BY sorts the results.

SELECT student_name, major
FROM students
ORDER BY student_name;

-- Plain English:
-- Show students sorted alphabetically by name.


-- 9. ORDER BY DESC
-- DESC sorts from highest to lowest or Z to A.

SELECT student_name, score
FROM grades
ORDER BY score DESC;

-- Plain English:
-- Show students' scores from highest to lowest.


-- 10. AS
-- AS renames a column or calculation in the result.

SELECT COUNT(*) AS total_students
FROM students;

-- Plain English:
-- Count all students and name the result total_students.


-- 11. WITH
-- WITH creates a temporary result that can be used in the next query.

WITH data_science_students AS (
    SELECT student_id, student_name, major
    FROM students
    WHERE major = 'Data Science'
)

SELECT *
FROM data_science_students;

-- Plain English:
-- First create a temporary table of Data Science students.
-- Then show all rows from that temporary table.


-- 12. JOIN
-- JOIN combines two tables using a matching column.

SELECT students.student_name,
       grades.course_name,
       grades.score
FROM students
INNER JOIN grades
    ON students.student_id = grades.student_id;

-- Plain English:
-- Combine the students table with the grades table using student_id.
-- Show each student's name, course, and score.
