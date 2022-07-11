## Run Copy Command to copy data from s3 to Redshift Table

Here is the copy command to copy data from AWS S3 to Redshift Table. We need to make sure the Redshift Cluster have read only access on S3 Bucket where we have files.

```sql
COPY orders FROM 's3://itv-retail/retail_db/orders/part-00000' 
CREDENTIALS 'aws_access_key_id=<YOUR_ACCESS_KEY>;aws_secret_access_key=<YOUR_SECRET_KEY>'
CSV;
```