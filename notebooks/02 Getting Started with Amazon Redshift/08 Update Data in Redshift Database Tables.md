## Update Data in Redshift Database Tables

Let us go through the details related to CRUD Operations on Redshift Database Tables. Like most of the standard Databases, Redshift supports all common CRUD Operations (INSERT, UPDATE, SELECT and DELETE)

Let us see few examples related to updating data in Redshift Tables.

```sql
UPDATE myusers
	SET user_first_name = 'Mickey', 
	user_last_name = 'Mouse'
WHERE user_id = 2;
 
SELECT * FROM myusers;
 
SELECT lower('Mouse');
 
SELECT * FROM myusers;
 
UPDATE myusers
	SET user_first_name = lower(user_first_name), 
		user_last_name = lower(user_last_name);
 
SELECT * FROM myusers
```