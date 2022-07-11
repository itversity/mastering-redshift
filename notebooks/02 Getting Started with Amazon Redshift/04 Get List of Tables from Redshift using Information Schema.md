## Get List of Tables from Redshift using Information Schema

Redshift is a flavor of Postgres. As we can get details of Postgres tables using **information_schema.tables**, in the similar lines we can get details of Redshift Database tables.

Here is a sample query to get list of tables created using Redshift.

```sql
SELECT * FROM information_schema.tables
WHERE table_schema = 'public'
```