<!-- omit in toc -->
# SQL Bootcamp 2021 & Advanced Queries

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
- [5. GROUP BY Statements & Aggregate Functions](#5-group-by-statements--aggregate-functions)
  - [5.1. Aggregation Functions - AVG, COUNT, MAX, MIN and SUM](#51-aggregation-functions---avg-count-max-min-and-sum)
  - [5.2. GROUP BY Statement](#52-group-by-statement)
  - [5.3. HAVING Clause](#53-having-clause)
- [6. Assessment Test 1](#6-assessment-test-1)
- [7. JOIN Clause](#7-join-clause)
  - [7.1. Aliases: AS Clause](#71-aliases-as-clause)
  - [7.2. (INNER) JOIN Keyword (Intersection)](#72-inner-join-keyword-intersection)
  - [7.3. FULL (OUTER) JOIN Keyword (Union and Symmetric Difference)](#73-full-outer-join-keyword-union-and-symmetric-difference)
  - [7.4. LEFT (OUTER) JOIN Keyword (A)](#74-left-outer-join-keyword-a)
  - [7.5. RIGHT (OUTER) JOIN Keyword (B)](#75-right-outer-join-keyword-b)
  - [7.6. UNION Operator](#76-union-operator)
  - [7.7. JOIN Challenges](#77-join-challenges)
- [8. Advanced SQL Commands](#8-advanced-sql-commands)
  - [8.1. Timestamps and Extract](#81-timestamps-and-extract)
    - [8.1.1. Displaying Current Time Information](#811-displaying-current-time-information)
    - [8.1.2. Extracting Time and Date Information](#812-extracting-time-and-date-information)
  - [8.2. Mathematical Functions and Operators](#82-mathematical-functions-and-operators)
  - [8.3. String Functions and Operators](#83-string-functions-and-operators)
  - [8.4. Subquery](#84-subquery)
  - [8.5. Self-Join](#85-self-join)
- [9. Assessment Test 2](#9-assessment-test-2)
- [10. Creating Databases and Tables](#10-creating-databases-and-tables)
  - [10.1. Data Types](#101-data-types)
  - [10.2. Primary and Foreign Key](#102-primary-and-foreign-key)
  - [10.3. Constraints](#103-constraints)
  - [10.4. CREATE TABLE Statement (TABLE)](#104-create-table-statement-table)
  - [10.5. INSERT INTO Statement (RECORD)](#105-insert-into-statement-record)
  - [10.6. UPDATE Statement (RECORD)](#106-update-statement-record)
  - [10.7. DELETE Statement (RECORD)](#107-delete-statement-record)
  - [10.8. ALTER TABLE Statement (TABLE AND COLUMN)](#108-alter-table-statement-table-and-column)
    - [10.8.1. RENAME, ADD, DROP, SET Statements (TABLE AND COLUMN)](#1081-rename-add-drop-set-statements-table-and-column)
    - [10.8.2. DROP Statement (COLUMN)](#1082-drop-statement-column)
  - [10.9. CHECK Constraint](#109-check-constraint)
- [11. Assessment Test 3](#11-assessment-test-3)
- [12. Conditional Expressions and Procedures](#12-conditional-expressions-and-procedures)
  - [12.1. CASE ... END Statement](#121-case--end-statement)
  - [12.2. COALESCE() Function](#122-coalesce-function)
  - [12.3. CAST() Function](#123-cast-function)
  - [12.4. NULLIF() Function](#124-nullif-function)
  - [12.5. (CREATE) VIEW Statement](#125-create-view-statement)
- [13. Import and Export](#13-import-and-export)
- [14. PgSQL with Python](#14-pgsql-with-python)
- [15. SQL Window Function Part 1](#15-sql-window-function-part-1)
  - [15.1. Fundamentals, the Over Clause and Partition By](#151-fundamentals-the-over-clause-and-partition-by)
  - [15.2. Other examples and Row Number and Order By (inside Over Clause)](#152-other-examples-and-row-number-and-order-by-inside-over-clause)
  - [15.3. Window Functions: Rank, Dense Rank](#153-window-functions-rank-dense-rank)
  - [15.4. Window Functions: Lead and Lag](#154-window-functions-lead-and-lag)
- [16. SQL Window Function Part 2](#16-sql-window-function-part-2)
  - [16.1. First and Last Value](#161-first-and-last-value)
  - [16.2. Frame Clause](#162-frame-clause)
  - [16.3. Windows Clause](#163-windows-clause)
  - [16.4. N-th Value](#164-n-th-value)
  - [16.5. Ntile](#165-ntile)
  - [16.6. Cumulative Distribution Cume_Dist](#166-cumulative-distribution-cume_dist)
  - [16.7. Percent Rank](#167-percent-rank)
- [17. SQL With Clause and CTE (Common Table Expression) or Sub-Query Factoring](#17-sql-with-clause-and-cte-common-table-expression-or-sub-query-factoring)
- [18. Practice Complex SQL Queries](#18-practice-complex-sql-queries)
  - [18.1. Exercise 1](#181-exercise-1)
  - [18.2. Exercise 2](#182-exercise-2)
  - [18.3. Exercise 3](#183-exercise-3)
  - [18.4. Exercise 4](#184-exercise-4)
  - [18.5. Exercise 5](#185-exercise-5)
  - [18.6. Exercise 6](#186-exercise-6)
  - [18.7. Exercise 7](#187-exercise-7)
  - [18.8. Exercise 9](#188-exercise-9)
- [19. Misc Notes](#19-misc-notes)
  - [19.1. General Syntax](#191-general-syntax)
  - [19.2. Misc Notes from Revision](#192-misc-notes-from-revision)
- [20. Solutions to Codility Exercise](#20-solutions-to-codility-exercise)

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

The `select` statement is used to select data from a database. The data returned is stored in a result table, called the result-set.

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

The `where` clause is used to filter records. It is used to extract only those records that fulfill a specified condition.

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

`%` can be blank too, `_`cannot be blank. Example:

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
select count(distinct(actor_id))
from actor
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

# 5. GROUP BY Statements & Aggregate Functions

`group by` will allow us to aggregate data and apply functions to better understand how data is distributed per category.

Overview:

- Aggregate Functions
- GROUP BY Statement
  - Theory
  - Implementation
- Challenge Tasks for GROUP BY
- HAVING - Filtering with a GROUP BY
- Challenge Tasks for HAVING

## 5.1. Aggregation Functions - AVG, COUNT, MAX, MIN and SUM

The main idea behind an aggregate function is to take multiple inputs and return a single output (stat). PgSQL aggregate functions can be found in the [documentation](https://www.postgresql.org/docs/13/functions-aggregate.html).

Most common aggregate functions:

- `avg()` returns average value
- `count()` returns number of values
- `max()` returns maximum value
- `min()` returns minimum value
- `sum()` returns the sum of all values

Aggregate function calls happen only in the `select` statement or `having` clause!

Special notes:

- `avg()` returns a floating point value with many decimal places (e.g. 2.342418..)
  - You can use `round()` to specify precision after the decimal
- `count()` simply returns the number of rows, which means by convention we just use `count(*)`

Calling an aggregate function returns a single value, which cannot be returned with another column. In order to call other columns we need the `group by` statement. It is possible to return multiple single values in one query. For example:

```sql
select min(replacement_cost), max(replacement_cost) from film
```

We can calculate the average cost:

```sql
select round(avg(replacement_cost),2) from film
```

Additionally, we can determine statistics in ordered sets with ordered-set aggregate functions using the keyword `within group`.

```sql
select
    min(replacement_cost),
    percentile_disc(0.25) within group(
        order by
            replacement_cost
    ) as "25p",
    percentile_disc(0.5) within group(
        order by
            replacement_cost
    ) as median,
    round(avg(replacement_cost), 2) as avg,
    percentile_disc(0.75) within group(
        order by
            replacement_cost
    ) as "75p",
    max(replacement_cost),
    mode() within group(
        order by
            replacement_cost
    )
from film
```


## 5.2. GROUP BY Statement

The `group by` statement allows us to aggregate columns per some category. We need to choose a categorical column to `group by`. Categorical columns are non-continuous. Keep in mind, they can still be numerical, such as cabin class categories on a ship (e.g. Class 1, Class 2, Class 3)

After choosing the categorical column we're essentially **splitting** the table up on a per category basis in n subtables. We can then **aggregate** the columns in the subtables with an aggregate function. Basic syntax:

```sql
select cat_col, add_function(data_col)
from table_
where condition_on_cat_col
group by cat_col
-- the GROUP BY statement must appear right after the FROM or WHERE statement
```

Note that the `group by` statement must appear right after the `from` or `where` statement.

In the `select` statement, columns must either have an aggregate function OR be in a `group by` call. Example:

```sql
select company, division, sum(sales)
-- sales won't appear in GROUP BY so we need an aggregate function to select it
from finance_table
group by company, division
-- this return the total number of sales per division per company
```

Another example from our database:

```sql
select
    rental_duration,
    rating,
    round(avg(replacement_cost), 2) as avg_replacement_cost,
    percentile_disc(0.5) within group(
        order by
            replacement_cost
    ) as median_replacement_cost
from
    film
group by
    rental_duration,
    rating
order by
    rental_duration,
    rating 
-- return the average and median replacement cost per rental duration per rating
```


We can also add a `where` statement to the query. `where` statements should not refer to the aggregation result. Later on we'll use the `having` clause to filter on those results. The `having` clause was added to SQL because the `where` keyword cannot be used with aggregate functions. Example:

```sql
select company, division, sum(sales)
from finance_table
where division in ('marketing', 'transport')
-- where cannot be used with aggregate function
group by company, division
```

Another example from our database:

```sql
select rating, round(avg(replacement_cost),2), percentile_disc(0.5) within group(order by replacement_cost)
from film
where rating in ('R','NC-17')
group by rating
order by rating
-- returns average and median replacement cost for the ratings R and NC-17
```

An example using `where` and `having`: 

```sql 
select
    rental_duration,
    rating,
    round(avg(replacement_cost), 2) as avg_replacement_cost,
    percentile_disc(0.5) within group(
        order by
            replacement_cost
    ) as median_replacement_cost
from
    film
where 
	rating in ('R','NC-17')
group by
    rental_duration,
    rating
having 
	round(avg(replacement_cost), 2) > 19
order by
    rental_duration,
    rating
-- returns the average and median replacement cost per rental duration per rating where the rating is R or NC-17 and the average replacement cost is greater than 19
```


If we want to sort results based on the aggregate, we must reference the entire function. Example:

```sql
select company, sum(sales)
from finance_table
group by company
order by sum(sales) desc
limit 5
-- returns top 5 companies based on total sales
```

Examples:

```sql
select customer_id from payment
group by customer_id

-- the result is the same as SELECT distinct(customer_id) FROM payment
```

We want to find out the top 5 customers that spent the most money:

```sql
select customer_id, sum(amount)
from payment
-- where
group by customer_id
order by sum(amount) desc
limit 5
```

Alternative: 

```sql
with top_customer as (
    select
        customer_id,
        sum(amount) as s_amount
    from
        payment -- where 
    group by
        customer_id -- having
    order by
        sum(amount) desc
    limit
        5
)
select
    t.customer_id,
    first_name,
    last_name,
    s_amount
from
    top_customer as t
    join customer as c on t.customer_id = c.customer_id
```

We want to find out how many transaction occurred per customer:

```sql
select customer_id, count(amount) from payment
group by customer_id
order by count(amount) desc
```

Alternative

```sql 
with tx_count as (
    select
        customer_id,
        count(payment_id) as tx_count
    from
        payment
    group by
        customer_id
)
select
    t.customer_id,
    first_name,
    last_name,
    tx_count
from
    tx_count as t
    join customer as c on t.customer_id = c.customer_id
order by
    tx_count desc
limit
    5
```

We want to find out the sum amount per customer per staff member:

```sql
select staff_id, customer_id, sum(amount) from payment
group by staff_id, customer_id
order by staff_id, customer_id
```

We want to find out the date with the most sum amount:

```sql
select date(payment_date), sum(amount) from payment
group by date(payment_date)
order by sum(amount) desc
-- note that the payment_date is a timestamp -> we remove the time with the date() function
```

Another example; find out the date with the most sum amount after April 29, 2007:

```sql
select date(payment_date), sum(amount)
from payment
where date(payment_date) > '2007-04-29'
group by date(payment_date)
order by sum(amount) desc
-- limit 5
```

**Challenge**: We have two staff members, with Staff IDs 1 and 2. We want to give a bonus to the staff member that handled the most payments. (Most in terms of number of payments processed, not total dollar amount). How many payments did each staff member handle and who gets the bonus?

```sql
select staff_id, count(payment_id) from payment
group by staff_id
```

Alternative solution:

```sql
select staff_id, count(distinct(payment_id))
from payment
where staff_id in (1,2)
group by staff_id
order by count(distinct(payment_id)) desc
-- limit 5
```

**Challenge**: Corporate HQ is conducting a study on the relationship between replacement cost and a movie MPAA rating. What is the average replacement cost per MPAA rating?

```sql
select rating, round(avg(replacement_cost),2)
from film
group by rating
order by avg(replacement_cost) desc
```

**Challenge**: We are running a promotion to reward our top 5 customers with coupons. What are the customer ids of the top 5 customers by total spend?

```sql
select customer_id, round(sum(amount),2)
from payment
group by customer_id
order by sum(amount) desc
limit 5
```

Alternative: 

```sql
with c_sum as (
    select
        customer_id,
        sum(amount)
    from
        payment
    group by
        customer_id
    limit
        5
)
select
    c.customer_id,
    first_name,
    last_name,
    sum
from
    c_sum as c
    join customer as u on c.customer_id = u.customer_id
order by
    sum desc
```

## 5.3. HAVING Clause

The `having` clause allows us to filter after an aggregation has already taken place. Example:

```sql
select company, sum(sales)
from finance_table
where company != 'Google'
group by company
having sum(sales) > 1000
```

Here we're aggregating sales per company. We can filter before executing the `group by` statement, since it's not being aggregated. We can not use `where` to filter based off of aggregate results, because the pgSQL aggregates after the `where` clause is executed. An additional filtering using aggregated results can be done with the `having` clause. Example:

```sql
select customer_id, sum(amount)
from payment
-- we remove some arbitrary customers by id
where customer_id not in (184,87,477)
group by customer_id
having sum(amount) > 150
order by sum(amount) desc
-- the restul is the records of the customer_id and sum amount, excluding some customers and where (having clause) the aggregated sum amount is bigger than 150, ordered by the descending sum amount
```

Example:

```sql
-- number of customer per store
select store_id, count(customer_id)
from customer
group by store_id
```

We can expand on this example. We want to see the number of customer per store in stores that have more than 300 customers.

```sql
-- number of customer per store with more than 300 customers
select store_id, count(customer_id)
from customer
group by store_id
having count(customer_id) >= 300
```

**Challenge**: We are launching a platinum service for our most loyal customers. We will assign platinum status to customers that have had 40 or more transaction payments. What customer_ids are eligible for platinum status?

```sql
select customer_id, count(*)
from payment
group by customer_id
having count(*) >= 40
```

**Challenge**: What are the customer ids of customers who have spent more than $100 in payment transactions with our staff_id member 2?

```sql
select
    customer_id,
    sum(amount)
from
    payment
where
    staff_id = 2
group by
    customer_id
having
    sum(amount) > 100
order by
    sum(amount) desc
```

# 6. Assessment Test 1

Return the customer IDs of customers who have spent at least $110 with the staff member who has an ID of 2.

```sql
select staff_id, customer_id, sum(amount)
from payment
where staff_id = 2
group by staff_id, customer_id
having sum(amount) > 110
```

How many films begin with the letter J?

```sql
select count(title)
from film
where title like 'J%'
```

What customer has the highest customer ID number whose name starts with an 'E' and has an address ID lower than 500?

```sql
select customer_id, first_name, last_name
from customer
where first_name like 'E%' and address_id < 500
order by customer_id desc
limit 1
```

Wrong answer:

```sql
select max(customer_id), first_name, last_name
from customer
where first_name ilike 'E%'
	and address_id < 5000
-- group by
-- having
-- order by
-- limit
```


# 7. JOIN Clause

JOINS will allow us to combine information from multiple tables. See [documentation](https://www.postgresql.org/docs/9.2/queries-table-expressions.html).

Overview:

- Creating an alias with the `as` clause
- Understanding the different kinds of `join`
  - `inner join`
  - `outer join`
  - `full join`
  - `union`
- Challenge Task

## 7.1. Aliases: AS Clause

Aliases are used to give a table, a column in a table or result, a temporary name. Basic syntax:

```sql
select c1 as new_c1_name
from t1
```

```sql
select sum(c1) as new_c1_name
from t1
-- useful for readability of the data output
```

The `as` operator gets executed at the very end of a query, meaning that we can not use the alies inside a `where` operator. This means the alias is only valid in the `select` statement. Example:

```sql
select count(amount) as "Number of Transactions"
from payment
```

```sql
select customer_id, sum(amount) as "Total Spent"
from payment
group by customer_id
having sum(amount) > 150
-- using "Total Spent" in the having clause returns an error because "Total Spen" does not exist (alias gets assigned at the very end)
```

Note: column aliases are for better readability of the output, whereas table aliases are for better readability and structuring of the query.

## 7.2. (INNER) JOIN Keyword (Intersection)

JOINs allow us to combine multiple tables together. The main reason for the different JOIN types is to decide how to deal with information only present in **one** of the joined tables.

The `inner join` keyword selects records that have matching values in both tables. Basis syntax:

```sql
select order.order_id, customer.first_name
from order inner join customer on order.customer_id = customer.customer_id
-- in this syntax, the INNER keyword is optional
-- inner join order ...
-- the inner join is symmetrical: the order of the tables does not matter
```

**Result**:

| set   | id_A | id_B |
| ----- | ---- | ---- |
| A ∩ B | ...  | ...  |

If we just use `join` without the `inner`, PgSQL will treat it as an `inner join`.

Example: we want to join the payment and customer table.

```sql
select payment.payment_id, payment.customer_id, customer.email
from payment inner join customer on payment.customer_id = customer.customer_id
-- this shows only customer that have done a payment
```

**Alternative in PostgreSQL**:

```sql
select p.payment_id, c.first_name
-- from payment as p inner join customer as c on p.customer_id = c.customer_id
from payment as p join customer as c using(customer_id)
```

The words `inner` and `outer` are optional in all forms. `inner` is the default; `left`, `right`, and `full` imply an outer join.

## 7.3. FULL (OUTER) JOIN Keyword (Union and Symmetric Difference)

There are few different types of OUTER JOINs. They will allow us to specify how to deal with values only present in one of the tables being joined. We will explain:

- `full outer join`
  - clarifying `where null`
- `left outer join`
  - clarifying `where null`
- `right outer join`
  - clarifying `where null`

Basic syntax of `full outer join`:

```sql
select * from order
full outer join customer
-- in this syntax, the OUTER keyword is optional
on order.customer_id = customer.customer_id
-- a full outer join is symmetrical: the order of the tables does not matter
```

**Result**:

| set   | id_A | id_B |
| ----- | ---- | ---- |
| A ∩ B | ...  | ...  |
| A \ B | ...  | NULL |
| B \ A | NULL | ...  |

We can further qualify the statement with a `full outer join` with `where` (and the help of `null` values): get rows unique to either table (rows not found in both tables), i.e. a XOR join (opposite of INNER join):

```sql
select * from order
full outer join customer
-- in this syntax, the OUTER keyword is optional
on order.customer_id = customer.customer_id
where order.customer_id is null or customer.customer_id is null
-- a full outer join with a symmetrical where clause is symmtrical
```

**Result**:

| set   | id_A | id_B |
| ----- | ---- | ---- |
| A \ B | ...  | NULL |
| B \ A | NULL | ...  |

Example:

```sql
select *
from customer
full outer join payment
on customer.customer_id = payment.customer_id
where customer.customer_id is null or payment.customer_id is null

-- we want to return (a) customer ids that are not present in the payment table (customer without historical payment data) and (b) customer ids that are not present in the customer table, but have done payments -> no customer has this property -> we're in compliance with this policy
```

## 7.4. LEFT (OUTER) JOIN Keyword (A)

A `left outer join` results the set of records that are in the left table, if there is no match with the right table, the results are null.

```sql
select * from order
left outer join customer
-- in this syntax, the OUTER keyword is optional
on order.customer_id = customer.customer_id
-- a left outer join is not symmetrical!
```

**Result**:

| set   | id_A | id_B |
| ----- | ---- | ---- |
| A ∩ B | ...  | ...  |
| A \ B    | ...  | NULL |

We can further qualify the statement with a `full left join` with `where` (and the help of `null` values): get rows unique to left table. What if we only wanted entries unique to Table A? Those rows found Table A and not found in Table B.

```sql
select * from order
left outer join customer
-- in this syntax, the OUTER keyword is optional
on order.customer_id = customer.customer_id
where customer.customer_id is null
-- a left outer join is not symmetrical!
```

**Result**:

| set | id_A | id_B |
| --- | ---- | ---- |
| A \ B   | ...  | NULL |

Example:

```sql
select film.film_id, inventory.film_id, film.title, inventory.inventory_id
-- select count(distinct(film.film_id))
-- select count(distinct(inventory.film_id))
from film
left join inventory on film.film_id = inventory.film_id
-- there are 958 distinct films IDs in our inventory and 1000 distinct films on the film table
```

We return all films in the film table, even if they're not present in the inventory table. We can use the `null` values generated to identify films that are not in our inventory:

```sql
select film.film_id, inventory.film_id, film.title, inventory.inventory_id
-- select count(distinct(film.film_id))
-- select count(distinct(inventory.film_id))
from film
left join inventory on film.film_id = inventory.film_id
-- there are 958 distinct films IDs in our inventory and 1000 distinct films on the film table
where inventory.film_id is null
-- this returns the films that are in our films table but not in our inventory
```

Alternative: 

```sql 
select
    distinct f.film_id,
    f.title
from
    film as f full
    outer join inventory as i on f.film_id = i.film_id
where
    i.film_id is null
order by
    f.film_id asc
```



Alternative to example:

```sql
select count(distinct(f.film_id))
	-- f.film_id, i.film_id, f.title
from film as f left join inventory as i on f.film_id = i.film_id
where i.film_id is null
-- # of films that are not in our inventory
```

## 7.5. RIGHT (OUTER) JOIN Keyword (B)

A `right join` is essentially the same as a `left join`, except the tables are switched. This would be the same as switching the table order in `left join`.

```sql
select * from order
right outer join customer
-- in this syntax, the OUTER keyword is optional
on order.customer_id = customer.customer_id
-- a right outer join is not symmetrical!
```

**Result**:

| set   | id_A | id_B |
| ----- | ---- | ---- |
| A ∩ B | ...  | ...  |
| B \ A    | NULL | ...  |

We can add a `where` qualifier:

```sql
select * from order
right outer join customer
-- in this syntax, the OUTER keyword is optional
on order.customer_id = customer.customer_id
where order.customer_id is null
-- a right outer join is not symmetrical!
```

**Result**:

| set | id_A | id_B |
| --- | ---- | ---- |
| B \ A   | NULL | ...  |

## 7.6. UNION Operator

The `union` operator is used to combine the result-set of two or more `select` statements.

- Every `select` statement within `union` must have the same number of columns
- The columns must also have similar data types
- The columns in every `select` statement must also be in the same order

It basically serves to directly concatenate two results together, essentially "pasting" them together. Basic syntax:

```sql
select c_1,...,c_n from t1
union
select c_1,...,c_n from t2
```

**Result**:

| col_1   | col_2   |
| ------- | ------- |
| A.col_1 | A.col_2 |
| B.col_2 | B.col_2 |

## 7.7. JOIN Challenges

**Challenge**: California sales tax laws have changed and we need to alert our customers of this through email. What are the emails of the customers who live in California?

```sql
-- task: what are the emails of the customers that live in California
-- California is a district in the address table

select customer.first_name, customer.last_name, customer.email, address.district
from customer
right join address on customer.address_id = address.address_id
where address.district = 'California'

-- this query returns the same information if we perform an inner join; we perform a right join to make sure that there is no person in California that does not have an email in the database
```

Alternative:

```sql
select a.district, c.email
from address as a join customer as c on a.address_id = c.address_id
where a.district ilike 'california'
order by c.email asc
```

**Challenge**: A customer walks in and is a huge fan of the actor "Nick Wahlberg" and wants to know which movies he is in. Get a list of all the movies "Nick Wahlberg" has been in.

```sql
-- task: get all Nick Wahlberg movies
-- tables: film for the title, film_actor for relationship, actor for first and last name

select actor.first_name, actor.last_name, film.title
from actor
join film_actor
 on actor.actor_id = film_actor.actor_id
join film
 on film.film_id = film_actor.film_id
where actor.first_name = 'Nick' and actor.last_name = 'Wahlberg'
```

Alternative:

```sql
select
	f.title, a.first_name, a.last_name
from film_actor as fa
	join actor as a on fa.actor_id = a.actor_id
	join film as f on f.film_id = fa.film_id
where
	a.first_name ilike 'nick' and
	a.last_name ilike 'wahlberg'
-- group by
-- having
order by f.title asc
-- limit
```

# 8. Advanced SQL Commands

Section Overview:

- Timestamps and EXTRACT
- Math Functions
- String Functions
- Sub-query
- Self-Join

## 8.1. Timestamps and Extract

### 8.1.1. Displaying Current Time Information

In Part One, we will go over a few commands that report back time and date information. These will be more useful when creating our own tables and databases, rather than querying a database.

We've already seen that PostgreSQL can hold date and time information:

- `time` Contains only time
- `date` Contains only date
- `timestamp` Contains date and time
- `timestamptz` Contains date,time, and timezone

Careful considerations should be made when designing a table and database and choosing a time data type. Depending on the situation you may or may not need the full level of `timestamptz`. Remember, you can always remove historical information, but you can't add it.

Let's explore functions and operations related to these specific data types:

- `timezone`
- `now`
- `timeofday`
- `current_time`
- `current_date`

We use the [`show`](https://www.postgresql.org/docs/current/sql-show.html) function:

```sql
show all
show timezone
-- show runtime parameters

select now()
-- return timestamp

select timeofday()
-- return string representation of timestamp

select current_time
-- return time with timezone

select current_date
-- return date
```

### 8.1.2. Extracting Time and Date Information

Let's explore extracting information from a time based data type using:

- `extract()`
- `age()`
- `to_char()`

`extract(field FROM source)` allows you to "extract" or obtain a sub-component of a date value. Valid values for field can be found in the [documentation](https://www.postgresql.org/docs/13/functions-datetime.html). Basic syntax:

```sql
extract(year from date_col)
```

In a full query it becomes:

```sql
-- select date_col becomes
select extract(year from date_col)
from t1
```

Example:

```sql
select extract(month from payment_date) as "Month"
from payment
group by extract(month from payment_date)
-- we can extract: year, quarter, month, week, day
```

`age()` calculates and returns the current age given a timestamp. Basic syntax:

```sql
age(date_col)
-- return for example: 13 years mon 5 days 01:34:13.003423
```

Example:

```sql
select age(payment_date)
from payment
```

`to_char()` general function to convert data types to text (see [Documentation](https://www.postgresql.org/docs/current/functions-formatting.html)). Useful for timestamp formattin. Basic syntax:

```sql
to_char(date_col, 'mm-dd-yyyy')
```

Example:

```sql
select to_char(payment_date,'MM/dd/YYYY')
from payment
```

**Challenge**: During which months did payments occur? Format your answer to return back the full month name.

```sql
-- task: during which month did payments occur?

-- select extract(month from payment_date) <- this returns the months as a number
select to_char(payment_date, 'Month')
from payment
group by to_char(payment_date, 'Month')
```

Alternative:

```sql
select distinct(to_char(payment_date, 'Month'))
from payment
```

Alternative (ordering the month chronologically):

```sql
-- task: during which month did payments occur?

select distinct(extract(month from payment_date)) as "num_month", to_char(payment_date, 'Month')
from payment
order by "num_month"
```

Alternative (without the alias):

```sql
select distinct(extract(month from payment_date)), to_char(payment_date, 'Month')
from payment
order by date_part
```

**Challenge**: How many payments occurred on a Monday?

```sql
-- task: how many payments occured on a monday?

select to_char(payment_date, 'day') as weekday, count(*)
from payment
group by weekday
-- this returns the list of weekday and it's corresponding number of payments
```

```sql
select extract(dow from payment_date), count(*)
from payment
where extract(dow from payment_date) = 1
group by date_part

-- for dow sunday (0) -> monday (1)
```

Alternative (more compact):

```sql
select count(*)
from payment
where extract(dow from payment_date) = 1
```

## 8.2. Mathematical Functions and Operators

See [documentation](https://www.postgresql.org/docs/current/functions-math.html). Examples:

```sql
-- mathematical functions and operators: we will focus on rental_rate and replacement_cost

select round(rental_rate/replacement_cost*100,2) as "percent_cost"
from film
```

```sql
select round(0.1*replacement_cost,2) as deposit
from film
```

## 8.3. String Functions and Operators

See [documentation](https://www.postgresql.org/docs/13/functions-string.html). PostgreSQL also provides a variety of string functions and operators that allow us to edit, combine, and alter text data columns. Examples:

```sql
select length(first_name) from customer
-- returns the length of the first_name of every record
```

```sql
select first_name || ' ' || last_name as full_name
from customer
-- concatenate text
```

```sql
select upper(first_name) || ' ' || upper(last_name) as full_name
from customer
-- concatenate text
-- use lower, upper or initcap functions to convert a string expression, values in a column, etc., to lowercase, uppercase, and proper case.
```

```sql
-- task: create email for customer

select lower(left(first_name,1)) || '_' || lower(last_name) || '@mail.com' as customer_email
from customer

-- using string functions and operators to create a new column that is useful for a certain situation
```

## 8.4. Subquery

See [documentation](https://www.postgresql.org/docs/13/functions-subquery.html). We discuss how to perform a subquery and the `exists` function.

A sub query allows you to construct complex queries, essentially performing a query on the results of another query. The syntax is straightforward and involves two `select` statements. Example:

```sql
select student, grade
from test_score
-- return the data for all the students
```

```sql
select avg(grade)
from test_score
-- returns the average score for the test
```

**Question**: How can we get a list of students who scored better than the average grade?

```sql
select student, grade
from test_score
where grade > (
  select avg(grade)
  from test_score
)
-- returns the data for students who scored better than the average grade
```

The subquery is performed first since it is inside the parenthesis. We can also use the `in` operator in conjunction with a subquery to check against multiple results returned. For example we can operate on a separate table:

```sql
select student, grade
from test_score
where student in (
  select student
  from honor_roll
)
-- we could also do this with a join
```

The `exists` operator is used to test for existence of rows in a subquery. Typically a subquery is passed in the `exists()` function to check if any rows are returned with the subquery (see [w3](https://www.w3schools.com/sql/sql_exists.asp)). The `exists` operator is used to test for the existence of any record in a subquery. The `exists` operator returns TRUE if the subquery returns one or more records. Typical syntax:

```sql
select c1
from t1
where exists(
  select c1
  from t1
  where cond1
)
```

Examples:

```sql
-- task: return film titles that have a higher than average rental cost
select title, rental_rate
from film
where rental_rate > (
 select avg(rental_rate) from film
)

-- subquery: calculate avg rental rate
-- select avg(rental_rate) from film
```

```sql
-- task: grad film titles that have been returned between certain dates

select film_id, title
from film
where film_id in (
 select inventory.film_id
 from inventory
 join rental on rental.inventory_id = inventory.inventory_id
 where return_date between '2005-05-29' and '2005-05-30'
)
order by title asc

-- problem: we do not have the film id
-- solution: we grad the tile with the help of the inventory id. We get the film_id from the inventory and use it as a subquery.
```

```sql
-- task: find customers that have at least one payment, whose amount is greater than 11

select customer_id, first_name, last_name
from customer as c
where exists (
 select *
 from payment as p
 where
  p.customer_id = c.customer_id
  and p.amount > 11
)
order by first_name
-- returns 8 customers
```

**Alternative**:

```sql
-- task: find customers that have at least one payment, whose amount is greater than 11

select c.customer_id, c.first_name, c.last_name
from payment as p, customer as c
where
 p.customer_id = c.customer_id
 and p.amount > 11
```

**Negation**:

```sql
select count(distinct(c.customer_id))
from customer as c
where not exists (
 select *
 from payment as p
 where
  p.customer_id = c.customer_id
  and p.amount > 11
)
-- returns 591
-- returns customers that do not have any payment greater than 11
-- note that this query returns customers that do not exists in the subquery (NOT clients that have payments with an amount less than 11)
```

Note that we cannot negate the alternative to produce the same result, since all customers have at least a payment with an amount less than or equal to 11.

## 8.5. Self-Join

A self-join is query in which a table is joined to itself. Self-joins are useful for comparing values in a column of rows within the same table.

The self join can be viewed a join of two copies of the same table. The table is not actually copied, but SQL performs the command as though it were. There is no special keyword for a self join, its simply standard JOIN syntax with the same table in both parts.

However, when using a self join it is necessary to use an alias for the table, otherwise the table names would be ambiguous. Let's see a syntax example of this. Basic syntax:

```sql
select c1.col, c2.col
from customer as c1
join customer as c2 on c1.some_col = c2.other_col
```

A self join is a join in which a table is joined with itself (which is also called unary relationships), especially when the table has a FOREIGN KEY which references its own PRIMARY KEY. To join a table itself means that each row of the table is combined with itself and with every other row of the table (see [w3](https://www.w3resource.com/sql/joins/perform-a-self-join.php)).

Example:

We store employee records in a table. Employees report to other employees, e.g. employee 1 reports to employee 2. We want results showing the employee name and their reports recipient name.

With the `join` operator:

```sql
select e_emp.name as employee_name, e_rep.name as rep_name
from employee as e_emp
join employee as e_rep
on e_rep.emp_id = e_emp.rep_id
```

Without the `join` opeartor:

```sql
select e_emp.name as employee_name, e_rep.name as rep_name
from employee as e_emp, employee as e_rep
where e_rep.emp_id = e_emp.rep_id
```

Visually the example looks like this:

**EMPLOYEE**
| emp_id | name    | rep_id |
| ------ | ------- | ------ |
| 1      | Andrew  | 3      |
| 2      | Bob     | 3      |
| 3      | Charlie | 4      |
| 4      | David   | 1      |

The join produces:

**EMPLOYEE AS e_emp, EMPLOYEE AS e_rep**
| e_emp.emp_id | e_emp.name | e_emp.rep_id | e_rep.emp_id | e_rep.name | e_rep.rep_id |
| ------------ | ---------- | ------------ | ------------ | ---------- | ------------ |
| 1            | Andrew     | 3            | 1            | Andrew     | 3            |
| 1            | Andrew     | 3            | 2            | Bob        | 3            |
| 1            | Andrew     | 3            | 3            | Charlie    | 4            |
| 1            | Andrew     | 3            | 4            | David      | 1            |
| 2            | Bob        | 3            | 1            | Andrew     | 3            |
| ...          | ...        | ...          | ...          | ...        | ...          |

We join on foreign key = primary key:

**EMPLOYEE AS e_emp JOIN EMPLOYEE AS e_rep ON e_rep.emp_id = e_emp.emp_id**
| e_emp.emp_id | e_emp.name    | **e_emp.rep_id** | **e_rep.emp_id** | e_rep.name    | e_rep.rep_id |
| ------------ | ------------- | ---------------- | ---------------- | ------------- | ------------ |
| <s>1</s>     | <s>Andrew</s> | <s>3</s>         | <s>1</s>         | <s>Andrew</s> | <s>3</s>     |
| <s>1</s>     | <s>Andrew</s> | <s>3</s>         | <s>2</s>         | <s>Bob</s>    | <s>3</s>     |
| 1            | Andrew        | 3                | 3                | Charlie       | 4            |
| <s>1</s>     | <s>Andrew</s> | <s>3</s>         | <s>4</s>         | <s>David</s>  | <s>1</s>     |
| <s>2</s>     | <s>Bob</s>    | <s>3</s>         | <s>1</s>         | <s>Andrew</s> | <s>3</s>     |
| ...          | ...           | ...              | ...              | ...           | ...          |

Example:

```sql
-- task: find all the pairs of films that have the same length (explicit self-join)

select f_left.title, f_right.title, f_right.length
from film as f_left
join film as f_right on f_left.length = f_right.length
where f_left.title != f_right.title
order by f_right.length
```

Alternatives:

```sql
-- task: find all the pairs of films that have the same length (explicit self-join w/out where clause)

select f_left.title, f_right.title, f_right.length
from film as f_left
join film as f_right on
 f_left.length = f_right.length and
 f_left.film_id != f_right.film_id

order by f_right.length
```

```sql
-- task: find all the pairs of films that have the same length (implicit self-join)

select f_left.title, f_right.title, f_right.length
from film as f_left, film as f_right
where
 f_left.length = f_right.length and
 f_left.title != f_right.title
order by f_right.length
```

# 9. Assessment Test 2

We will use a new database for a set of exercise questions. This database has a `public` and `cd` [schema](https://www.postgresql.org/docs/13/ddl-schemas.html). This means the queries for the FROM tables will have `cd.` in front them.

Running Command:

```shell
/Applications/pgAdmin 4.app/Contents/SharedSupport/pg_restore --host "localhost" --port "0000" --username "postgres" --no-password --dbname "exercise" --section=pre-data --section=data --section=post-data --verbose "/.../exercise.tar"
```

How can you retrieve all the information from the cd.facilities table?

```sql
select *
from cd.facility
```

You want to print out a list of all of the facilities and their cost to members. How would you retrieve a list of only facility names and costs?

```sql
select name, m_cost
from cd.facility
```

How can you produce a list of facilities that charge a fee to members?

```sql
select name, m_cost
from cd.facility
where m_cost > 0
```

How can you produce a list of facilities that charge a fee to members, and that fee is less than 1/50th of the monthly maintenance cost? Return the facid, facility name, member cost, and monthly maintenance of the facilities in question.

```sql
select fac_id, name, m_cost, maintenance
from cd.facility
where
 m_cost > 0
 and m_cost < maintenance/50.0
```

How can you produce a list of all facilities with the word 'Tennis' in their name?

```sql
select *
from cd.facility
where name ilike '%tennis%'
```

How can you retrieve the details of facilities with ID 1 and 5? Try to do it without using the OR operator.

```sql
select *
from cd.facility
where fac_id in (1,5)
```

How can you produce a list of members who joined after the start of September 2012? Return the memid, surname, firstname, and joindate of the members in question.

```sql
select *
from cd.member
where join_date between '2012-09-01' and now()
```

Alternative:

```sql
select *
from cd.member
where join_date::date >= '2012-09-01'
```

How can you produce an ordered list of the first 10 surnames in the members table? The list must not contain duplicates.

```sql
select distinct(last_name)
from cd.member
where last_name != 'GUEST'
order by last_name
limit 10
```

You'd like to get the signup date of your last member. How can you retrieve this information?

```sql
select max(join_date)
from cd.member
-- return max
```

Alternative 1:

```sql
select first_name, last_name, join_date
from cd.member
order by join_date desc
limit 1
-- order and limit
```

Alternative 2:

```sql
select first_name, last_name, join_date
from cd.member
where join_date in (
 select max(join_date)
 from cd.member
)
-- where ... in clause; condition is single value
```

Alternative 3:

```sql
select first_name, last_name, join_date
from cd.member as m_left
join (
 select max(join_date) as max_join_date
 from cd.member
) as m_right
on m_left.join_date = m_right.max_join_date
-- inner join on single value
```

Produce a count of the number of facilities that have a cost to guests of 10 or more.

```sql
select count(*)
from cd.facility
where g_cost >= 10
```

Produce a list of the total number of slots booked per facility in the month of September 2012. Produce an output table consisting of facility id and slots, sorted by the number of slots.

```sql
select fac_id, sum(slot) as booked_slots_sept
from cd.booking
where extract(month from start_time) = 9
-- where start_time::date >= '2012-09-01' and start_time::date <= '2012-10-01'
group by fac_id
order by sum(slot) asc
```

Produce a list of facilities with more than 1000 slots booked. Produce an output table consisting of facility id and total slots, sorted by facility id.

```sql
select fac_id, sum(slot)
from cd.booking
group by fac_id
having sum(slot) > 1000
order by fac_id
```

How can you produce a list of the start times for bookings for tennis courts, for the date '2012-09-21'? Return a list of start time and facility name pairings, ordered by the time.

```sql
select b.start_time, f.name
from cd.booking as b
join cd.facility as f on b.fac_id = f.fac_id
where
 b.start_time::date = '2012-09-21'
 and f.name ilike '%tennis%court%'
order by b.start_time
-- keyword as is optional
```

Alternative:

```sql
select start_time, f.name
from cd.booking as b
join cd.facility as f on b.fac_id = f.fac_id
where
  start_time between '2012-09-21' and '2012-09-22'
  and f.name ilike '%tennis%court%'
order by start_time
```

How can you produce a list of the start times for bookings by members named 'David Farrell'?

```sql
select start_time
from cd.booking as b
join cd.member as m on b.mem_id = m.mem_id
where
 m.first_name = 'David'
 and m.last_name = 'Farrell'
```

# 10. Creating Databases and Tables

Let's now shift our focus to creating our own databases and tables.

Section Overview

- Data Types
- Primary and Foreign Keys
- Constraints
- `create`
- `insert`
- `update`
- `delete`, `alter`, `drop`

We first focus on learning a few theoretical concepts, such as choosing the correct data type for a stored value and setting possible constraints on it. We will also learn about primary and foreign keys.

## 10.1. Data Types

Main data types in SQL:

- Boolean
  - `True` or `False`
- Character
  - `char`, `varchar`, and `text`
- Numeric
  - `integer` and `floating-point number`
- Temporal
  - `date`, `time`, `timestamp`, and `interval`
- UUID: Universally Unique Identifiers
- Array
  - Stores an `array` of `strings`, `numbers`, etc.
- JSON
- Hstore key-value pair
- Special types such as network address and geometric data.

When creating databases and tables, you should carefully consider which data types should be used for the data be stored. Review the [documentation](https://www.postgresql.org/docs/current/datatype.html) to see limitations of data types.

## 10.2. Primary and Foreign Key

A **primary key** is a column or a group of columns used to identify a row uniquely in a table. For example, our dvdrental database we saw customers had a unique, non-null customer_id column as their primary key.

Primary keys are also important since they allow us to easily discern what columns should be used for joining tables together. Later we will learn about `serial` data type.

A **foreign key** is a field or group of fields in a table that uniquely identifies a row in another table. A foreign key is defined in a table that references to the primary key of the other table. The table that contains the foreign key is called referencing table or child table. The table to which the foreign key references is called referenced table or parent table. A table can have multiple foreign keys depending on its relationships with other tables.

Recall in the dvdrental database payment table, each payment row had its unique payment_id (a primary key) and identified the customer that made the payment through the customer_id (a foreign key since it references the customer table's primary key).

You may begin to realize primary key and foreign key typically make good column choices for joining together two or more tables. When creating tables and defining columns, we can use constraints to define columns as being a primary key, or attaching a foreign key relationship to another table.

## 10.3. Constraints

Constraints are the rules enforced on data columns on table. These are used to prevent invalid data from being entered into the database. This ensures the accuracy and reliability of the data in the database.

Constraints can be divided into two main categories:

- Column Constraints: Constrains the data in a column to adhere to certain conditions.
- Table Constraints: Applied to the entire table rather than to an individual column.

The most common **column constraints** used:

- `not null` Constraint: Ensures that a column cannot have NULL value.
- `unique` Constraint: Ensures that all values a column are different.
- `primary` Key: Uniquely identifies each row/record in a database table.
- `foreign` Key: Constrains data based or columns in other tables.
- `check` Constraint: Ensures that all values in a column satisfy certain conditions.
- `exclusion` Constraint: Ensures that if any two rows are compared on the specified column or expression using the specified operator, not all of these comparisons will return TRUE.

The most common **table constraints** used:

- `check(condition)`: to check condition when inserting or updating data.
- `refenrences`: to constrain the value stored in the column that must exist in a column in another table.
- `unique(column_list)`: Forces the values stored in the columns listed inside the parentheses to be unique.
- `primary key(columns_list)`: Allows you to define the primary key that consists of multiple columns.

## 10.4. CREATE TABLE Statement (TABLE)

General syntax:

```sql
CREATE TABLE table_name(
  column_name TYPE column_constraint,
  column_name TYPE column_constraint,
  table_constraint table_constraint
)
INHERITS existing_table_name;
```

Example:

```sql
create table player(
  player_id serial primary key,
  age smallint not null
)
```

Always refer to the [documentation](https://www.postgresql.org/docs/current/datatype-numeric.html) when choosing data types. `serial` datatype:

- In PostgreSQL, a sequence is a special kind of database object that generates a sequence of integers.
- A sequence is often used as the primary key column in a table.
- It will create a sequence object and set the next value generated by the sequence as the default value for the column.
- This is perfect for a primary key, because it logs unique integer entries for you automatically upon insertion.
- If a row is later removed, the column with the `serial` data type will not adjust, marking the fact that a row was removed from the sequence, e.g. for 1,2,3,5,6,7 -> you know row 4 was removed at some point.

We create a database (in the table we generate a password and an email column, see [here](https://stackoverflow.com/questions/2647158/how-can-i-hash-passwords-in-postgresql) and [here](https://dba.stackexchange.com/questions/68266/what-is-the-best-way-to-store-an-email-address-in-postgresql) for best practices):

```sql
create table account(
 user_id serial primary key,
 username varchar(50) unique not null,
 password varchar(50) not null,
 email varchar(255) unique not null,
 create_date timestamp not null,
 last_login timestamp
)
```

```sql
create table job(
 job_id serial primary key,
 job_name varchar(255) unique not null
)
```

```sql
create table account_job(
 user_id int references account(user_id),
 -- serial should be only used as a primary key for the table it is in
 job_id int references job(job_id),
 hire_date timestamp
)
```

## 10.5. INSERT INTO Statement (RECORD)

The `insert into` statement is used to insert new records in a table. General syntax:

```sql
insert into table(col1, col2, ...)
values
  (val1_1, val2_1, ...),
  (val1_2, val2_2, ...)
  ...
```

Syntax for inserting values from another table:

```sql
insert into table(col1, col2, ...)
select col1, col2, ...
from another_table
where condition
```

Keep in mind, the inserted row values must match up for the table, including constraints. `serial` columns do not need to be provided a value (since serial is a sequence object, so it will automatically update the next available `int` for that row).

Example:

```sql
insert into account(username, password, email, create_date)
values
 ('Luis','password','luis@mail.com',now())
```

```sql
insert into job(job_name)
values
 ('Astronaut')
```

```sql
insert into account_job(user_id, job_id, hire_date)
values
 (1,1,now())
```

## 10.6. UPDATE Statement (RECORD)

The `update` statement is used to modify the existing records in a table. General syntax:

```sql
update table
set
  col1 = val1,
  col2 = val2,
  ...
where condition
```

Example:

```sql
update account
set last_login = now()
where last_login is null
```

We can also reset everything if we don't add a `where` condition:

```sql
update account
set last_login = now()
```

We can also set everything based on another column:

```sql
update account
set last_login = create_date
```

We can also use another table's values (so called UPDATE JOIN):

```sql
update table_left
set col_left = table_right.col_right
from table_right
where table_left.id = table_right.id
```

We can also return the affected rows:

```sql
update account
set last_login = create_date
returning account_id, last_login
```

Examples:

```sql
update account
set last_login = now()
returning *
```

```sql
update account
set last_login = create_date
returning *

```

```sql
update account_job as aj
 set hire_date = a.create_date
from account as a
 where a.user_id = aj.user_id
returning *
```

**Note**: Be careful when updating records in a table! Notice the `where` clause in the `update` statement. The `where` clause specifies which record(s) should be updated. If you omit the `where` clause, all records in the table will be updated!

## 10.7. DELETE Statement (RECORD)

The `delete` statement is used to delete existing records in a table. Basic syntax:

```sql
delete from t1
where id = 1
```

We can delete rows based on their presence in other tables:

```sql
delete from t1
using t2
where t1.id = t2.id
```

We can delete all rows in a table:

```sql
delete from t1
```

**Note**: Be careful when deleting records in a table! Notice the `where` clause in the `delete` statement. The `where` clause specifies which record(s) should be deleted. If you omit the `where` clause, all records in the table will be deleted!

Similar to the `update` statement, we can also add in a `returning` call to return rows that were removed.

## 10.8. ALTER TABLE Statement (TABLE AND COLUMN)

The `alter table` statement is used to add, delete, or modify columns in an existing table. The `alter table` statement is also used to add and drop various constraints on an existing table. See [documentation](https://www.postgresql.org/docs/current/sql-altertable.html) for all the options available in the synopsis.

### 10.8.1. RENAME, ADD, DROP, SET Statements (TABLE AND COLUMN)

In general the `alter` clause allows for changes to an existing table structure, e.g.:

- Adding, dropping or renaming columns
- Changing a column's data type
- Set `default` values for a column
- Add `check` constraints
- Rename table

General syntax:

```sql
alter table table_name
-- action
-- rename table
rename to new_name
-- rename column
rename column col_name to new_col_name
-- add columns
add column new_col type
-- add unique
add unique(col_name)
-- remove columns
drop column col_name
-- alter constraints
alter column data_type
set default value
drop default value
set not null
drop not null
add constraint constraint_name
```

Examples:

```sql
-- insert into info(title)
-- values ('some new title')
-- returns err: violates not-null constraint

alter table info
alter column ppl drop not null
```

To alter unique constraint see [here](https://www.w3schools.com/sql/sql_unique.asp).

### 10.8.2. DROP Statement (COLUMN)

`drop` allows for the complete removal of a column in a table. In PostgreSQL this will also automatically remove all of its indexes and constraints involving the column. However, it will not remove columns used in views, triggers, or stored procedures without the additional `cascade` clause. General syntax:

```sql
alter table table_name
drop column col_name -- cascade
-- add the cascade keyword to remove all dependencies
```

Check for existence to avoid error:

```sql
alter table table_name
drop column if exists col_name
```

Drop multiple columns:

```sql
alter table table_name
drop column col1
drop column col2
```

## 10.9. CHECK Constraint

The `check` constraint is used to limit the value range that can be placed in a column. If you define a `check` constraint on a column it will allow only certain values for this column. If you define a `check` constraint on a table it can limit the values in certain columns based on values in other columns in the row. Basically, the `check` constraint allows us to create more customized constraints that adhere to a certain condition. General syntax:

```sql
create table example(
  id serial primary key,
  age smallint check (age > 21),
  parent_age smallint check (parent_age > age)
)
```

Example:

```sql
create table employee(
 emp_id serial primary key,
 fist_name varchar(50) not null,
 last_name varchar(50) not null,
 birthdate date check(birthdate > '1900-01-01'),
 hire_date date check(hire_date > birthdate),
 salary int check (salary > 0)
)
```

# 11. Assessment Test 3

This will test your knowledge of the previous section, focused on creating databases and table operations. This test will actually consist of a more open-ended assignment. Complete the following task:

- Create a new database called "school" this database should have two tables: teachers and students.
- The students table should have columns for student_id, first_name, last_name, homeroom_nr, phone, email, and graduation year.
- The teachers table should have columns for teacher_id, first_name, last_name, homeroom_nr, department, email, and phone.
- The constraints are mostly up to you, but your table constraints do have to consider the following:
  - We must have a phone number to contact students in case of an emergency.
  - We must have ids as the primary key of the tables
  - Phone numbers and emails must be unique to the individual.
- Once you've made the tables, insert a student named Mark Watney (student_id=1) who has a phone number of 777-555-1234 and doesn't have an email. He graduates in 2035 and has 5 as a homeroom number.
- Then insert a teacher names Jonas Salk (teacher_id = 1) who as a homeroom number of 5 and is from the Biology department. His contact info is: jsalk@school.org and a phone number of 777-555-4321.

Solution:

```sql
create table student(
 student_id serial primary key,
 first_name varchar(50) not null,
 last_name varchar(50) not null,
 homeroom_nr varchar(50),
 phone varchar(50),
 email varchar(255),
 grad_year date
)
```

```sql
create table teacher(
 teacher_id serial primary key,
 first_name varchar(50) not null,
 last_name varchar(50) not null,
 homeroom_nr smallint,
 department varchar(255),
 email varchar(255),
 phone varchar(255)
)
```

```sql
-- change data type from date to smallint to store only the grad year
alter table student
alter column grad_year type smallint using (extract(year from grad_year)::smallint)
```

```sql
-- change data type from varchar to smallint to store only a number
alter table student
alter column homeroom_nr type smallint using (homeroom_nr::smallint)
```

```sql
-- add unique constraint to phone and email columns (contraint will be assign to one name!)
alter table student
add unique(phone, email)
```

```sql
insert into student(
 first_name,
 last_name,
 phone,
 grad_year,
 homeroom_nr
)
values(
 'Mark',
 'Watney',
 '777-555-1234',
 2035,
 5
)
```

```sql
insert into teacher(
 first_name,
 last_name,
 homeroom_nr,
 department,
 email,
 phone
)
values(
 'Jonas',
 'Salk',
 5,
 'Biology',
 'jsalk@school.org',
 '777-555-4321'
)
```

# 12. Conditional Expressions and Procedures

Section Overview

- `case`
- `coalesce`
- `nullif`
- `cast`
- Views
- Import and Export Functionality

These keywords and functions will allow us to add logic to our commands and workflows in SQL.

## 12.1. CASE ... END Statement

We can use the `case` statement to only execute SQL code when certain conditions are met. This is very similar to `if ... else` statements in other programming languages.

There are two main ways to use a `case` statement, either a general `case` or a `case` expression. Both methods can lead to the same results. Let's first show the syntax for a **general** `case` (more flexible):

```sql
case
  when cond1 then res1
  when cond2 then res2
  else default_res
end
from t1
```

Example:

| a   |
| --- |
| 1   |
| 2   |

```sql
select a
case
  when a = 1 then 'one'
  -- if the instance is equal to one, return the string 'one'
  when a = 2 then 'two'
  else 'other'
end -- as new_col_name
from test
-- this generates a new column named 'Case'
```

| a   | Case |
| --- | ---- |
| 1   | one  |
| 2   | two  |

The `case` **expression syntax** first evaluates an expression then compares the result with each value in the `when` clauses sequentially (it only works for equality):

```sql
case expresssion
  when val1 then res1
  when val2 then res2
  else default_res
end
```

```sql
select a
case a
  when 1 then 'one'
  when 2 then 'two'
  else 'other'
end -- as new_col_name
from test
-- yields the same resulst as the query above
```

Example:

```sql
select customer_id,
case
 when (customer_id <= 100 ) then 'Premium'
 when (customer_id between 101 and 200) then 'Plus'
 else 'Normal'
end as tier
from customer
order by customer_id
```

```sql
select customer_id,
case customer_id
 when 2 then 'First Place'
 when 5 then 'Second Place'
 when 11 then 'Third Place'
 else null
end as raffle_results
from customer
order by raffle_results
```

Example:

```sql
select rental_rate, count(*)
from film
group by rental_rate
order by rental_rate
```

We can reformat the results of the query above with the `case` statement:

```sql
select
    sum(
        case
            rental_rate
            when 0.99 then 1
            else 0
        end
    ) as bargains,
    sum(
        case
            rental_rate
            when 2.99 then 1
            else 0
        end
    ) as regular,
    sum(
        case
            rental_rate
            when 4.99 then 1
            else 0
        end
    ) as premium
from
    film
```

Alternative: 

```sql 
select
    case
        rental_rate
        when 0.99 then 'bargains'
        when 2.99 then 'regular'
        when 4.99 then 'premium'
    end as tier,
    rental_rate,
    count(*)
from
    film
group by
    rental_rate
```


**Challenge**: We want to know and compare the various amounts of films we have per movie rating. Use `case` and the dvdrental database:

```sql
select
 sum(
  case rating
  when 'NC-17' then 1
  else 0
  end) as nc17,
 sum(
  case rating
  when 'G' then 1
  else 0
  end ) as g,
 sum(
  case rating
  when 'PG' then 1
  else 0
  end) as pg,
 sum(
  case rating
  when 'PG-13' then 1
  else 0
  end) as pg13,
 sum(
  case rating
  when 'R' then 1
  else 0
  end ) as r
from film
```

Better option: 

```sql 
select rating, count(*)
from film
group by rating
```

## 12.2. COALESCE() Function

The `coalesce` function accepts an unlimited number of arguments. It returns the first argument that is not null. If all arguments are null, the `coalesce` function will return null.

```sql
coalesce(arg_1,...,arg_n)
```

The `coalesce` function becomes useful when querying a table that contains null values and substituting it with another value. Example:

```sql
select item, (price-discount) as final_price
from price_table
-- this query returns null as the final_price if the discount is null
```

This becomes:

```sql
select item, (price-coalesce(discount,0)) as final price
from price_table

```

## 12.3. CAST() Function

The `cast` operator let's you convert from one data type into another. Keep in mind not every instance of a data type can be `cast` to another data type, it must be reasonable to convert the data, for example '5' to an integer will work, 'five' to an integer will not. There are two options:

```sql
select cast('5' as int)
```

```sql
select '5'::int
```

## 12.4. NULLIF() Function

The NULLIF function takes in 2 arguments and returns `null` if both are equal, otherwise it returns the first argument passed.

Example:
```sql
nullif(10,10)
-- returns null
```

This becomes very useful in cases where a `null` value would cause an error or unwanted result.

Example: Given this table calculate the ratio of department A to deparment B.

| Name    | Dept |
| ------- | ---- |
| Alice   | A    |
| Bob     | A    |
| Charlie | B    |

```sql
select(
	sum(case when dept = 'A' then 1 else 0 end)/
	sum(case when dept = 'B' then 1 else 0 end)
) as dept_ratio
from dept
```

But what happens when department B has no people?

```sql
select(
	sum(case when dept = 'A' then 1 else 0 end)/
	nullif(sum(case when dept = 'B' then 1 else 0 end),0)
) as dept_ratio
from dept
```

If the denominator is 0 we return a null.

## 12.5. (CREATE) VIEW Statement

A view is a virtual table based on the result-set of an SQL statement.

A view contains rows and columns, just like a real table. The fields in a view are fields from one or more real tables in the database. You can add SQL statements and functions to a view and present the data as if the data were coming from one single table.

Often there are specific combinations of tables and conditions that you find yourself using quite often for a project. Instead of having to perform the same query over and over again as a starting point, you can create a `view` to quickly see this query with a simple call.

Basic syntax:
```sql
select c1,c2,c3,c4
from t1
join t2
on t1.c1 = t2.c3
```

Becomes:
```sql
select * from view
```

A view is a database object that is of a stored query. A view can be accessed as a virtual table in PostgreSQL. Notice that a view does not store data physically, it simply stores the query. It transforms a complex query into a (virtual table). You can also update and alter existing views.

Examples:

```sql
create view customer_info as
select first_name, last_name, address
from customer as c
join address as a
on c.address_id = a.address_id
```

Afterwards we can call:

```sql
select * from customer_info
```

To modify the view we can:

```sql
create or replace view customer_info as
select first_name, last_name, address, district
from customer as c
join address as a
on c.address_id = a.address_id
```

To drop / delete / remove the view we can (check first if it exists to prevent errors):

```sql
drop view if exists customer_info
```

To rename:

```sql
alter view customer_info rename to customer_info_new
```

# 13. Import and Export

Useful links:

- [Documentation on COPY Function](https://www.postgresql.org/docs/current/sql-copy.html)
- [How to import CSV file data into a PgSQL table?](https://stackoverflow.com/questions/2987433/how-to-import-csv-file-data-into-a-postgresql-table)
- [How to import and export data using CSV files in PostgreSQL](https://www.enterprisedb.com/postgres-tutorials/how-import-and-export-data-using-csv-files-postgresql)
- [Create table from csv file with headers](https://stackoverflow.com/questions/21018256/can-i-automatically-create-a-table-in-postgresql-from-a-csv-file-with-headers)

Not every outside data file will work, variations in formatting, macros, data types, etc. may prevent the import command from reading the file, at which point, you must edit your file to be compatible with PgSQL.

The Import command DOES NOT create a table for you. It assumes a table is already created. Currently there is no automated way within pgAdmin to create table directly from a `.csv` file.

Import example:

```sql
command " "\\copy public.simple (id, a, b, c) FROM '/Users/aceituno/Desktop/projects-ss21/sql/simple_table.csv' DELIMITER ',' CSV HEADER QUOTE '\"' ESCAPE '''';""
```

We imported twice so we deleted duplicates with:

```sql
-- task: delete duplicates
-- solution: find a identifying column and use the ctdi (physical location of the row version)
-- assumptions: we can identify duplicates based on column id

delete from simple ls using(
	select min(ctid) as ctid ,id
	from simple
	group by id
  having count(*)>1
) rs
where ls.id = rs.id
and ls.ctid <> rs.ctid

-- The USING clause is a shorthand that allows you to take advantage of the specific situation where both sides of the join use the same name for the joining column(s). It takes a comma-separated list of the shared column names and forms a join condition that includes an equality comparison for each one. For example, joining T1 and T2 with USING (a, b) produces the join condition ON T1.a = T2.a AND T1.b = T2.b.

-- ctid: The physical location of the row version within its table. Note that although the ctid can be used to locate the row version very quickly, a row's ctid will change each time it is updated or moved by VACUUM FULL. Therefore ctid is useless as a long-term row identifier. The OID, or even better a user-defined serial number, should be used to identify logical rows.
```

**Logic of deleting duplicates**:

```sql
-- general delete syntax

delete from ls
using rs
where ls.id = ls.id

-- our specific case

delete from ls
using rs
where ls.id = rs.id
and rc.ctid != ls.ctid

-- construction rs

select min(ctid) as ctid, id
from ls
group by id
having count(*)>1
```

# 14. PgSQL with Python

In this section of the course I'll give you a quick overview of how to use the psycopg2 library with Python to interact with a database in PostgreSQl with Python.

# 15. SQL Window Function Part 1

## 15.1. Fundamentals, the Over Clause and Partition By
From [SQL Window Function](https://www.youtube.com/watch?v=Ww71knvhQ-s). [Documentation on Window Function](https://www.postgresql.org/docs/current/tutorial-window.html). [Documentation on Window Functions](https://www.postgresql.org/docs/8.4/functions-window.html).

A window function performs a calculation across a set of table rows that are somehow related to the current row. This is comparable to the type of calculation that can be done with an aggregate function. However, window functions do not cause rows to become grouped into a single output row like non-window aggregate calls would. Instead, the rows retain their separate identities. For example these queries:

```sql
select max(salary) as max_salary
from employee
```

```sql
select dept_name, max(salary) as max_salary_per_department
from employee
group by dept_name
```
Become these:

```sql
select e.*, max(salary) over() as max_salary
from employee as e
-- the over clause with no parameter produces a window of the whole table
```

```sql
select e.*, max(salary) over( partition by dept_name ) as max_salary_per_dept
from employee as e
-- shows max salary per deparment in addition to employee data
```

Notes that the  rows considered by a window function are those of the “*virtual table*” produced by the query's `FROM` clause (as filtered by its `WHERE`, `GROUP BY`, and `HAVING` clauses if any). For example, a row removed because it does not meet the WHERE condition is not seen by any window function.

## 15.2. Other examples and Row Number and Order By (inside Over Clause)

```sql
select e.*, row_number() over() as rn
from employee e
-- gives each record a unique identifier; to use it, we can pass the query as a subquery
```

```sql
select e.*, row_number() over( partition by dept_name ) over() as rn
from employee e
-- gives each record per department an identifier
```

Note that You can also control the order in which rows are processed by window functions using ORDER BY within OVER. (The window ORDER BY does not even have to match the order in which the rows are output.) Here is an example:

```sql
SELECT depname, empno, salary, rank() OVER (PARTITION BY depname ORDER BY salary DESC)
FROM empsalary
```

From our previous example

```sql
select e.*, row_number() over(partition by dept_name order by emp_id) as rn
from employee e
-- We make the assumption that emp_id reflects when the employee joined the company
```

We use this query as a subquery to fetch the first 2 employees from each department to join the company

```sql
select *
from
  (select e.*, row_number() over(partition by dept_name order by emp_id) as rn from employee e) sq
where hq.rn < 3
```

## 15.3. Window Functions: Rank, Dense Rank

```sql
select e.*, rank() over(partition by dept_name order by salary desc) as rnk
from employee e
```

We use this subquery to determine the employees with the top 3 salaries per department

```sql
select *
from (select e.*, rank() over(partition by dept_name order by salary desc) as rnk
from employee e) sq
where sq.rnk < 4
```

```sql
select e.*, rank() over(partition by dept_name order by salary desc) as rnk, dense_rank() over(partition by dept_name order by salary desc) as dense_rnk
from employee e
```

Alternative:

```sql
select e.*, rank() over w as rnk, dense_rank() over w as dense_rnk
from employee e
window w as over(partition by dept_name order by salary desc)
```

Note that when a query involves multiple window functions, it is possible to write out each one with a separate OVER clause, but this is duplicative and error-prone if the same windowing behavior is wanted for several functions. Instead, each windowing behavior can be named in a WINDOW clause and then referenced in OVER. For example:

```sql
SELECT sum(salary) OVER w, avg(salary) OVER w
  FROM empsalary
  WINDOW w AS (PARTITION BY depname ORDER BY salary DESC);
```

## 15.4. Window Functions: Lead and Lag

Task: Fetch a query to display if the salary of an employee is higher, lower or equal to the previous employee. **Preparation**:

```sql
select e.*, lag(salary) over (partition over dept_name order by emp_id) as prev_emp_salary
from employee e
```

We can pass some other arguments with the lag function (see [Documentation](https://www.postgresql.org/docs/8.4/functions-window.html)).

```sql
select e.*, lag(salary,2,0) over (partition over dept_name order by emp_id) as prev_emp_salary
from employee e
```

Lead gives us the rows that are following the current row.

```sql
select e.*, lead(salary) over (partition over dept_name order by emp_id) as next_emp_salary
from employee e
```

**Solution**:

```sql
select
  e.*,
  lag(salary) over w as prev_emp_salary,
  case
    when e.salary > lag(salary) over w then 'Higher than previous employee'
    when e.salary < lag(salary) over w then 'Lower than previous employee'
    when e.salary = lag(salary) over w then 'Same as previous employee'
  end sal_range
from employee e
window w as (partition over dept_name order by emp_id)
```

Another example from our database:

```sql
select
	p.*,
	lag(amount) over w1 as prev_amount,
	case
		when amount > lag(amount) over w2 then 'Higher than previous amount'
		when amount < lag(amount) over w2 then 'Lower than previous amount'
		when lag(amount) over w2  is null then 'No info'
		else 'The same as previous amount'
	end as amount_range
from payment p
window w1 as (partition by customer_id order by payment_date), w2 as (partition by customer_id order by payment_date)
-- note that w1 and w2 are identical
```

The same example more concise:

```sql
select
	p.*,
	lag(amount) over w as prev_amount,
	case
		when amount > lag(amount) over w then 'Higher than previous amount'
		when amount < lag(amount) over w then 'Lower than previous amount'
		when lag(amount) over w  is null then 'No info'
		else 'The same as previous amount'
	end as amount_range
from payment p
window w as (partition by customer_id order by payment_date)
```

# 16. SQL Window Function Part 2

## 16.1. First and Last Value

From [SQL Window Function Part 2](https://www.youtube.com/watch?v=zAmJPdZu8Rg). [Documentation on Window Functions](https://www.postgresql.org/docs/8.4/functions-window.html). Task: Write a query to display the most expensive product under each category (corresponding ot each record).

```sql
select p.*, first_value(product_name) over(partition by product_category order by price desc) as most_exp_per_category
from product p
```

Example from DVD rental data:

```sql
select distinct(customer_id), first_value(payment_id) over(partition by customer_id order by amount desc) as most_exp_payment
from payment p
order by customer_id
```

This window function does the same as the following `group by` and aggregate function.

```sql
select customer_id, payment_id
from payment p
group by customer_id, payment_id
having amount = max(amount)
order by customer_id
```

Task: Write a query to display the least expensive product under each category (corresponding to each record)

```sql
select *, last_value(product_name) over(partition by product_category order by price desc) as least_exp_product
from product
```

This delivers the wrong result! The reason is the default **frame clause**.

## 16.2. Frame Clause

Note that `first_value`, `last_value`, and `nth_value` consider only the rows within the "*window frame*", which by default contains the rows from the start of the partition through the last peer of the current row. This is likely to give unhelpful results for last_value and sometimes also nth_value. You can redefine the frame by adding a suitable frame specification (RANGE or ROWS) to the OVER clause. See Section 4.2.8 for more information about frame specifications. The default frame clause is:

```sql
select
  p.*,
  last_value(product_name) over(
    partition by product_category
    order by price desc
    range between unbounded preceding and current row
  )
from product p
```

To use the `last_value` window function, we need to adjust the frame clause:

```sql
select
  p.*,
  last_value(product_name) over(
    partition by product_category
    order by price desc
    range between unbounded preceding and unbounded following
  )
from product p
```

An alternative frame is the following:

To use the `last_value` window function, we need to adjust the frame clause:

```sql
select
  p.*,
  last_value(product_name) over(
    partition by product_category
    order by price desc
    rows between unbounded preceding and unbounded following
  )
from product p
```

This alternative becomes relevant when we have duplicates. `rows` considers the current row while `range` considers the last row of all duplicate values. We can also specify the number of rows:

```sql
select
  p.*,
  last_value(product_name) over(
    partition by product_category
    order by price desc
    rows between 2 preceding and 2 following
  )
from product p
```

An example from our database:

```sql
-- fetch lowest amount per customer
-- default frame: range between unbounded preceding and current row
select
	p.*,
	-- first_value(payment_id) over(partition by customer_id order by amount desc) as highest_payment,
	last_value(amount) over(
		partition by customer_id
		order by amount desc
		range between unbounded preceding and unbounded following
	) as lowest_payment
from payment p
-- order by amount
```

## 16.3. Windows Clause

```sql
select
  *,
  first_value(product_name) over w as most_exp_product,
  last_value(product_name) over w as least_exp_product
from product
window w as (partition by product_category order by price desc range between unbounded preceding and unbounded following)
-- order by
```

## 16.4. N-th Value

Fetch a value from any particular position. Task: Write a query to display the second most expensive product under each category.

```sql
select
  *,
  nth_value(product_name, 2) over(partition by product_category order by price desc) as second_most_expensive
from product
```

If the number of records is less that the parameter, the `nth_value` function will return `null`. This query won't display correctly for the first record (see `frame` clause above). We can fix this:

```sql
select
  *,
  nth_value(product_name, 2) over w as second_most_expensive
from product
window w as (partition by product_category order by price desc range between unbounded preceding and unbounded following)
```
## 16.5. Ntile

Task: Write a query to segregate all the expensive phones, mid range and the cheaper phones.

```sql
with phone_bucket as (
  select
    *,
    ntile(3) over w as bucket
  from product
  where product_category = 'Phone'
)

select
  product_name,
  case
    when bucket = 1 then 'Expensive Phone'
    when bucket = 2 then 'Mid Phone'
    when bucket = 3 then 'Cheaper Phone'
  end
from phone_bucket
```
## 16.6. Cumulative Distribution Cume_Dist

`cume_dist = sum (# of rows with the same value as the current row / # of rows)`

Task: Write a query to fetch all products which are constituting the first 30% of the data in products table based on price -> write a query to fetch the top 30% products based on price.

```sql
select
  *,
  cume_dist() over (order by price desc) as cume_dist_by_price
from product
-- cast cume_dist() to numeric to use round function
```

We can clean up the table:

```sql
select
  *,
  round(cume_dist() over (order by price desc)::numeric*100,2) as cume_dist_by_price
from product
-- cast cume_dist() to numeric to use round function
```

We can then use this query as a subquery and filter our data:

```sql
with cume_dist_t as (
  select
    *,
    round(cume_dist() over (order by price desc)::numeric*100,2) as cume_dist_by_price
from product
)

select product_name, (cume_dist_by_price || '%') as cume_dist_pct
from cume_dist_t
where cume_dist_by_price <= 30
```

## 16.7. Percent Rank

Similar to `cume_list`. Relative rank of the current row. `percent_rank = (# of current row - 1) / (# of rows -1)`

Task: Write a query to identify how much percentage more expensive is the phone "Galaxy Z Fold 3" when compared to all products

```sql
select
  *,
  round(percent_rank() over(order by price)::numeric*100,2) as pct_rank
from product
```

We use this as our subquery:

```sql
with pct_rank as (
  select
  *,
  round(percent_rank() over(order by price)::numeric*100,2) as pct_rank
  from product
)

select product_name, pct_rank
from pct_rank
where product_name = 'Galaxy Z Fold 3'
```

# 17. SQL With Clause and CTE (Common Table Expression) or Sub-Query Factoring

From [SQL WITH Clause](https://www.youtube.com/watch?v=QNfnuK-1YYY&).

Task: Find employees with a salary higher than the average.

```sql
with average_salary as (
  select avg(salary)::int
  from employee
)

select *
from employee, average_salary
where salary > average_salary
```

Task: Find stores with sales higher than the average across all stores.

```sql
-- find sales per store
select store_id, sum(cost) as sales_per_store
from sales
group by store_id

-- compute average revenue across all stores
select round(avg(sales_per_store)::numeric, 2) as avg_sales
from (
  select store_id, sum(cost) as sales_per_store
  from sales
  group by store_id
)

-- filter by the comparisson average revenue < store revenue
select *
from (
  select store_id, sum(cost) as sales_per_store
  from sales
  group by store_id
) sales_per_store
join (
  select round(avg(sales_per_store)::numeric, 2) as avg_sales
  from (
    select store_id, sum(cost) as sales_per_store
    from sales
    group by store_id
  ) sales_per_store
) avg_sales
on sales_per_store.sales_per_store > avg_sales.avg_sales
```

This query becomes:

```sql
with sales_per_store (store_id, sales_per_store) as (
  select store_id, sum(cost) as sales_per_store
  from sales
  group by store_id
), avg_sales (avg_sales) as (
  select round(avg(sales_per_store)::numeric, 2) as avg_sales
  from sales_per_store
)

select *
where sales_per_store > avg_sales
```

Example from our database:

```sql
with revenue (customer_id, revenue) as (
  select customer_id, rental_id * amount as revenue
  from payment
), revenue_per_store (customer_id, revenue_per_store) as (
  select customer_id, sum(revenue) as revenue_per_store
  from revenue
  group by customer_id
  order by customer_id
), avg_revenue (avg_revenue) as (
  select round(avg(revenue_per_store) :: numeric, 2) as avg_revenue
  from revenue_per_store
)

select customer_id, revenue_per_store
from revenue_per_store, avg_revenue
where revenue_per_store > avg_revenue
```

# 18. Practice Complex SQL Queries

From [Practice Complex SQL Queries](https://www.youtube.com/watch?v=FNYdBLwZ6cE).

## 18.1. Exercise 1

```sql
-- Query 1:
 -- Write a SQL query to fetch all the duplicate records from a table.
 --Tables Structure:

create table users (user_id int primary key, user_name varchar(30) not null, email varchar(50));

insert into users
values (1, 'Sumit', 'sumit@gmail.com'),
       (2, 'Reshma', 'reshma@gmail.com'),
       (3, 'Farhana', 'farhana@gmail.com'),
       (4, 'Robin', 'robin@gmail.com'),
       (5, 'Robin', 'robin@gmail.com'),
       (4, 'Robin', 'another_robin@gmail.com');


select *
from users;
```

Solutions:

```sql
select max(user_id), user_name, email
from users
group by user_name, email
having count(user_name) > 1 and count(email) > 1
```

Solution from video: Use a window function with `row_number()`.

```sql
with rn_dups as (
  select *, row_number() over(partition by user_name, email order by user_id) as rn
  from users
  order by user_id
)

select user_name, email, max(rn) as nr_of_dups
from rn_dups
where rn > 1
group by user_name, email
```

## 18.2. Exercise 2

```sql
-- Query 2:
-- Write a SQL query to fetch the second record from a employee table.

--Tables Structure:
-- drop table if exists employee;
create table employee
( emp_ID int primary key
, emp_NAME varchar(50) not null
, DEPT_NAME varchar(50)
, SALARY int);

insert into employee values(101, 'Mohan', 'Admin', 4000);
insert into employee values(102, 'Rajkumar', 'HR', 3000);
insert into employee values(103, 'Akbar', 'IT', 4000);
insert into employee values(104, 'Dorvin', 'Finance', 6500);
insert into employee values(105, 'Rohit', 'HR', 3000);
insert into employee values(106, 'Rajesh',  'Finance', 5000);
insert into employee values(107, 'Preet', 'HR', 7000);
insert into employee values(108, 'Maryam', 'Admin', 4000);
insert into employee values(109, 'Sanjay', 'IT', 6500);
insert into employee values(110, 'Vasudha', 'IT', 7000);
insert into employee values(111, 'Melinda', 'IT', 8000);
insert into employee values(112, 'Komal', 'IT', 10000);
insert into employee values(113, 'Gautham', 'Admin', 2000);
insert into employee values(114, 'Manisha', 'HR', 3000);
insert into employee values(115, 'Chandni', 'IT', 4500);
insert into employee values(116, 'Satya', 'Finance', 6500);
insert into employee values(117, 'Adarsh', 'HR', 3500);
insert into employee values(118, 'Tejaswi', 'Finance', 5500);
insert into employee values(119, 'Cory', 'HR', 8000);
insert into employee values(120, 'Monica', 'Admin', 5000);
insert into employee values(121, 'Rosalin', 'IT', 6000);
insert into employee values(122, 'Ibrahim', 'IT', 8000);
insert into employee values(123, 'Vikram', 'IT', 8000);
insert into employee values(124, 'Dheeraj', 'IT', 11000);

select * from employee;
```

Solution:

```sql
with rn as (
	select *, row_number() over(order by emp_id) as rn
	from employee
)

select *
from rn
where rn = 2
```

## 18.3. Exercise 3

```sql
-- Query 3:

-- Write a SQL query to display only the details of employees who either earn the highest salary or the lowest salary in each department from the employee table.

--Tables Structure:

-- drop table if exists employee;
create table employee
( emp_ID int primary key
, emp_NAME varchar(50) not null
, DEPT_NAME varchar(50)
, SALARY int);

insert into employee values(101, 'Mohan', 'Admin', 4000);
insert into employee values(102, 'Rajkumar', 'HR', 3000);
insert into employee values(103, 'Akbar', 'IT', 4000);
insert into employee values(104, 'Dorvin', 'Finance', 6500);
insert into employee values(105, 'Rohit', 'HR', 3000);
insert into employee values(106, 'Rajesh',  'Finance', 5000);
insert into employee values(107, 'Preet', 'HR', 7000);
insert into employee values(108, 'Maryam', 'Admin', 4000);
insert into employee values(109, 'Sanjay', 'IT', 6500);
insert into employee values(110, 'Vasudha', 'IT', 7000);
insert into employee values(111, 'Melinda', 'IT', 8000);
insert into employee values(112, 'Komal', 'IT', 10000);
insert into employee values(113, 'Gautham', 'Admin', 2000);
insert into employee values(114, 'Manisha', 'HR', 3000);
insert into employee values(115, 'Chandni', 'IT', 4500);
insert into employee values(116, 'Satya', 'Finance', 6500);
insert into employee values(117, 'Adarsh', 'HR', 3500);
insert into employee values(118, 'Tejaswi', 'Finance', 5500);
insert into employee values(119, 'Cory', 'HR', 8000);
insert into employee values(120, 'Monica', 'Admin', 5000);
insert into employee values(121, 'Rosalin', 'IT', 6000);
insert into employee values(122, 'Ibrahim', 'IT', 8000);
insert into employee values(123, 'Vikram', 'IT', 8000);
insert into employee values(124, 'Dheeraj', 'IT', 11000);

select * from employee;
```

Solution:

```sql
with max_salary as (
	select dept_name, max(salary)
	from employee
	group by dept_name
), min_salary as (
	select dept_name, min(salary)
	from employee
	group by dept_name
)

select
	e.emp_id, e.emp_name, e.dept_name, e.salary,
	case
		when e.salary = mas.max then 'Highest Salary'
		else 'Lowest Salary'
	end as description
from employee e, max_salary mas, min_salary mis
where
	e.dept_name = mas.dept_name and e.salary = mas.max or
	e.dept_name = mis.dept_name and e.salary = mis.min
order by e.dept_name, salary desc
```

## 18.4. Exercise 4

```sql
-- Query 4:

-- From the doctors table, fetch the details of doctors who work in the same hospital but in different speciality.

--Table Structure:

-- drop table if exists doctors;
create table doctors
(
id int primary key,
name varchar(50) not null,
speciality varchar(100),
hospital varchar(50),
city varchar(50),
consultation_fee int
);

insert into doctors values
(1, 'Dr. Shashank', 'Ayurveda', 'Apollo Hospital', 'Bangalore', 2500),
(2, 'Dr. Abdul', 'Homeopathy', 'Fortis Hospital', 'Bangalore', 2000),
(3, 'Dr. Shwetha', 'Homeopathy', 'KMC Hospital', 'Manipal', 1000),
(4, 'Dr. Murphy', 'Dermatology', 'KMC Hospital', 'Manipal', 1500),
(5, 'Dr. Farhana', 'Physician', 'Gleneagles Hospital', 'Bangalore', 1700),
(6, 'Dr. Maryam', 'Physician', 'Gleneagles Hospital', 'Bangalore', 1500);
```

Solution:

```sql
select d1.id, d1.name, d1.speciality, d1.hospital, d1.city, d1.consultation_fee
from doctors d1 join doctors d2 on d1.hospital = d2.hospital and d1.speciality != d2.speciality
```

## 18.5. Exercise 5

```sql
-- Query 5:

-- From the login_details table, fetch the users who logged in consecutively 3 or more times.

--Table Structure:

-- drop table if exists login_details;
create table login_details(
login_id int primary key,
user_name varchar(50) not null,
login_date date);

delete from login_details;
insert into login_details values
(101, 'Michael', current_date),
(102, 'James', current_date),
(103, 'Stewart', current_date+1),
(104, 'Stewart', current_date+1),
(105, 'Stewart', current_date+1),
(106, 'Jimmy', current_date+2),
(107, 'Michael', current_date+2),
(108, 'Stewart', current_date+3),
(109, 'Stewart', current_date+3),
(110, 'James', current_date+4),
(111, 'James', current_date+4),
(112, 'James', current_date+5),
(113, 'James', current_date+6);
```

Solution:

```sql
with l as (
	select *, lag(user_name) over w as prev_user1, lag(user_name,2) over w as prev_user2
	from login_details
	window w as (order by login_date, login_id)
)

select *
from l
where user_name = prev_user1 and prev_user1 = prev_user2
```

Alternative solution:

```sql
with rep as (
	select
		*,
		case
			when lag(user_name) over (order by login_date) = user_name then 'repeat'
			else 'not repeat'
		end as rep
	from login_details
), cume_rep as (
	select
		*,
		case
			when rep = 'repeat' and lag(rep) over (order by login_date) = rep then 1
			else 0
		end as cume_rep
	from rep
)

select *
from cume_rep
where cume_rep = 1
```

Better alternative solution. This solution also counts the number of consecutive logins by the user.

```sql
with rep as (
	select
		*,
		case
			when lag(user_name) over(order by login_date) = user_name then 1
			else 0
		end as rep
	from login_details
), island_head as (
	select
		*,
		case
			when
				rep = 0 and lead(rep) over(order by login_date) = 1 then login_id
		end as island_head
	from rep
), island_id as(
	select
		*,
		case
			when rep = 1 then max(island_head) over(order by login_date)
			when rep = 0 then island_head
		end as island_id
	from island_head
)

select
	*,
	count(island_id) over(partition by island_id order by login_date rows between unbounded preceding and unbounded following)
from island_id
order by login_date, island_head
```

To make the result set more compact:

```sql
with rep as (
	select
		*,
		case
			when lag(user_name) over(order by login_date) = user_name then 1
			else 0
		end as rep
	from login_details
), island_head as (
	select
		*,
		case
			when
				rep = 0 and lead(rep) over(order by login_date) = 1 then login_id
		end as island_head
	from rep
), island_id as(
	select
		*,
		case
			when rep = 1 then max(island_head) over(order by login_date)
			when rep = 0 then island_head
		end as island_id
	from island_head
), island as(
	select
		*,
		count(island_id) over(partition by island_id order by login_date rows between unbounded preceding and unbounded following) as consecutive_logins
	from island_id
)

select  island_id, consecutive_logins, user_name
from island
where consecutive_logins != 0
group by island_id, consecutive_logins, user_name
order by island_id
```

## 18.6. Exercise 6

```sql
-- Query 6:
-- From the students table, write a SQL query to interchange the adjacent student names.
-- Note: If there are no adjacent student then the student name should stay the same.
--Table Structure:

-- drop table if exists students;
create table students
(
id int primary key,
student_name varchar(50) not null
);
insert into students values
(1, 'James'),
(2, 'Michael'),
(3, 'George'),
(4, 'Stewart'),
(5, 'Robin');

-- select * from students;
```

Solution:

```sql
select
	*,
	case
		when id % 2 = 1 then lead(student_name,1,student_name) over()
		when id % 2 = 0 then lag(student_name,1,student_name) over()
	end as new_student_name
from students
```

## 18.7. Exercise 7

```sql
-- Query 7:
-- From the weather table, fetch all the records when London had extremely cold temperature for 3 consecutive days or more.
-- Note: Weather is considered to be extremely cold then its temperature is less than zero.

--Table Structure:
-- drop table if exists weather;
create table weather
(
id int,
city varchar(50),
temperature int,
day date
);
delete from weather;
insert into weather values
(1, 'London', -1, to_date('2021-01-01','yyyy-mm-dd')),
(2, 'London', -2, to_date('2021-01-02','yyyy-mm-dd')),
(3, 'London', 4, to_date('2021-01-03','yyyy-mm-dd')),
(4, 'London', 1, to_date('2021-01-04','yyyy-mm-dd')),
(5, 'London', -2, to_date('2021-01-05','yyyy-mm-dd')),
(6, 'London', -5, to_date('2021-01-06','yyyy-mm-dd')),
(7, 'London', -7, to_date('2021-01-07','yyyy-mm-dd')),
(8, 'London', 5, to_date('2021-01-08','yyyy-mm-dd'));

-- select * from weather;
```

Solution:

```sql
with
streak as (
  select *,
	case
		when temperature < 0 and lag(temperature) over (order by id) >= 0 then id -- head (does consider first record)
		when temperature < 0 and lead(temperature) over (order by id) < 0 then 1 -- body
		when temperature < 0 and lead(temperature) over (order by id) >= 0 then 1 -- tail
		when temperature < 0 then 1 --handles the last record
	end as streak
  from weather),
island_id as (
	select
		*,
		case
			when streak is not null then max(streak) over(order by id)
		end as island_id
		from streak),
island_size as (
	select
		*,
		count(island_id) over(partition by island_id order by id rows between unbounded preceding and unbounded following) as island_size
	from island_id
)

select id, city, temperature, day, island_size
from island_size
where island_size >= 3
order by id
```

## 18.8. Exercise 9

We skipped exercise 9 because the task was not clear.

```sql
-- Query 9:
-- Find the top 2 accounts with the maximum number of unique patients on a monthly basis.
-- Note: Prefer the account if with the least value in case of same number of unique patients

--Table Structure:

-- drop table if exists patient_logs;
create table patient_logs
(
  account_id int,
  date date,
  patient_id int
);

insert into patient_logs values (1, to_date('02-01-2020','dd-mm-yyyy'), 100);
insert into patient_logs values (1, to_date('27-01-2020','dd-mm-yyyy'), 200);
insert into patient_logs values (2, to_date('01-01-2020','dd-mm-yyyy'), 300);
insert into patient_logs values (2, to_date('21-01-2020','dd-mm-yyyy'), 400);
insert into patient_logs values (2, to_date('21-01-2020','dd-mm-yyyy'), 300);
insert into patient_logs values (2, to_date('01-01-2020','dd-mm-yyyy'), 500);
insert into patient_logs values (3, to_date('20-01-2020','dd-mm-yyyy'), 400);
insert into patient_logs values (1, to_date('04-03-2020','dd-mm-yyyy'), 500);
insert into patient_logs values (3, to_date('20-01-2020','dd-mm-yyyy'), 450);

select * from patient_logs;
```

Solution:

```sql
with dp as
  (select distinct to_char(date, 'month') as month,
                   account_id,
                   patient_id
   from patient_logs
   order by month),
     c as
  (select month,
          account_id,
          count(account_id) as c
   from dp
   group by month, account_id),
     r as
  (select *,
          rank() over(partition by month order by c desc, account_id) as rnk
   from c)
select *
from r
where rnk < 3
order by month, rnk
```

# 19. Misc Notes

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
- [W3 SQL Tutorial](https://www.w3schools.com/sql/default.asp)
- [Full Text Search PostgreSQL](https://www.youtube.com/watch?v=szfUbzsKvtE)
- [Learn PostgreSQL Tutorial - Full Course for Beginners](https://www.youtube.com/watch?v=qw--VYLpxG4)
- [Official Tutorials and Other Resources](https://www.postgresql.org/docs/online-resources/)
- [EDB Offer](https://www.enterprisedb.com/training/free-postgres-training)
- [Tutorials point](https://www.tutorialspoint.com/postgresql/)
- [Show all tables](https://www.postgresqltutorial.com/postgresql-show-tables/):

```sql
SELECT * FROM pg_catalog.pg_tables
WHERE schemaname != 'pg_catalog' AND
      schemaname != 'information_schema';
```

- [A Visual Explanation of SQL Joins](https://blog.codinghorror.com/a-visual-explanation-of-sql-joins/)
- [Join (SQL) Wiki](https://en.wikipedia.org/wiki/Join_(SQL))
- [Table Covert Online](https://tableconvert.com/)
- [Math Symbols List](https://www.rapidtables.com/math/symbols/Basic_Math_Symbols.html)
- [Casting columns to date](https://stackoverflow.com/questions/5875712/postgresql-select-something-where-date-01-01-11)
- [Transpose Results](https://stackoverflow.com/questions/23060256/postgres-transpose-rows-to-columns)
- [Dollar Quoting](https://stackoverflow.com/questions/12144284/what-are-used-for-in-pl-pgsql)
- [Delete duplicate records](https://stackoverflow.com/questions/6583916/delete-duplicate-rows-from-small-table)
- [Creating multiple tables with sqlite3](https://gist.github.com/iampramodyadav/793ec2b0ea71c3bcbfd6deea636907e2)

## 19.1. General Syntax

```sql 
select
	count distinct
from 
where
	=<> 
	is null
	in ()
	between x and y 
	like 
	ilike
group by 
having 
order by 
limit 
```

## 19.2. Misc Notes from Revision

- `not` keyword appears before the condition
- `order by`-columns also appears in `select`-column
- if we `group by` -> `select`-columns appear in:
  - `group by`-statement OR
  - are in an aggregate function
- column in `select` -> column in `group by`
- aggregate function appear in:
  - `select` OR
  - `having`

# 20. Solutions to Codility Exercise

```sql
select distinct(event_type), nth_value(delta, 1) over(partition by event_type) as value
from
	(select e.*, lag(value) over( partition by event_type order by time desc) - value as delta
	from events e
	order by event_type) delta
where delta is not null
order by event_type
```

Alternative (since we remove the null values with the `where` clause and parameter of nth_value is 1):

```sql
select distinct(event_type), first_value(delta) over(partition by event_type) as value
from
	(select e.*, lag(value) over( partition by event_type order by time desc) - value as delta
	from events e
	order by event_type) delta
where delta is not null
order by event_type
```

Alternative with `with` as syntactic convenience to make the query more readable.

```sql
with delta as (
  select e.*, lag(value) over( partition by event_type order by time desc) - value as delta
  from events e
	order by event_type
)

select distinct(event_type), first_value(delta) over(partition by event_type) as value
from delta
where delta is not null
order by event_type
```