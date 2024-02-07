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

