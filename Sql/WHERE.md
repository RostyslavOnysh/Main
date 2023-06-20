#  WHERE statement is used in SQL to filter data based on specified conditions. It allows you to retrieve rows from a table that satisfy a particular criterion. The WHERE clause is typically used in conjunction with the SELECT statement, but it can also be used with other statements like UPDATE and DELETE. Here's the basic syntax of the WHERE statement:

```sql

SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
In this syntax:

SELECT: Specifies the columns you want to retrieve.
column1, column2, ...: The names of the columns you want to select.
FROM: Indicates the table from which you want to retrieve the data.
table_name: The name of the table from which you want to retrieve the data.
WHERE: Specifies the condition for filtering the data.
condition: The condition that determines which rows to include in the result.
The condition can be constructed using comparison operators (such as "=", "<>", "<", ">", "<=", ">=") and logical operators (such as "AND", "OR", "NOT"). Here are some examples to illustrate the usage of the WHERE statement:

Example 1: Retrieving rows that meet a specific condition

```sql
SELECT * FROM employees
WHERE salary > 50000;
```
This query selects all columns from the employees table where the salary is greater than 50000. It will return all rows where the salary meets the specified condition.

Example 2: Filtering based on multiple conditions

```sql
SELECT * FROM orders
WHERE order_date >= '2023-01-01' AND total_amount > 1000;
```
This query selects all columns from the orders table where the order_date is on or after January 1, 2023, and the total_amount is greater than 1000.

Example 3: Combining conditions with logical operators

```sql
SELECT * FROM customers
WHERE (city = 'New York' OR city = 'Los Angeles') AND status = 'Active';
```
This query selects all columns from the customers table where the city is either "New York" or "Los Angeles" and the status is "Active". The conditions are combined using the logical operators "OR" and "AND".

Example 4: Using wildcard characters

```sql
SELECT * FROM products
WHERE product_name LIKE '%apple%';
```
This query selects all columns from the products table where the product_name contains the word "apple". The '%' wildcard character is used to match any sequence of characters before or after the keyword "apple".

These examples demonstrate how the WHERE statement allows you to filter data based on specific conditions, providing flexibility in retrieving only the rows that meet your criteria.
