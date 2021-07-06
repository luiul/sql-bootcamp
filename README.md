<!-- omit in toc -->
# SQL Bootcamp

<!-- omit in toc -->
## Description

Databases are systems that allow users to store and organize data and are useful when dealing with large amounts of data. On the other hand, spreadsheets are good for one-time analysis, quickly need to chart something, reasonable data set size, and the ability for untrained people to work with data.

Databases are good for data integrity, they can handle massive amounts of data, quickly combine different datasets, automate steps of re-use, and can support data for websites and applications.

A **database** is a collection of tables. **Tables** contain rows and columns, where the **rows** are known as **records** and the **columns** are known as **fields**. A **column** is a set of data values of a particular type, one value for each row of the database. A **row** represents a single data item in a table, and every row in the table has the same structure.

<!-- omit in toc -->
## Table of Contents
<!-- toc here -->
- [1. Overview](#1-overview)
  - [1.1. Course Curriculum](#11-course-curriculum)
  - [1.2. Challenges](#12-challenges)
- [2. Setup](#2-setup)
- [3. SQL Statement Fundamentals](#3-sql-statement-fundamentals)
  - [3.1. SELECT Statement](#31-select-statement)
  - [3.2. DISTINCT Keyword](#32-distinct-keyword)
  - [3.3. COUNT Function](#33-count-function)
  - [3.4. WHERE Clause](#34-where-clause)
  - [3.5. ORDER BY Clause](#35-order-by-clause)
- [4. Misc](#4-misc)

<!-- update number, TOC -->

# 1. Overview

Overview of the course curriculum and challenges.

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
-- the ; at the end of the query is optional is pgSQL 
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

We retrieve information from tables with queries. We construct queries with statements.

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

## 3.2. DISTINCT Keyword

The `distinct` / `distinct()` **keyword**  can be used to return only the distinct values in a column.

```sql
-- the DISTINCT keyword operates on a column
select distinct c from t1

-- we can add parenthesis for clarity. When adding more calls together, the parenthesis will be necessary
select distinct(c) from t1
```

**Challenge**: retrieve the distinct rating types out films could have in our database.

## 3.3. COUNT Function

The `count()` **function** returns the number of input rows that match a specific condition of a query. We can apply `count()` on a specific column or just pass `count(*)`, this should return the same result. It simply returns the number of rows in the table, regardless of the column we call.

```sql
select count(c1) from t1
-- it's useful to use a column name to contextualize the query (what question were we trying to answer?)
```

`count()` is more useful when combined with other commands, e.g. `distinct()`. We can answer questions like, how many unique names are there in the table?

```sql
select count(distinct(c1)) from t1
-- we're calling count on the result of distinct name 
```

## 3.4. WHERE Clause

`select` and `where` are the most fundamental SQL statements. The `where` statement allows us to **specify conditions** on columns for the rows to be returned. Basic syntax:

```sql
select c1,...,cn from t1 where conditions
```

The `where` clause appears immediately after the `from` clause of the `select` statement. The conditions are used to filter the rows returned from the `select` statement. There are a variety of standard operators to construct the conditions.  

- Comparison operators: compare a column value to something.
- Logical operators: allow us to combine multiple comparison operators.

Example:

```sql
select count(title) from film where rental_rate >= 4 and replacement_cost >= 19.99 and rating = 'R'
-- condition on rental_rate, replacement_cost and rating
-- note that the COUNT function does not need a specific column, as it just counts the number of records expected to be returned by the SELECT statement
```

**Challenge**: from now on we will focus more on directly asking the business related questions, to more realistically model a typical task. Find the email for the customer with the name Nancy Thomas. Solution: 

```sql
-- task: find the email for the customer with the name Nancy Thomas

-- return the columns of the customer table
-- select * from customer where 1=0

select email, first_name, last_name from customer where first_name = 'Nancy' and last_name = 'Thomas'
```

**Challenge**: what is the movie Outlaw Hanky about? Solution: 

```sql
-- select * from film where 1=0
select description from film where title = 'Outlaw Hanky'
```

**Challenge**: get the phone number for the customer who lives at 259 Ipoh Drive. 
```sql
-- select * from address where 1=0
select phone from address where address='259 Ipoh Drive'
```

## 3.5. ORDER BY Clause

We can use `order by` to sort rows based on a column value, in either ascending or descending order. Basic syntax: 

```sql 
select c1, c2 from t1 order by c1 asc / desc
```

Notice `order by` towards the end of a query, since we want to do any selection and filtering first, before finally sorting. 


# 4. Misc

Misc notes:

- Use column names `create_date` (date) and `last_update` (timestamp without timezone).
- A **database** is a collection of tables. **Tables** contain rows and columns, where the rows are known as records and the columns are known as fields. A **column** is a set of data values of a particular type, one value for each row of the database. A **row** represents a single data item in a table, and every row in the table has the same structure.
- [Single vs Double Quotes](https://stackoverflow.com/questions/41396195/what-is-the-difference-between-single-quotes-and-double-quotes-in-postgresql): Double quotes are for names of **tables** or **fields**. Sometimes You can omit them. The single quotes are for **string constants**. This is the SQL standard. In the verbose form, your query looks like this:

```sql
select * from "table1" where "column1"='name1';
```

- SQL COUNT function is the simplest function and very useful in counting the number of records, which are expected to be returned by a SELECT statement.
