## Run Copy Command to copy from s3 to Redshift table

Here are the commands to create table and also to copy data from files in AWS S3 into Redshift Database Table using Redshift COPY Command.

```sql
DROP TABLE IF EXISTS orders;
CREATE TABLE orders (
  order_id INT PRIMARY KEY,
  order_date DATETIME,
  order_customer_id INT,
  order_status VARCHAR(30)
);

COPY orders FROM 's3://itv-retail/retail_db/orders/part-00000' 
CREDENTIALS 'aws_access_key_id=<YOUR_ACCESS_KEY>;aws_secret_access_key=<YOUR_SECRET_KEY>'
CSV;
```