## Create Database Table in Redshift Cluster

Let us go ahead and run our first `CREATE TABLE` command against Redshift Cluster to create our first table.

```sql
CREATE TABLE myusers (
  user_id INT PRIMARY KEY,
  user_first_name VARCHAR(30),
  user_last_name VARCHAR(30)
);
```

Here are some of the important details related to Redshift tables when compared with Postgres.
* The PRIMARY KEY is not enforced.
* There will be index created to support PRIMARY KEY.
* We cannot define the PRIMARY KEY as SERIAL (sequence generated surrogate keys)