```sql
SELECT *
FROM retail_db.orders
LIMIT 10;

SELECT *
FROM retail_db.order_items
LIMIT 10;

-- Make sure to switch to retail_dm database

CREATE EXTERNAL SCHEMA IF NOT EXISTS retail_db
FROM DATA CATALOG
DATABASE 'retail_db'
IAM_ROLE 'arn:aws:iam::269066542444:role/AIRedshiftRetailSpectrum'
CREATE EXTERNAL DATABASE IF NOT EXISTS;

CREATE TABLE public.daily_product_revenue
AS
SELECT o.order_date,
    oi.order_item_product_id,
    round(sum(oi.order_item_subtotal), 2) AS product_revenue
FROM retail_db.orders AS o
    JOIN retail_db.order_items AS oi
        ON o.order_id = oi.order_item_order_id
WHERE o.order_status IN ('COMPLETE', 'CLOSED')
GROUP BY o.order_date,
    oi.order_item_product_id;
```