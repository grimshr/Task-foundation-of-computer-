# Task 3 -foundation-of-computer science

## General Overview
```
- This repository contains a simple **college club membership** database.
- The database stores **students**, **clubs**, and **membership records** (who joined which club and when).
- The design uses **3 tables** (Student, Club, Membership) to keep data clean and reduce repetition.
- Membership works as a **link table** so the system can support:
  - one student joining many clubs
  - one club having many students
```

## Learning Objectives
```
- Understand why splitting data into tables improves database quality.
- Create tables with:
  - **Primary Key (PK)** to uniquely identify records
  - **Foreign Key (FK)** to link tables correctly
- Build a database that supports a **many-to-many relationship** using a linking table.
- Insert sample data into multiple tables.
- Use `SELECT` queries to view data.
- Use `JOIN` queries to combine tables and show meaningful results.
```
---

## Installation / Run Guide (MySQL)
### Requirements
```
- MySQL installed (or XAMPP/WAMP with MySQL)
- MySQL Workbench or phpMyAdmin (optional)
```
### Steps
```
1. Open MySQL Workbench (or phpMyAdmin / terminal).
2. Create a new SQL file (example: `schema.sql`) and paste your queries.
3. Run the script in this order:
   - Create database
   - Use database
   - Create tables
   - Insert data
   - Run select + join queries
```
```
-- Create and use database
CREATE DATABASE assignment_sahil_db;
USE assignment_sahil_db;

-- Create Student table
CREATE TABLE Student (
  Studentid INT AUTO_INCREMENT PRIMARY KEY,
  Studentname VARCHAR(100) NOT NULL,
  Email VARCHAR(100) NOT NULL
);

-- Insert Students
INSERT INTO Student (Studentid, Studentname, Email) VALUES
(1, 'Asha', 'asha@email.com'),
(2, 'Bikash', 'bikash@email.com'),
(3, 'Nisha', 'nisha@email.com'),
(4, 'Rohan', 'rohan@email.com'),
(5, 'Suman', 'suman@email.com'),
(6, 'Pooja', 'pooja@email.com'),
(7, 'Aman', 'aman@email.com');

-- Create Club table
CREATE TABLE Club (
  Clubname VARCHAR(100) NOT NULL PRIMARY KEY,
  Clubroom VARCHAR(100) NOT NULL,
  Clubmentor VARCHAR(100) NOT NULL
);

-- Insert Clubs
INSERT INTO Club (Clubname, Clubroom, Clubmentor) VALUES
('Music Club', 'R101', 'Mr. Raman'),
('Sports Club', 'R202', 'Ms. Sita'),
('Drama Club', 'R303', 'Mr. Kiran'),
('Coding Club', 'Lab1', 'Mr. Anil');

-- Create Membership table (link table)
CREATE TABLE Membership (
  Studentid INT NOT NULL,
  Clubname VARCHAR(100) NOT NULL,
  Joindate VARCHAR(100) NOT NULL,
  FOREIGN KEY (Studentid) REFERENCES Student(Studentid),
  FOREIGN KEY (Clubname) REFERENCES Club(Clubname)
);

-- Insert Membership Records
INSERT INTO Membership (Studentid, Clubname, Joindate) VALUES
(1, 'Music Club', '1/10/2024'),
(1, 'Sports Club', '1/15/2024'),
(2, 'Sports Club', '1/12/2024'),
(2, 'Drama Club', '1/25/2024'),
(3, 'Music Club', '1/20/2024'),
(3, 'Coding Club', '1/28/2024'),
(4, 'Drama Club', '1/18/2024'),
(5, 'Music Club', '1/22/2024'),
(6, 'Sports Club', '1/27/2024'),
(7, 'Coding Club', '1/30/2024');

-- Extra Inserts
INSERT INTO Student (Studentid, Studentname, Email) VALUES
(9, 'Leon Kennedy', 'leon@email.com');

INSERT INTO Club (Clubname, Clubroom, Clubmentor) VALUES
('ESport Club', 'R405', 'Mr. Honk');

-- Display Queries
SELECT Studentname FROM Student;
SELECT Clubname FROM Club;
SELECT Joindate FROM Membership;

-- JOIN Query (Student + Club + JoinDate)
SELECT 
  Student.Studentid,
  Student.Studentname,
  Club.Clubname,
  Membership.Joindate
FROM Membership
JOIN Student ON Membership.Studentid = Student.Studentid
JOIN Club ON Membership.Clubname = Club.Clubname;
```
## ER diagram 
```
+-------------------+         +-------------------+
|      Student      |         |       Club        |
+-------------------+         +-------------------+
| PK Studentid      |         | PK Clubname       |
|    Studentname    |         |    Clubroom       |
|    Email          |         |    Clubmentor     |
+-------------------+         +-------------------+
          | 1                         | 1
          |                           |
          |                           |
          | M                         | M
      +---------------------------------------+
      |               Membership              |
      +---------------------------------------+
      | FK Studentid  -> Student.Studentid    |
      | FK Clubname   -> Club.Clubname        |
      |    Joindate                           |
      +---------------------------------------+

Relationship meaning

One Student can have many Membership records.
One Club can have many Membership records.
So overall: Student ↔ Club is many-to-many using Membership.
```
