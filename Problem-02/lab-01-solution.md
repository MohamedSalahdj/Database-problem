# 	Lab-01 - Answers 

### Create Database

```postgresql
CREATE DATABASE labone;
```

### Create your tables in 'db.txt' with their columns in PostgreSQL.

```postgresql
CREATE TABLE Student (
	id SERIAL PRIMARY KEY,
	student_name VARCHAR(255) NOT NULL,
	email VARCHAR(255) NOT NULL,
	address VARCHAR(255),
	phone VARCHAR(255) NOT NULL,
	track_id int
)
CREATE TABLE Track(
	id SERIAL PRIMARY KEY,
	track_name VARCHAR(255) NOT NULL
)

-- After create Track table 
ALTER TABLE Student 
ADD CONSTRAINT student_track_fk
FOREIGN KEY (track_id)
REFERENCES Track(id);

CREATE TABLE Track(
	id SERIAL PRIMARY KEY,
	track_name VARCHAR(255) NOT NULL
)

CREATE TABLE Subject (
	id SERIAL PRIMARY KEY,
	subject_name VARCHAR(255) NOT NULL,
	max_score SMALLINT
)

CREATE TABLE Exam (
	id SERIAL PRIMARY KEY,
	exam_date DATE NOT NULL
)

CREATE TABLE Grades (
	student_id INTEGER NOT NULL,
	subject_id INTEGER NOT NULL,
	exam_id INTEGER NOT NULL,
	grade SMALLINT NOT NULL, 
	
	CONSTRAINT grade_student_fk 
	FOREIGN KEY (student_id)
	REFERENCES Student(id),
	
	CONSTRAINT grade_subject_fk
	FOREIGN KEY (subject_id)
	REFERENCES Subject(id),
	
	CONSTRAINT grade_exam_fk
	FOREIGN KEY (exam_id)
	REFERENCES Exam(id),
	
	CONSTRAINT "grade_pk" PRIMARY KEY (student_id, subject_id)
	
)

CREATE TABLE student_subject (
	student_id INTEGER NOT NULL,
	subject_id INTEGER NOT NULL,
	
	CONSTRAINT "student_stu_sub_fk"
	FOREIGN KEY (student_id)
	REFERENCES Student(id),
	
	CONSTRAINT "subject_stu_sub_fk"
	FOREIGN KEY (subject_id)
	REFERENCES Subject (id),
	
	CONSTRAINT "studnt_subject_pk" PRIMARY KEY (student_id, subject_id)

)

CREATE TABLE Track_Subject(
	track_id INTEGER,
	subject_id INTEGER,
	
	CONSTRAINT "track_track_subject_fk"
	FOREIGN KEY (track_id)
	REFERENCES Track (id),
	
	CONSTRAINT "subject_track_subject_fk"
	FOREIGN KEY (subject_id)
	REFERENCES Subject (id),
	
	CONSTRAINT "track_subject_pk" PRIMARY KEY (track_id, subject_id)
	
);

```

```postgresql
// Insert into every tables 

INSERT INTO Track(track_name)
	VALUES 
		('FULL STACK using Python'),
		('FULL STACK using PHP'),
		('Cyber security'),
		('Embeded System');
		
INSERT INTO Student(student_name, email, phone, track_id)
	VALUES
			('Mohamed Samy', 'mohamed@gmail.com','12345648',1),
			('Mohamed Salah', 'mohamedsalah@gmail.com','987455648',3),
			('Ziad', 'ziad@gmail.com','0111111111',4),
			('Ali', 'ali@gmail.com','01222222',1);
			
INSERT INTO Subject (subject_name, max_score)
	VALUES 
		('OOP', 100),
		('JS', 100),
		('Stucture Programming', 100),
		('Data Structure', 100);
		
INSERT INTO Exam(exam_date)
	VALUES 
		('2023-01-10'),
		('2023-01-15'),
		('2023-01-20'),
		('2023-01-25');
		
INSERT INTO Grades(student_id, subject_id, exam_id, grade)
	VALUES
		(1, 1, 1, 90),
		(2, 3, 3, 80),
		(3, 3, 2, 99),
		(4, 2, 4, 70);
        
INSERT INTO student_subject(student_id, subject_id)
	VALUES 
		(1,2),
		(2,1),
		(3,4),
		(4,2);
		
INSERT INTO Track_Subject(track_id, subject_id)
	 VALUES 
         (1, 1),
         (1, 2),
         (4, 3),
         (4, 4);
```

