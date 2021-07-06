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
  - [3.6. LIMIT Clause](#36-limit-clause)
  - [3.7. BETWEEN Operator](#37-between-operator)
  - [3.8. IN Operator](#38-in-operator)
  - [3.9. LIKE and ILIKE Operators & Pattern Matching](#39-like-and-ilike-operators--pattern-matching)
- [4. General Challenge 1](#4-general-challenge-1)
- [5. GROUP BY Statements](#5-group-by-statements)
- [6. Misc](#6-misc)

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
select c1,...,cn from t1
where conditions
```

The `where` clause appears immediately after the `from` clause of the `select` statement. The conditions are used to filter the rows returned from the `select` statement. There are a variety of standard operators to construct the conditions.  

- Comparison operators: compare a column value to something.
- Logical operators: allow us to combine multiple comparison operators.

Example:

```sql
select count(title) from film
where rental_rate >= 4 and replacement_cost >= 19.99 and rating = 'R'
-- condition on rental_rate, replacement_cost and rating
-- note that the COUNT function does not need a specific column, as it just counts the number of records expected to be returned by the SELECT statement
```

**Challenge**: from now on we will focus more on directly asking the business related questions, to more realistically model a typical task. Find the email for the customer with the name Nancy Thomas. Solution:

```sql
-- task: find the email for the customer with the name Nancy Thomas

-- return the columns of the customer table
-- select * from customer where 1=0

select email, first_name, last_name from customer 
where first_name = 'Nancy' and last_name = 'Thomas'
```

**Challenge**: what is the movie Outlaw Hanky about? Solution:

```sql
-- select * from film where 1=0
select description from film 
where title = 'Outlaw Hanky'
```

**Challenge**: get the phone number for the customer who lives at 259 Ipoh Drive.

```sql
-- select * from address where 1=0
select phone from "address" 
where address='259 Ipoh Drive'
```

## 3.5. ORDER BY Clause

We can use `order by` to sort rows based on a column value, in either ascending or descending order. Basic syntax:

```sql
select c1, c2 from t1 
order by c1 asc / desc c2 asc / desc
-- ORDER BY uses ASC by default
```

Notice `order by` towards the end of a query, since we want to do any selection and filtering first, before finally sorting. We can use `order by` in multiple columns (this makes sense when one column has duplicate entries), e.g.

```sql
select company, employee, sales from sales 
order by company asc , sales desc
-- we first sort rows based on the company and then we sort rows by sales (the second sorting does not affect the first one). Here we query the companies by ascending name and order the sales by descending amounts
```

## 3.6. LIMIT Clause

`limit` allows us to limit the number of rows returned for a query. Useful for not wanting to return every singlerow in a table, but only view the top few rows to get an idea of the table layout. ´limit´ becomes useful in combination with `order by`.

`limit` goes at the very end of a query request and is the last command to be executed. Basic syntax:

```sql
select c1 from t1 
order by c1 desc limit 10
-- get the top 10 values in c1
```

For example:

```sql
select * from payment 
where amount != 0 
order by payment_date desc 
limit 5
-- history of the 5 most recent payments where the amount is not zero
```

**Challenge**: we want to reward out first 10 paying customers. What are the customer ids of the first 10 customers who created a payment.

```sql
-- return columns names / layout of the table
-- select * from payment limit 1 

select distinct(customer_id), payment_date from payment
-- where 
order by payment_date asc 
limit 10
-- assumption: we want to reward 10 different paying cusotmers
```

**Challenge**: a customer wants to quickly rent a video to watch over their short lunch break. What are the titles of the 5 shortest (in length of runtime) movies?

```sql
-- see layout of the table film
-- select * from film limit 1

select title, "length" from film
-- where 
order by "length" asc
limit 5
```

**Challenge**: if a customer can watch a movie that is 50 minutes or less in run time, how many options does the customer have?

```sql
select count(title) from film
where "length" <= 50
```

## 3.7. BETWEEN Operator

The `between` operator can be used to match a value against a range of values:

```sql
select c1 from t1
where c1 between m and M
-- this is the same as WHERE c1 >= m  and c1 <= M
-- between includes the bounds
-- the set that contains the results is not disjunct 
```

We can also use the negation `not`:

```sql
select c1 from t1
where c1 not between m and M
-- this is the same as WHERE c1 < m OR c1 > M
-- not between does not include the bounds
-- the set that contains the results is disjunct
```

The `between` operator can also be used with dates. Note that we need to format dates in the ISO 8601 standard format YY-MM-DD.

When using `between` operator with dates that also include **timestamp** information, pay careful attention to using `between` versus comparison operators, due to the fact that a datetime starts at 00:00:00 (and ends at 23:59:59). Later we will study more specific methods for datetime information types.

```sql
select c1 from t1
where c1 between 'YY-MM-DD hh:mm:ss.sss' and 'YY-MM-DD hh:mm:ss.sss'
-- if not specified hh:mm:ss.sss is set to 00:00:00.000, which affects the logic of the upper bound! 
```

## 3.8. IN Operator

In certain cases you want to check for multiple possible value options, e.g. if a user's name shows up `in` a list of know names. We can use the `in` operator to create a condition that checks to see if a value included in a list of multiple options. Basic syntax:

```sql
select c1 from t1
where c1 in (opt1,...,optn)
-- this is the same as WHERE c1 = opt1 OR ... OR c1 = optn
-- the options should match the general syntax of the column
```

We can also use the negation `not`:

```sql
select c1 from t1
where c1 not in (opt1,...,optn)
-- this is the same as WHERE c1 != opt1 AND ... AND c1 != optn
```

## 3.9. LIKE and ILIKE Operators & Pattern Matching

We've already been able to perform direct comparisons against strings. But what we want to match against a
general pattern in a string? Example:

- All emails ending in '@gmail.com'
- All names that begin with an 'A'

The `like` operator (case-sensitive) allows us to perform pattern matching against string data with the use of wildcard characters:

- Percent `%`: matches **any** sequence of characters (can be blank too).
- Underscore `_`: matches any **single** character

```sql
select c1 from t1
where c1 like 'A%'
-- all names in c1 that begin with an 'A'
```

The operator `ilike` is case-insensitive. PgSQL also supports full regex capabilities (see [docs](https://www.postgresql.org/docs/13/functions-matching.html)). Example:

```sql
select * from customer
where first_name ilike 'j%' and last_name ilike 's%'
-- look for customers with a first name that starts with 'j' and a last name that starts with 's' (case-insensitive)
```

`%` can be black too, `_`cannot be blank. Example:

```sql
select * from customer
where first_name ilike 'heather%'
-- does return rows with the first name 'Heather'
```

```sql
select * from customer
where first_name ilike 'heather_'
-- does not return row with the first name 'Heather'
```

We can combine operations and clauses to create more complex queries.

```sql
select * from customer
where first_name like 'A%' and last_name not like 'B%'
order by first_name
-- return all customers whose name start with an 'A' and last name does not start with a 'B'. Order the results ascending by the first name. 
```

# 4. General Challenge 1

How many payment transaction were greater than $5.00?

```sql
select count(amount) from payment
where amount > 5
```

How many actors have a first name that starts with the letter P?

```sql
select count(first_name) from actor
where first_name ilike 'p%'
```

How many unique districts are our customers from?

```sql
select count(distinct(district)) from address
-- where
```

Retrieve the list of names for those distinct districts from the previous question.

```sql
select distinct(district) from address
-- where
```

How many films have a rating of R and a replacement cost between $5 and $15? ([*](https://xzilla.net/blog/2007/Sep/PostgreSQL-8.3-Features-Enum-Datatype.html))

```sql
select count(title) from film
where rating = 'R' and replacement_cost between 5 and 15
-- note that rating is mpaa_rating data type 
```

How many films have the word Truman somewhere in the title?

```sql
select count(title) from film
where title ilike '%truman%'
```

# 5. GROUP BY Statements

Continue here!

# 6. Misc

Misc notes:

- [SQL Cheat Sheet](https://www.sqltutorial.org/wp-content/uploads/2016/04/SQL-cheat-sheet.pdf):
  - `limit` n `offset` m: skip m row and return the next n rows.
- Use column names `create_date` (date) and `last_update` (timestamp without timezone).
- A **database** is a collection of tables. **Tables** contain rows and columns, where the rows are known as records and the columns are known as fields. A **column** is a set of data values of a particular type, one value for each row of the database. A **row** represents a single data item in a table, and every row in the table has the same structure.
- [Single vs Double Quotes](https://stackoverflow.com/questions/41396195/what-is-the-difference-between-single-quotes-and-double-quotes-in-postgresql): **Double quotes** are for names of **tables** or **fields**. Sometimes You can omit them. The **single quotes** are for **string constants**. This is the SQL standard. In the verbose form, your query looks like this:

```sql
select * from "table1" where "column1"='name1';
```

- SQL `COUNT` function is the simplest function and very useful in counting the number of records, which are expected to be returned by a SELECT statement.
- [SQL SELECT with DISTINCT on multiple columns](https://www.w3resource.com/sql/select-statement/queries-with-distinct-multiple-columns.php)
- Additional PgSQL keywords and functions:
  - length()
  - offset
- [PgSQL Pattern Matching](https://www.postgresql.org/docs/13/functions-matching.html): Be wary of accepting regular-expression search patterns from hostile sources. If you must do so, it is advisable to impose a statement timeout.  
Searches using `SIMILAR TO` patterns have the same security hazards, since `SIMILAR TO` provides many of the same capabilities as POSIX-style regular expressions.  
`LIKE` searches, being much simpler than the other two options, are safer to use with possibly-hostile pattern sources.
