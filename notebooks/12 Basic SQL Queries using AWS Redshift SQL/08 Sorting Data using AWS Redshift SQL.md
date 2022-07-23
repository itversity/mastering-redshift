```sql
SELECT * 
FROM retail_db.order_items
LIMIT 10;

SELECT * 
FROM retail_db.order_items
ORDER BY order_item_order_id, 
	order_item_subtotal
LIMIT 10;

SELECT * 
FROM retail_db.order_items
ORDER BY 2, 5
LIMIT 10;

SELECT * 
FROM retail_db.order_items
ORDER BY order_item_order_id, 
	order_item_subtotal DESC
LIMIT 10;

SELECT * 
FROM retail_db.order_items
ORDER BY 2, 5 DESC
LIMIT 10;

SELECT o.order_date,
	oi.order_item_product_id,
	count(DISTINCT o.order_id) AS order_count,
    round(sum(oi.order_item_subtotal), 2) AS order_revenue
FROM retail_db.orders AS o
	JOIN retail_db.order_items AS oi
    	ON o.order_id = oi.order_item_order_id
WHERE o.order_status IN ('COMPLETE', 'CLOSED')
GROUP BY o.order_date,
	oi.order_item_product_id
ORDER BY 1, 4 DESC
LIMIT 10;
```