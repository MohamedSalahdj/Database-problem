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
```

