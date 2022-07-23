```sql
SELECT *
FROM retail_db.orders
LIMIT 10;

SELECT *
FROM retail_db.order_items
LIMIT 10;

SELECT count(*)
FROM retail_db.orders;

SELECT count(*)
FROM retail_db.order_items;

SELECT *
FROM retail_db.orders AS o
	JOIN retail_db.order_items AS oi
    	ON o.order_id = oi.order_item_order_id
LIMIT 10;

SELECT count(*)
FROM retail_db.orders AS o
	JOIN retail_db.order_items AS oi
    	ON o.order_id = oi.order_item_order_id;

SELECT count(*)
FROM retail_db.products;

SELECT count(DISTINCT order_item_product_id)
FROM retail_db.orders AS o
	JOIN retail_db.order_items AS oi
    	ON o.order_id = oi.order_item_order_id
        	AND o.order_date LIKE '2014-01%';

-- Number of products which are not sold for the entire month of January 2014

SELECT count(*)
FROM retail_db.orders AS o
	JOIN retail_db.order_items AS oi
    	ON o.order_id = oi.order_item_order_id
        	AND o.order_date LIKE '2014-01%'
    RIGHT OUTER JOIN retail_db.products p
    	ON p.product_id = oi.order_item_product_id
WHERE oi.order_item_product_id IS NULL;
```