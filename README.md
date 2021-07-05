<!-- omit in toc -->
# SQL Bootcamp

<!-- omit in toc -->
## Description

Databases are systems that allow users to store and organize data and are useful when dealing with large amounts of data.

Spreadsheets are good for one-time analysis, quickly need to chart something, reasonable data set size, and the ability for untrained people to work with data.

Databases are good for data integrity, they can handle massive amounts of data, quickly combine different datasets, automate steps of re-use, and can support data for websites and applications.

<!-- omit in toc -->
## Table of Contents
<!-- toc here -->
- [1. Overview](#1-overview)
  - [1.1. Course Curriculum](#11-course-curriculum)
  - [1.2. Challenges](#12-challenges)
- [2. Setup](#2-setup)
- [3. SQL Statement Fundamentals](#3-sql-statement-fundamentals)
  - [3.1. SELECT Statement](#31-select-statement)

# 1. Overview

## 1.1. Course Curriculum

<details>
<summary>The course is divided in the following sections...</summary>
- Section 1
  - Databses and Table Basics
  - SQL Statement Fundamentals
  - GROUP BY Clause
  - Assessment Test 1
- Section 2
  - JOINS
  - Advanced SQL
  - Commands
  - Assessment Test 2
- Section 3
  - Create Database and Tables
  - Assessment Test 3
  - Views
  - PostgreSQL with Python
</details>

<details>
<summary>Typical database users...</summary>

- Analyst
  - Marketing
  - Business
  - Sales
- Technical
  - Data Scientist
  - Software Engineers
  - Web Developers

</details>

<details>
<summary>Database Platform Options:</summary>

- PostgreSQL (focus of the course)
  - Free (Open Source)
  - Widely used on internet
  - Multi platform
- MySQL & MariaSQL
  - Free (Open Source)
  - Widely used on internet
  - Multi platform
- MS SQL Server Express
  - Free, but with some limitations
  - Compatible with SQL Server
  - Windows only (-)
- Microsoft Access
  - Cost (-)
  - Not easy to use just SQL (-)
- SQLite
  - Free (Open Source)
  - Mainly command line (-)

</details>

SQL is the programming language used to communicate with our database. Example:

```sql
select customer_id, first_name, last_name
from sales
order by first_name;
```

## 1.2. Challenges

Challenges are based on the scenario that we've just been hired as a SQL consultant for a DVD Rental Store. Challenges increase in difficult over the course.

<details>
<summary>Challenge structure...</summary>

- Business Situation
- Challenge Question
- Expected Answer
- Hints
- Solution

</details>

# 2. Setup

We install and use the following applications. 

- [PostgreSQL](https://www.postgresql.org/): SQL Engine that stores data and reads queries and returns information
- [PgAdmin](https://www.pgadmin.org/): graphical User Interface for connecting with PostgreSQL
- Restore the provided database with the `.tar` file.
- VS Code: source-code editor. We use VS Code as a scratch pad and for general note taking.

Go to Servers > PostgreSQL 12 > Databases > dvdrental > Schemas > Tables to see the tables in the restored database.

# 3. SQL Statement Fundamentals

## 3.1. SELECT Statement

The syntax we learn can be applied to any major type of SQL database. `select` is the most common statement used, and it allows us to retrieve information from a table. Later on we will learn how to combine `select` with other statements to perform more complex queries.

```sql
-- select columns c1,...,cn from table t1
select c1,...,cn from t1

-- select all columns from table t1, i.e. select the whole table
select * from t1
-- note that it is bad practice to use * if we don't need all columns (increased traffic between database server and app -> slows down retrieval of results)
```

**Challenge**: we want to send out a promotional email to our existing customers. Grab the first and last names of every customer and their email address.

The `distinct` / `distinct()` keyword  can be used to return only the distinct values in a column.

```sql
-- the DISTINCT keyword operates on a column
select distinct c from t1

-- we can add parenthesis for clarity. When adding more calls together, the parenthesis will be necessary
select distinct(c) from t1
```

**Challenge**: retrieve the distinct rating types out films could have in our database. 

The `count()` function returns the number of input rows that match a specific condition of a query. We can apply `count()` on a specific column or just pass `count(*)`, this should return the same result. It simply returns the number of rows in the table, regardless of the column we call. 

```sql
select count(c1) from t1
-- it's useful to use a column name to contextualize the query (what question were we trying to answer?)
```

`count()` is more useful when combined with other commands, e.g. `distinct()`. We can answer questions like, how many unique names are there in the table? 

```sql
select count(distinct(c1)) from t1
-- we're calling count on the result of distinct name 
```

`select` and `where` are the most fundamental SQL statements. The `where` statement allows us to *specify conditions* on columns for the rows to be returned. 