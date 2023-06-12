# Relational SQL

This is a guide to the fundamentals of Relational SQL in all of its varied forms.

## Introduction

SQL, or Structured Query Language, is a programming language designed for
managing data in relational database management systems (RDBMS). It's easy to
use and as the most widely used database language in the world is a key tool in
the data engineers toolbox.

SQL is a powerful and versatile language that can be used for a variety of tasks,
including:

- Creating and managing databases
- Inserting, updating, and deleting data from databases
- Retrieving data from databases
- Sorting and filtering data
- Joining tables
- Creating views
- Creating stored procedures
- Granting and revoking permissions

## Join Types

In SQL, a join is a clause used to combine data from two or more tables. There
are four main types of joins: inner join, outer join, cross join, and self join.

### Inner join

An inner join is the most common type of join. It returns all rows from the
left table that have matching rows in the right table. The matching rows are
determined by the join condition, which is an expression that compares values
in the two tables.

```sql
SELECT *
FROM customers
INNER JOIN orders
ON customers.customer_id = orders.customer_id;
```

This query will return all rows from the customers table that have matching rows
in the orders table. The * in the SELECT clause means to return all columns from
both tables.

### Outer join

An outer join returns all rows from the a table, including rows that do not
have matching rows in the second table. Any columns from the second table that
do not have a matching row will have NULL values for the columns from.

There are two types of outer joins: left outer join and right outer join. Outer
joins are almost always left.

Left outer join: Returns all rows from the left table, and the matching rows
from the right table.
Right outer join: Returns all rows from the right table, and the matching rows
from the left table.

```sql
SELECT *
FROM customers
LEFT OUTER JOIN orders
ON customers.customer_id = orders.customer_id;
```

This query will return all rows from the customers table, including rows that
do not have matching rows in the orders table. The rows in the customers table
that do not have matching rows in the orders table will have NULL values for
the columns from the orders table.

```sql
SELECT *
FROM orders
RIGHT OUTER JOIN customers
ON orders.customer_id = customers.customer_id;
```

This query will return all rows from the orders table, including rows that do
not have matching rows in the customers table. The rows in the orders table that
do not have matching rows in the customers table will have NULL values for the
columns from the customers table.

### Cross join

A cross join returns all possible combinations of rows from the left table and
the right table. This means that the cross join will return all rows from the
customers table, and then for each row in the customers table, it will return
all rows in the orders table.

```sql
SELECT *
FROM customers
CROSS JOIN orders;
```

This query will return all possible combinations of rows from the customers table
and the orders table.

### Self join

A self join is a join that joins a table to itself. This is useful for finding
relationships between rows in the same table.

```sql
SELECT *
FROM customers
INNER JOIN customers AS c2
ON customers.customer_id = c2.customer_id;
```

This query will return all rows from the customers table, and for each row, it
will also return all rows from the customers table where the customer ID is
different. This is useful for finding relationships between rows in the same table.

## Aggregation

In SQL, aggregation is the process of summarizing data from a group of rows into
a single value. This is done using aggregate functions, which are functions that
operate on a set of values and return a single value.

Some common aggregate functions include:

- COUNT: Returns the number of rows in a group.
- SUM: Returns the sum of the values in a group.
- AVG: Returns the average of the values in a group.
- MIN: Returns the minimum value in a group.
- MAX: Returns the maximum value in a group.

Aggregate functions can be used in the SELECT clause of a SQL query to return
aggregated data. For example, the following query returns the number of customers
in each country:

```sql
SELECT country, COUNT(*) AS num_customers
FROM customers
GROUP BY country;
```

The `COUNT(*)` aggregate function returns the number of rows in each group, and
the `GROUP BY` clause groups the rows by the `country` column. This query will
return a table with two columns: `country` and `num_customers`.

Aggregate functions can also be used with the WHERE clause of a SQL query to filter
rows before they are aggregated. For example, the following query returns the
average price of products that have been sold after `2022-01-01`:

```sql
SELECT AVG(price) AS avg_price
FROM products
WHERE sold_date > '2022-01-01';
```

The `AVG(price)` aggregate function returns the average price of products that
have been sold in the period, and the `WHERE` clause filters the rows to only
include products that have been sold in the last year.

Aggregation is a powerful tool that can be used to summarize data from a database.
By using aggregate functions, you can quickly and easily get insights into your data.

## Security

### Database Permissions

In a relational database management system (RDMS), access and roles work by
defining permissions for users and groups of users. These permissions determine
what users can do with the data in the database, such as read, write, or delete.
Access and roles are an important part of database security. By using access and
roles, you can control who can access your data and what they can do with it.
This helps to protect your data from unauthorized access and malicious attacks.

Permissions are assigned to users and groups of users through roles. A role is a
collection of permissions that can be assigned to users. Roles make it easy to
manage permissions for large numbers of users. For example, a role called
"administrator" might have the permissions to create, drop, read, write, and
delete tables. A user could be assigned the "administrator" role to give them
all of these permissions. Permissions should always be managed using roles.

When a user tries to access a database object, the database checks the user's
permissions to see if they are allowed to access the object. If the user does
not have the required permissions, the database will deny access.

Each RDMS have their own defined access and roles eg.

- A user with the "read" permission for a table can view the data in the table.
- A user with the "write" permission for a table can add, update, or delete data
in the table.
- A user with the "delete" permission for a table can delete the table.
- A user with the "create" permission for a table can create a new table.
- A user with the "drop" permission for a table can delete a table.
