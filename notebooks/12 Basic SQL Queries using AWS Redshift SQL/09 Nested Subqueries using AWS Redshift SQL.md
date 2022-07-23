```sql
SELECT * FROM retail_db.customers
WHERE customer_id NOT IN (
    SELECT order_customer_id FROM
    retail_db.orders
)
ORDER BY 1
LIMIT 10;

SELECT count(*) FROM retail_db.customers
WHERE customer_id NOT IN (
    SELECT order_customer_id FROM
    retail_db.orders
);

SELECT count(*) FROM retail_db.customers AS c
WHERE customer_id NOT IN (
    SELECT order_customer_id FROM
    retail_db.orders AS o
    WHERE c.customer_id = o.order_customer_id
);

SELECT * 
FROM retail_db.customers AS c
WHERE NOT EXISTS (
    SELECT 1 
    FROM retail_db.orders AS o
    WHERE c.customer_id = o.order_customer_id
)
ORDER BY 1
LIMIT 10;

SELECT count(*) 
FROM retail_db.customers AS c
WHERE NOT EXISTS (
    SELECT 1 
    FROM retail_db.orders AS o
    WHERE c.customer_id = o.order_customer_id
);
```