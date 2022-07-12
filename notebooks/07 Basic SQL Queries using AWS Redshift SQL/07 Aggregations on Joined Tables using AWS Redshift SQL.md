```sql
SELECT *
FROM retail_db.orders
LIMIT 10;

SELECT *
FROM retail_db.order_items
LIMIT 10;

SELECT o.*,
	count(*) AS order_item_count,
    round(sum(oi.order_item_subtotal), 2) AS order_revenue
FROM retail_db.orders AS o
	JOIN retail_db.order_items AS oi
    	ON o.order_id = oi.order_item_order_id
WHERE o.order_status IN ('COMPLETE', 'CLOSED')
GROUP BY o.order_id,
    o.order_date,
    o.order_customer_id,
    o.order_status
ORDER BY 1
LIMIT 10;

SELECT o.*,
	count(*) AS order_item_count,
    round(sum(oi.order_item_subtotal), 2) AS order_revenue
FROM retail_db.orders AS o
	JOIN retail_db.order_items AS oi
    	ON o.order_id = oi.order_item_order_id
WHERE o.order_status IN ('COMPLETE', 'CLOSED')
GROUP BY o.order_id,
    o.order_date,
    o.order_customer_id,
    o.order_status
	HAVING order_revenue >= 1000
ORDER BY 1
LIMIT 10;
```