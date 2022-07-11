## Create Database and Table for Redshift Copy Command

Here are the commands that are used to create database and table in Redshift Cluster which will eventually be used to demonstrate Redshift COPY Command.


```sql
CREATE DATABASE retail_db;

DROP TABLE IF EXISTS orders;
CREATE TABLE orders (
  order_id INT,
  order_date DATE,
  order_customer_id INT,
  order_status VARCHAR(30)
);
```