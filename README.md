# 📚 Library Management System

## 📌 Overview

This is a SQL-based Library Management System project built with MySQL.
The database manages books, members, employees, branches, book issue
transactions, and book returns.

The project demonstrates practical SQL skills including relational
database design, CRUD operations, joins, aggregate functions, CTAS,
date-based analysis, and stored procedures.

## 🛠️ Technologies Used

-   MySQL
-   MySQL Workbench
-   Visual Studio Code
-   Git and GitHub
-   CSV files

## 🎯 Objectives

-   Design a relational library database
-   Connect tables using Primary Keys and Foreign Keys
-   Import and manage CSV data
-   Perform CRUD operations
-   Generate reports using JOIN, GROUP BY, and aggregate functions
-   Create summary tables using CTAS
-   Track overdue books and calculate fines
-   Create a stored procedure for book availability management

## 🗄️ Database Tables

  Table             Purpose
  ----------------- ------------------------------------------
  `branch`          Stores library branch information
  `employees`       Stores employee details
  `members`         Stores library member details
  `books`           Stores book information and availability
  `issued_status`   Stores book issue transactions
  `return_status`   Stores book return transactions

## 🔗 Table Relationships

``` text
                 BRANCH
                   │
                   ▼
               EMPLOYEES
                   │
                   ▼
MEMBERS ───── ISSUED_STATUS ───── BOOKS
                   │
                   ▼
             RETURN_STATUS
```

Primary Keys uniquely identify records, while Foreign Keys connect
related tables and help maintain data consistency.

## 📁 Project Structure

``` text
Library-Management-System/
README.md
library_management.sql
project_tasks.sql
books.csvbranch.csv
employees.csv
members.csv
issued_status.csv
return_status.csv
solutions.csv
insertquries.csv
    

## ⚙️ Database Setup

``` sql
CREATE DATABASE library_management;
USE library_management;
```

After creating the database:

1.  Create the six tables.
2.  Add Primary Keys and Foreign Key relationships.
3.  Import the CSV files.
4.  Run the queries from the project task file.

# 📝 Project Tasks

## 1. CRUD Operations

### Task 1 --- Add a New Book

``` sql
INSERT INTO books (
    isbn, book_title, category, rental_price, status, author, publisher
)
VALUES (
    '978-1-60129-456-2',
    'To Kill a Mockingbird',
    'Classic',
    6.00,
    'yes',
    'Harper Lee',
    'J.B. Lippincott & Co.'
);
```

### Task 2 --- Update a Member's Address

``` sql
UPDATE members
SET member_address = '125 Oak St'
WHERE member_id = 'C103';
```

### Task 3 --- Delete an Issue Record

``` sql
DELETE FROM issued_status
WHERE issued_id = 'IS104';
```

### Task 4 --- Books Issued by Employee E101

``` sql
SELECT *
FROM issued_status
WHERE issued_emp_id = 'E101';
```

### Task 5 --- Members Who Issued More Than One Book

``` sql
SELECT
    issued_member_id,
    COUNT(issued_id) AS total_books_issued
FROM issued_status
GROUP BY issued_member_id
HAVING COUNT(issued_id) > 1;
```

## 2. CTAS and Data Analysis

### Task 6 --- Create a Book Issue Summary

Creates a table showing each book and its total issue count.

### Task 7 --- Retrieve Books by Category

Retrieves all books from a selected category.

### Task 8 --- Rental Income by Category

Calculates total rental income for each category.

### Task 9 --- Members Registered in the Last 180 Days

Uses date functions to identify recently registered members.

### Task 10 --- Employee, Manager and Branch Details

Uses JOIN and self-JOIN logic to display employee and manager
information.

### Task 11 --- Books Above a Rental Price Threshold

Creates a new table containing higher-priced rental books.

### Task 12 --- Books Not Yet Returned

Identifies issue records without a matching return record.

## 3. Advanced SQL Operations

### Task 13 --- Identify Overdue Books

A book is considered overdue when it has not been returned within 30
days.

### Task 14 --- Update Book Status on Return

Updates the book availability status when a return is recorded.

### Task 15 --- Branch Performance Report

Generates branch-wise data for:

-   Books issued
-   Books returned
-   Rental revenue

### Task 16 --- Create Active Members Table

Uses CTAS to create a table of members who issued at least one book
during the last six months.

### Task 17 --- Top 3 Employees by Issues Processed

Finds the employees who processed the highest number of issue
transactions.

### Task 18 --- Damaged Book Analysis

Identifies members associated with damaged books more than twice.

### Task 19 --- Stored Procedure

Creates a procedure that:

-   Sets book status to `no` when a book is issued
-   Sets book status to `yes` when a book is returned

### Task 20 --- Overdue Books and Fine Calculation

Creates a CTAS table containing:

-   Member ID
-   Number of overdue books
-   Total fines
-   Number of books issued

Fine calculation:

``` text
Fine = Overdue Days × 0.50
```

## 💡 SQL Concepts Used

``` text
CREATE DATABASE
CREATE TABLE
PRIMARY KEY
FOREIGN KEY
INSERT
SELECT
UPDATE
DELETE
WHERE
JOIN
LEFT JOIN
GROUP BY
HAVING
COUNT()
SUM()
COALESCE()
DATEDIFF()
DATE_SUB()
CTAS
CASE
ORDER BY
LIMIT
STORED PROCEDURE
```

## 📈 Learning Outcomes

Through this project, I practiced:

-   Relational database design
-   Primary and Foreign Key relationships
-   CRUD operations
-   Data filtering and aggregation
-   Multi-table JOIN operations
-   Date-based SQL queries
-   CTAS for summary tables
-   Stored procedures
-   Overdue tracking and fine calculation
-   Business-style SQL reporting

## ▶️ How to Run

1.  Clone or download this repository.
2.  Open MySQL Workbench.
3.  Create and select the `library_management` database.
4.  Run the table creation queries.
5.  Import the CSV files.
6.  Execute the SQL tasks.

## 👨‍💻 Author

**Rushikesh Vyas**

Computer Engineering Student

------------------------------------------------------------------------

⭐ If you found this project useful, feel free to explore the SQL
queries and database structure.
