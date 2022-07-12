```sql
SELECT count(*) FROM retail_db.orders;

SELECT * FROM retail_db.orders LIMIT 10;

SELECT count(distinct order_date),
	count(distinct order_status)
FROM retail_db.orders;

SELECT count(*) FROM retail_db.order_items;

SELECT * 
FROM retail_db.order_items 
LIMIT 10;

SELECT sum(order_item_subtotal)
FROM retail_db.order_items
WHERE order_item_order_id = 2;

SELECT round(sum(order_item_subtotal), 2)
FROM retail_db.order_items
WHERE order_item_order_id = 2;

SELECT count(*) item_count,
	round(sum(order_item_subtotal), 2) total_revenue,
    round(avg(order_item_subtotal), 2) avg_revenue
FROM retail_db.order_items
WHERE order_item_order_id = 2;
```