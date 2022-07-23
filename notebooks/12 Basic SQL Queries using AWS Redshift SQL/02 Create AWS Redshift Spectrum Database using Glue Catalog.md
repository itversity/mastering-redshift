```sql
SELECT * FROM information_schema.tables;

CREATE EXTERNAL SCHEMA IF NOT EXISTS retail_db
FROM DATA CATALOG
DATABASE 'retail_db'
IAM_ROLE 'arn:aws:iam::269066542444:role/AIRedshiftRetailSpectrum'
CREATE EXTERNAL DATABASE IF NOT EXISTS;

SELECT count(*) FROM retail_db.orders;

SELECT count(*) FROM retail_db.order_items;
```