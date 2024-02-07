# Lab-02 Answers

```postgresql
-- Create a view for tracks names and the subjects which belong to it.

CREATE VIEW track_subject_view AS 
SELECT 
	t.track_name ,
	s.subject_name
From
	Track AS t 
INNER JOIN  
	Track_Subject AS ts ON t.id = ts.track_id
INNER JOIN 
Subject AS s ON s.id = ts.subject_id;

SELECT * FROM track_subject_view;

-- Create a view for student names with their subject's names which will study.

CREATE VIEW student_subject_view AS
SELECT 
	stu.student_name,
	sub.subject_name
FROM
Student as stu
INNER JOIN 
	student_subject ON stu.id =  student_subject.student_id
INNER JOIN 
	Subject as sub ON sub.id = student_subject.subject_id;

SELECT * FROM student_subject_view;
```

```postgresql
-- Add gender column for the student table[Enum]. It holds two value (male or female)

CREATE TYPE gender AS ENUM('male', 'female')

ALTER TABLE Student
ADD COLUMN gender gender;

-- Delete the address and email columns and replace it with contact_info (Address, email) as Composite Data type

ALTER TABLE Student 
DROP COLUMN email,
DROP COLUMN address;

CREATE TYPE contact_type AS (
	address VARCHAR(255),
	emial VARCHAR(255)
);

ALTER TABLE Student
ADD COLUMN contact_info contact_type;

-- Display name and age of each student.
SELECT 
	student_name,
	age(now(), birth_date) as age
FROM Student;

-- Display the name of students with the year of b_date.
SELECT 
	student_name,
	age(now(), birth_date) as age
FROM Student;

-- Add new exam, in date column use NOW() function.
INSERT INTO Exam(exam_date)
	VALUES(now())
	
-- Display the number of students’ their name is “Mohammed.

SELECT count(*)
FROM Student
WHERE student_name = 'Mohamed'


```

