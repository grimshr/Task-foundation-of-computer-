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
