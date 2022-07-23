```sql
SELECT * 
FROM retail_db.orders 
LIMIT 10;

SELECT order_status,
	count(*) AS order_count
FROM retail_db.orders
GROUP BY order_status
ORDER BY order_status;

SELECT * 
FROM retail_db.order_items
LIMIT 10;

SELECT order_item_order_id,
	round(sum(order_item_subtotal), 2) AS order_revenue
FROM retail_db.order_items
GROUP BY order_item_order_id
ORDER BY order_item_order_id
LIMIT 10;

SELECT order_item_order_id,
	round(sum(order_item_subtotal), 2) AS order_revenue
FROM retail_db.order_items
GROUP BY order_item_order_id
	HAVING round(sum(order_item_subtotal), 2) > 1000
ORDER BY order_item_order_id
LIMIT 10;
```