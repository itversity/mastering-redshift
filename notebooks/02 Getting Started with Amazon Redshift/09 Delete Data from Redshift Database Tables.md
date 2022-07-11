## Delete Data from Redshift Database Tables

Let us go through the details related to CRUD Operations on Redshift Database Tables. Like most of the standard Databases, Redshift supports all common CRUD Operations (INSERT, UPDATE, SELECT and DELETE)

Let us see few examples related to deleting data from Redshift Tables.

```sql 
SELECT * FROM myusers;
 
DELETE FROM myusers
WHERE user_id = 1;
 
SELECT * FROM myusers;
 
DELETE FROM myusers;
 
TRUNCATE TABLE myusers;
 
SELECT * FROM myusers;
```