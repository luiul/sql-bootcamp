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
- [5. GROUP BY Statements & Aggregate Functions](#5-group-by-statements--aggregate-functions)
  - [5.1. Aggregation Functions - AVG, COUNT, MAX, MIN and SUM](#51-aggregation-functions---avg-count-max-min-and-sum)
  - [5.2. GROUP BY Statement](#52-group-by-statement)
  - [5.3. HAVING Clause](#53-having-clause)
- [6. Assessment Test 1](#6-assessment-test-1)
- [7. JOIN Clause](#7-join-clause)
  - [7.1. Aliases: AS Clause](#71-aliases-as-clause)
  - [7.2. INNER JOIN Keyword (Intersection)](#72-inner-join-keyword-intersection)
  - [7.3. FULL (OUTER) JOIN Keyword (Union and Symmetric Difference)](#73-full-outer-join-keyword-union-and-symmetric-difference)
  - [7.4. LEFT (OUTER) JOIN Keyword (A)](#74-left-outer-join-keyword-a)
  - [7.5. RIGHT (OUTER) JOIN Keyword (B)](#75-right-outer-join-keyword-b)
  - [7.6. UNION Operator](#76-union-operator)
  - [7.7. JOIN Challenges](#77-join-challenges)
- [8. Advanced SQL Commands](#8-advanced-sql-commands)
  - [8.1. Timestamps and Extract](#81-timestamps-and-extract)
    - [8.1.1. Displaying Current Time Information](#811-displaying-current-time-information)
    - [8.1.2. Extracting Time and Date Information](#812-extracting-time-and-date-information)
- [9. Misc](#9-misc)

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

## 5.2. GROUP BY Statement

The `group by` statement allows us to aggregate columns per some category. We need to choose a categorical column to `group by`. Categorical columns are non-continuous. Keep in mind, they can still be numerical, such as cabin class categories on a ship (e.g. Class 1, Class 2, Class 3)

After choosing the categorical column we're essentially **splitting** the table up on a per category basis in n subtables. We can then **aggregate** the columns in the subtables with an aggregate function. Basic syntax:

```sql
select cat_col, "agg"(data_col) from t1
where cat_col != 'A'
group by cat_col
-- "agg" is a placeholder for some aggregate function
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

We can also add a `where` statement to the query. `where` statements should not refer to the aggregation result. Later on we'll use the `having` clause to filter on those results. The `having` clause was added to SQL because the `where` keyword cannot be used with aggregate functions. Example:

```sql
select company, division, sum(sales)
from finance_table
where division in ('marketing', 'transport')
-- where cannot be used with aggregate function
group by company, division
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

We want to find out what customer spent the most money:

```sql
select customer_id, sum(amount) from payment
group by customer_id
order by sum(amount) desc
-- this can be read as total sum amount per customer id
```

We want to find out how many transaction occurred per customer:

```sql
select customer_id, count(amount) from payment
group by customer_id
order by count(amount) desc
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

**Challenge**: We have two staff members, with Staff IDs 1 and 2. We want to give a bonus to the staff member that handled the most payments. (Most in terms of number of payments processed, not total dollar amount). How many payments did each staff member handle and who gets the bonus?

```sql
select staff_id, count(payment_id) from payment
group by staff_id
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
select staff_id, customer_id, sum(amount)
from payment
where staff_id = 2
group by staff_id, customer_id
having sum(amount) > 100
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

## 7.2. INNER JOIN Keyword (Intersection)

JOINs allow us to combine multiple tables together. The main reason for the different JOIN types is to decide how to deal with information only present in **one** of the joined tables.

The `inner join` keyword selects records that have matching values in both tables. Basis syntax:

```sql
select order.order_id, customer.first_name
from order
-- from customer
inner join customer on order.customer_id = customer.customer_id
-- in this syntax, the INNER keyword is optional
-- inner join order ... 
-- the inner join is symmetrical: the order of the tables does not matter
```

**Result**:

| set      | id_A | id_B |
|---------|------|------|
| A ∩ B | ...  | ...  |

If we just use `join` without the `inner`, PgSQL will treat it as an `inner join`.

Example: we want to join the payment and customer table.

```sql
select payment.payment_id, payment.customer_id, customer.email
from payment
inner join customer on payment.customer_id = customer.customer_id
-- this shows only customer that have done a payment
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

| set     | id_A | id_B |
|---------|------|------|
| A ∩ B | ...  | ...  |
| A \ B   | ...  | NULL |
| B \ A   | NULL | ...  |

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

| set     | id_A | id_B |
|---------|------|------|
| A \ B   | ...  | NULL |
| B \ A   | NULL | ...  |

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
|-------|------|------|
| A ∩ B | ...  | ...  |
| A     | ...  | NULL |

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

| set   | id_A | id_B |
|-------|------|------|
| A     | ...  | NULL |

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
|-------|------|------|
| A ∩ B | ...  | ...  |
| B     | NULL  | ... |

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

| set   | id_A | id_B |
|-------|------|------|
| B     | NULL  | ... |

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
|---------|---------|
| A.col_1 | A.col_2 |
| B.col_2 | B.col_2 |

## 7.7. JOIN Challenges

**Challenge**: California sales tax laws have changed and we need to alert our customers to this through email. What are the emails of the customers who live in California?

```sql
-- task: what are the emails of the customers that live in California
-- California is a district in the address table

select customer.first_name, customer.last_name, customer.email, address.district
from customer
right join address on customer.address_id = address.address_id
where address.district = 'California'

-- this query returns the same information if we perform an inner join; we perform a right join to make sure that there is no person in California that does not have an email in the database
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

# 8. Advanced SQL Commands

Section Overview:

- Timestamps and EXTRACT
- Math Functions
- String Functions
- Sub-query
- Self-Join

## 8.1. Timestamps and Extract

### 8.1.1. Displaying Current Time Information

In Part One, we will go over a few commands that report back time and date information. These will be more useful when creating our own tables and databases, rather than when querying a database.

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
-- show all
-- show timezone
-- show runtime parameters

-- select now()
-- return timestamp

-- select timeofday()
-- return string representation of timestamp

-- select current_time
-- return time with timezone

-- select current_date
-- return date

```

### 8.1.2. Extracting Time and Date Information

Let's explore extracting information from a time based data type using:

- `extract()`
- `age()`
- `to_char()`

`extract(field FROM source)` allows you to "extract" or obtain a sub-component of a date value. Valid values for field can be found in the [documentation](https://www.postgresql.org/docs/13/functions-datetime.html).

Syntax:

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

# 9. Misc

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
