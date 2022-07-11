## Copy Data from s3 to Redshift table using IAM Role

Here are the commands to recreate the Redshift Database Table and also copy data from files in AWS s3 into Redshift Table using IAM Role.

```sql
DROP TABLE IF EXISTS order_items;
CREATE TABLE order_items (
  order_item_id INT PRIMARY KEY,
  order_item_order_id INT,
  order_item_product_id INT,
  order_item_quantity INT,
  order_item_subtotal FLOAT,
  order_item_product_price FLOAT
);

COPY order_items FROM 's3://itv-retail/retail_db/order_items/part-00000' 
IAM_ROLE 'arn:aws:iam::582845781536:role/ITVRedshiftS3FullAccessRole'
DELIMITER ','

SELECT * FROM order_items LIMIT 10

SELECT count(*) FROM order_items
```