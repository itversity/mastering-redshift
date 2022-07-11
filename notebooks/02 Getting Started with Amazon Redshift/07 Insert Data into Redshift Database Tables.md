## Insert Data into Redshift Database Tables

Let us go through the details related to CRUD Operations on Redshift Database Tables. Like most of the standard Databases, Redshift supports all common CRUD Operations (INSERT, UPDATE, SELECT and DELETE)

Let us see few examples related to inserting data into Redshift Tables.

```sql
INSERT INTO myusers
(user_id, user_first_name, user_last_name)
VALUES
(1, 'Scott', 'Tiger');

INSERT INTO myusers
VALUES
(2, 'Donald', 'Duck');
```

You can also insert multiple records at once.
```sql
INSERT INTO myusers
VALUES
(1, 'Scott', 'Tiger'),
(2, 'Donald', 'Duck');

SELECT * FROM myusers
```