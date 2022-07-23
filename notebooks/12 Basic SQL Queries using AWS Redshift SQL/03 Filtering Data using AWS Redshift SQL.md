```sql
SELECT *
FROM retail_db.orders
WHERE order_status = 'COMPLETE'
LIMIT 10;

SELECT count(*)
FROM retail_db.orders
WHERE order_status = 'COMPLETE';

SELECT *
FROM retail_db.orders
WHERE order_status = 'COMPLETE' 
	AND order_date = '2014-01-01 00:00:00.0'
LIMIT 10;

SELECT count(*)
FROM retail_db.orders
WHERE order_status = 'COMPLETE' 
	AND order_date = '2014-01-01 00:00:00.0';

SELECT *
FROM retail_db.orders
WHERE order_status = 'COMPLETE' 
	AND order_date LIKE '2014-01%'
LIMIT 10;

SELECT count(*)
FROM retail_db.orders
WHERE order_status = 'COMPLETE' 
	AND order_date LIKE '2014-01%';

-- Get orders which are either in COMPLETE or CLOSED Status

SELECT *
FROM retail_db.orders
WHERE order_status IN ('COMPLETE', 'CLOSED')
LIMIT 10;

SELECT count(*)
FROM retail_db.orders
WHERE order_status IN ('COMPLETE', 'CLOSED');

SELECT count(*)
FROM retail_db.orders
WHERE order_status IN ('COMPLETE', 'CLOSED')
	AND order_date LIKE '2014-01%';
```