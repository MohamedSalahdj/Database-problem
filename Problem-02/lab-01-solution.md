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
```

