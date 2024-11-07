# Databases

- [x] Introduction to database
- [x] intro to mysql engines
- [x] What is mysql?
- [x] basic queries - create db, table
- [x] insert, update, alter
- [x] select - where clause, distinct
- [x] groupby, order, offset, limit
- [x] Normalization, select queries
- [x] Joins, subqueries
- [x] Pros and Cons of relational databases
- [x] DB model design
- [x] Relational Database Vs Non Relational Database

## Introduction to database

- Database is a collection of data stored in a computer system.
- Data can be stored in the form of tables or objects.
- Data stored in the form of tables is called structured or relational data.
- Data stored in the form of objects is called unstructured data.

## Intro to DB Engines

- Database engines are database management systems that are used to manage the data stored in the database.
- There are different types of database engines available in the market.
  - SQL Engines: MySQL, PostgreSQL, Oracle, Microsoft SQL Server
  - NoSQL Engines: MongoDB, CouchDB, Cassandra, Redis
  - Embedded Engines: SQLite, H2

## Intro to Mysql Engines

- MySQL is an open-source relational database management system.
- It is one of the most popular database engines in the world.
- MySQL is used to store and manage data in the form of tables.

## What is SQL?

- SQL stands for Structured Query Language.
- It is a standard language used to interact with the database.
- SQL is used to create, read, update, and delete data in the database.
- SQL is categorized into:
  - DDL (Data Definition Language): CREATE, ALTER, DROP
  - DML (Data Manipulation Language): INSERT, UPDATE, DELETE
  - DQL (Data Query Language): SELECT
  - DCL (Data Control Language): GRANT, REVOKE
  - DTL (Data Transaction Language): COMMIT, ROLLBACK

## Basic Queries

### Show Existing Databases

```sql
SHOW DATABASES;
```

### Show Version of MySQL

```sql
SELECT VERSION();
```

### Show Current Date and Time

```sql
SELECT NOW();
```

### To view the currently selected database

```sql
SELECT DATABASE();
```

### Create a Database

```sql
CREATE DATABASE ECommerce
```

### Use a Database

```sql
USE Ecommerce;
```

### Drop a Database

```sql
DROP DATABASE Ecommerce;
```

### Show Tables in a Database

```sql
SHOW TABLES;
```
Sample Tables:

Customers Table:

+------+---------------+--------------------------+-----------------------------------+
| id   | name          | email                    | address                           |
+------+---------------+--------------------------+-----------------------------------+
|    1 | John Smith    | john.smith@gmail.com     | 7, laker street Washington USA    |
|    2 | Jane Doe      | jane.doe@gmail.com       | 3 , wilson street Toronto CA      |
|    3 | Glenn Gould   | glenn.gould@gmail.com    | 5, park street New York USA       |
|    4 | Kim Vissette  | kim.vissette@outlook.com | 8, lobstone street London UK      |
|    5 | Tim Wood      | timwood007@outlook.com   | 10, savepoint street New York USA |
|    6 | Clara Miller  | claram@gmail.com         | 17, nasher lane Detroit USA       |
|    7 | Jennifer Louw | jennilouw08@gmail.com    | 23, MDC street Morrisvile USA     |
|    8 | David Ruiz    | davidruiz@gmail.com      | 15, maintain street New York USA  |
|    9 | Sarah Lee     | sarahlee@gmail.com       | 21, will street Cincinnati USA    |
|   10 | Michael Brown | michaelbrown@gmail.com   | 22, loker street Berlin Germany   |
|   11 | David Lee     | davidlee@rediff.com      | 23, paker street Ipswich UK       |
|   12 | John Brown    | johnbrown@gmail.com      | 24, kerkero street Kimberley SA   |
+------+---------------+--------------------------+-----------------------------------+


### Create a Table

```sql
CREATE TABLE customers (
    id INT,
    name CHAR(100),
    email CHAR(100),
    address CHAR(255)
);

CREATE TABLE products (
    id INT,
    name CHAR(100),
    price DECIMAL(10, 2),
    description TEXT
);

CREATE TABLE orders (
    id INT,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10, 2),
);
```

### Describe a Table

```sql
DESCRIBE ECommerce;
```

or

```sql
desc ECommerce;
```

### Add Primary Key separately after creating a table

```sql
ALTER TABLE ECommerce ADD PRIMARY KEY (id);
```

### Insert Data into a Table

```sql
INSERT INTO ECommerce (id, name, email, address) VALUES
(1, 'John Smith', 'john.smith@gmail.com', '7, laker street Washington USA');
(2, 'Jane Doe', 'jane.doe@gmail.com', '3 , wilson street Toronto CA');
(3, 'Glenn Gould', 'glenn.gould@gmail.com', '5, park street New York USA');
(4, 'Kim Vissette', 'kim.vissette@outlook.com', '8, lobstone street London UK');
(5, 'Tim Wood', 'timwood007@outlook.com', '10, savepoint street New York USA');
(6, 'Clara Miller', 'claram@gmail.com', '17, nasher lane Detroit USA');
(7, 'Jennifer Louw', 'jennilouw08@gmail.com', '23, MDC street Morrisvile USA');
(8, 'David Ruiz', 'davidruiz@gmail.com', '15, maintain street New York USA');
(9, 'Sarah Lee', 'sarahlee@gmail.com', '21, will street Cincinnati USA');
(10, 'Michael Brown', 'michaelbrown@gmail.com', '22, loker street Berlin Germany');
(11, 'David Lee', 'davidlee@rediff.com', '23, paker street Ipswich UK');
(12, 'John Brown', 'johnbrown@gmail.com', '24, kerkero street Kimberley SA');

```

### Delete all rows from a table

```sql
DELETE FROM ECommerce;
```

or

```sql
TRUNCATE TABLE ECommerce;
```

### View all rows and all columns from a table

```sql
SELECT * FROM ECommerce;
```

### To select specific columns from a table

```sql
SELECT id, name FROM ECommerce;
```

### To select specific rows from a table

```sql
SELECT * FROM ECommerce WHERE id = 1;
```

More Examples:

```sql
SELECT * FROM products WHERE price > 10000;
SELECT * FROM products WHERE price BETWEEN 1000 AND 5000;
SELECT * FROM products WHERE name LIKE 'L%';
SELECT * FROM products WHERE name LIKE '%e';
SELECT * FROM products WHERE name LIKE '%e%';
select * from products where name like 'L%' and price > 10000;
select * from products where name like 'L%' or price > 10000;
```

### Char Vs Varchar:

- CHAR is fixed length and VARCHAR is variable length.
- CHAR is faster than VARCHAR.
- CHAR is used when the length of the column is fixed.
- VARCHAR is used when the length of the column is variable.

### Update Data in a Table

```sql
UPDATE products SET price = 60000 WHERE id = 1;
```

### Add a Column to a Table

```sql
ALTER TABLE products ADD description TEXT;
```

### Update Data in a Table

```sql
UPDATE products SET description = 'This is a laptop' WHERE id = 1;
```

### Delete a Column from a Table

```sql
ALTER TABLE products DROP description;
```

### Delete Data from a Table

```sql
DELETE FROM products WHERE id = 1;
```

### products table with multiple product name entries and their prices

Products table

+------+-------------------+----------+-----------------------------------------+
| id   | name              | price    | description                             |
+------+-------------------+----------+-----------------------------------------+
|    1 | Apple Watch       |   800.00 | includes the fitness information        |
|    2 | Samsung QLED      | 12000.00 | Watching the TV favourites with HQ      |
|    3 | Sony Headphones   |   800.00 | listening to the music                  |
|    4 | iPhone            | 15000.00 | includes the camera and phone           |
|    5 | Dell Laptop       | 45000.00 | includes the portable than PC           |
|    6 | Sony Camera       |  6900.00 | includes the taking the pictures        |
|    7 | Apple AirPods     |  1200.00 | listening to the music                  |
|    8 | Samsung flip12    | 25000.00 | includes the fliping the phone          |
|    9 | Redmi Note R18    | 13000.00 | includes the smartphone like android    |
|   10 | Sony BRAVIA       | 35000.00 | includes the watching the TV favourites |
|   11 | Samsung Galaxy S7 | 23000.00 | includes the smartphone like android    |
|   12 | TCL Vitro 4K      | 29000.00 | includes the watching the TV            |
+------+-------------------+----------+-----------------------------------------+

### insert query for the above table

```sql
INSERT INTO products (id, name, price, description) VALUES
(1, 'Apple Watch', 800.00, 'includes the fitness information'),
(2, 'Samsung QLED', 12000.00, 'Watching the TV favourites with HQ'),
(3, 'Sony Headphones', 800.00, 'listening to the music'),
(4, 'iPhone 13', 15000.00, 'includes the camera and phone'),
(5, 'Dell Laptop', 45000.00, 'includes the portable than PC'),
(6, 'Sony Camera', 6900.00, 'includes the taking the pictures'),
(7, 'Apple AirPods', 1200.00, 'listening to the music'),
(8, 'Samsung flip12', 25000.00, 'includes the fliping the phone'),
(9, 'Redmi Note R18', 13000.00, 'includes the smartphone like android'),
(10, 'Sony BRAVIA', 35000.00, 'includes the watching the TV favourites'),
(11, 'Samsung Galaxy S7', 23000.00, 'includes the smartphone like android'),
(12, 'TCL Vitro 4K', 29000.00, 'includes the watching the TV');
```

### Create a order table like customer_id and order Date

+------+-------------+------------+--------------+
| id   | customer_id | order_date | total_amount |
+------+-------------+------------+--------------+
| NULL |           1 | 2024-11-07 |        60.00 |
| NULL |           2 | 2024-11-02 |        80.00 |
| NULL |           3 | 2024-09-28 |        45.00 |
| NULL |           4 | 2024-10-28 |       120.00 |
| NULL |           5 | 2024-10-23 |       100.00 |
| NULL |           6 | 2024-10-18 |        75.00 |
| NULL |           7 | 2024-10-13 |        95.00 |
| NULL |           8 | 2024-10-08 |       130.00 |
| NULL |           9 | 2024-10-03 |        60.00 |
| NULL |          10 | 2024-09-23 |       110.00 |
+------+-------------+------------+--------------+


### insert query for the above table

```sql
INSERT INTO orders (customer_id, order_date, total_amount)
VALUES 
    (1, CURDATE(), 60.00),
    (2, CURDATE() - INTERVAL 5 DAY, 80.00),
    (3, CURDATE() - INTERVAL 40 DAY, 45.00),
    (4, CURDATE() - INTERVAL 10 DAY, 120.00),
    (5, CURDATE() - INTERVAL 15 DAY, 100.00),
    (6, CURDATE() - INTERVAL 20 DAY, 75.00),
    (7, CURDATE() - INTERVAL 25 DAY, 95.00),
    (8, CURDATE() - INTERVAL 30 DAY, 130.00),
    (9, CURDATE() - INTERVAL 35 DAY, 60.00),
    (10, CURDATE() - INTERVAL 45 DAY, 110.00);
```


### Retrieve all customers who have placed an order in the last 30 days

```sql
SELECT DISTINCT c.*
FROM customers c
JOIN orders o ON c.id = o.customer_id
WHERE o.order_date >= CURDATE() - INTERVAL 30 DAY;
```

### Get the total amount of all orders placed by each customer

```sql
SELECT customer_id, SUM(total_amount) AS total_spent
FROM orders
GROUP BY customer_id;
```


### Update the price of Product C to 45.00

```sql
UPDATE products
SET price = 745.00
WHERE name = 'Sony Camera';
```


### Add a new column discount to the products 

```sql
SELECT * 
FROM products
ORDER BY price DESC
LIMIT 3;
```


### Get the names of customers who have ordered Dell Laptop

```sql
SELECT DISTINCT c.name
FROM customers c
JOIN orders o ON c.id = o.customer_id
JOIN order_items oi ON o.id = oi.order_id
JOIN products p ON oi.product_id = p.id
WHERE p.name = 'Dell Laptop';
```


### Join the orders and customers tables to retrieve the customer's name and order date for each order

```sql
SELECT c.name, o.order_date
FROM orders o
JOIN customers c ON o.customer_id = c.id;
```


### Retrieve the orders with a total amount greater than 150.00

```sql
SELECT * 
FROM orders
WHERE total_amount > 150.00;
```


### Normalize the database by creating a separate table for order_items and updating the orders table

```sql
CREATE TABLE order_items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
-- Remove total_amount column from orders table
ALTER TABLE orders DROP COLUMN total_amount;
```


### Retrieve the average total of all orders

```sql
SELECT AVG(oi.quantity * p.price) AS average_order_total
FROM orders o
JOIN order_items oi ON o.id = oi.order_id
JOIN products p ON oi.product_id = p.id;
```