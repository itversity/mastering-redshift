## Validate users data using Redshift Query Editor

Let us understand how to validate users data using Redshift Query Editor by running relevant queries.

Once we provision Redshift Cluster with sample database called **dev** we will end up having some tables in the database. One of the table is nothing but **users**. Here are the examples to get started with queries against Redshift tables.

```sql
SELECT * FROM users LIMIT 10;
 
SELECT count(*) FROM users;
```