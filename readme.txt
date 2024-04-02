-- Step 1. Create Database Feb2023;

CREATE DATABASE Feb2024;

-- Step 2. Create a table and name it students. It should contain the following information: id, name, website, github_username, points, gender, cohort_start_date, graduated.

CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    website VARCHAR(255),
    github_user_name VARCHAR(255),
    points INT,
    gender VARCHAR(255),
    cohort_start_date DATE,
    graduated BOOLEAN
);

-- Step 3. Add three students to your table.

INSERT INTO students (id, name, website, github_user_name, points, gender, cohort_start_date, graduated)
values
( 1, 'dexter smith', 'https://this.com', 'github2', 88, 'male', '2023-09-01', true),
( 2, 'alexa smit', 'https://this2.com', 'github23', 98, 'female', '2024-06-06', true),
( 3, 'allen jones', 'https://this3.com', 'github24', 68, 'male', '2029-03-05', false);

-- Step 4. Update your table so that the student with the lowest points is given 5 more points.

UPDATE students
SET points = points + 5
WHERE id = (
    SELECT id
    FROM students
    ORDER BY points ASC
    LIMIT 1
);


-- Step 5. Update the values in your table where any student who has False for their graduation is changed to True.

UPDATE students
SET graduated = true
WHERE graduated = false;

-- Step 6. Add two more students to your table.

INSERT INTO students (id, name, website, github_user_name, points, gender, cohort_start_date, graduated)
VALUES 
( 4, 'beth smithy', 'https://this3.com', 'github29', 84, 'male', '2026-03-07', true),
( 5, 'alexa savino', 'https://this25.com', 'github239', 58, 'female', '2017-02-04', false)


-- Step 7. Delete one student from your table. 

DELETE FROM students 
WHERE name = 'beth smithy';

-- Step 8. Show all students with M selected as their gender. 

SELECT * 
FROM students 
WHERE gender = 'male';

-- Step 9. Show which students have graduated. 

SELECT * 
FROM students 
WHERE graduated = true;

-- Step 10. Alter table and add city to your table.

ALTER TABLE students
ADD COLUMN city VARCHAR(255);

-- Step 11: Get the average points from the table. 

SELECT AVG(points)
FROM students;


Step 1. Create a database named mockcompany.

CREAT DATABASE mockcompany;

-- Step 2. Create a table named employee, and have the following columns: id, name, position, currently_employed, gender, years_employed, salary, id.

CREATE TABLE employee (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    position VARCHAR(255),
    currently_employed BOOLEAN,
    gender VARCHAR(255),
    years_employed INT,
    salary INT,
    employee_id VARCHAR(255) 
);


-- Step 3. Add five employees to your table, 3 that are currently employed and two that are not.

INSERT INTO employee (id, name, position, currently_employed, gender, years_employed, salary, employee_id) 
VALUES 
    ( 1, 'John Doe', 'Software Engineer', true, 'male', 3, 175000, 'JD001'),
    ( 2, 'Jane Smith', 'Data Analyst', true, 'female', 2, 90000, 'JS002'),
    ( 3, 'Alex Johnson', 'Project Manager', true, 'male', 5, 80000, 'AJ003'),
    ( 4, 'Emily Brown', 'HR Coordinator', false, 'female', 1, 50000, 'EB004'),
    ( 5, 'Michael Davis', 'Marketing Specialist', false, 'male', 4, 40000, 'MD005');

-- Step 4. Display only the names and corresponding id numbers from your table.

SELECT name, employee_id 
FROM employee;

-- Step 5. Display only the names and corresponding id numbers of employees that are currently employed.

SELECT name, employee_id 
FROM employee 
WHERE currently_employed = true;

-- Step 6. Display only the names, corresponding id numbers, and salaries of employees that have been working for more than 5 years.

SELECT name, employee_id, salary 
FROM employee 
WHERE years_employed >= 2;

-- Step 7. Display only the names, corresponding id numbers, and years employed of those who have salaries higher than 75k.

SELECT name, employee_id, years_employed 
FROM employee 
WHERE salary > 75000;

-- Step 8: Display only the names of employees that have a d, upper or lower case, somewhere in their name.

SELECT name 
FROM employee 
WHERE name LIKE '%d%' OR name LIKE '%D%';

-- Step 9. Display only the names of employees that have an upper case T in their name.

SELECT name 
FROM employee 
WHERE name  ILIKE '%M%';

-- Step 10. Take out the gender column from the table.

ALTER TABLE employee 
DROP COLUMN gender;

-- Step 11. Figure out how many records you have in your database.

SELECT COUNT(*) AS record_count 
FROM employee;

-- Step 12. Display the name, position, and salary of the highest paid employee.

SELECT name, position, salary 
FROM employee 
ORDER BY salary DESC 
LIMIT 1;

-- Step 13. Display all employees, sorted in ascending order by name.

SELECT * 
FROM employee 
ORDER BY name ASC;

-- Step 14. Display all employees, sorted in descending order by salary.

SELECT * 
FROM employee 
ORDER BY salary DESC;

-- Step 15. Display the names and salaries of the top three highest paid employees in descending order.

SELECT name, salary 
FROM employee 
ORDER BY salary DESC 
LIMIT 3;

-- Step 16. Display the name and corresponding id number of the second highest paid employee. 

SELECT name, employee_id 
FROM employee 
ORDER BY salary DESC 
LIMIT 1 OFFSET 1;

