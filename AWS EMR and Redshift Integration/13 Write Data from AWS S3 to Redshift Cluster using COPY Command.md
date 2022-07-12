## Write Data from AWS S3 to Redshift Cluster using COPY Command

Let us go through the details about writing data from AWS S3 to Redshift Cluster using COPY Command.

* Develop required logic using Pyspark to get only the new repositories added.

```python
ghactivity = spark.read.json('s3://aigithub/landing/ghactivity/2022-06-19*')
ghactivity.createOrReplaceTempView('ghactivity')
new_repos = spark.sql("""
  SELECT
    repo.id AS repo_id,
    repo.name AS repo_name,
    actor.id AS actor_id,
    actor.login AS actor_login,
    actor.display_login AS actor_display_login,
    payload.ref_type AS ref_type,
    type,
    created_at,
    year(created_at) AS created_year,
    month(created_at) AS created_month,
    dayofmonth(created_at) AS created_dayofmonth
  FROM ghactivity
  WHERE type = 'CreateEvent'
    AND payload.ref_type = 'repository'
""")

# Original logic to write to files
new_repos. \
  write. \
  partitionBy('created_year', 'created_month', 'created_dayofmonth'). \
  mode('overwrite'). \
  parquet('s3://aigithub/github_dm/new_repos')
```
* Make sure the required permissions are granted on s3 to Redshift Cluster via IAM role.
* Come up with the logic to write dataframe s3 and then use COPY to copy data to Redshift Table. We use this approach if we directly want to load the data from AWS s3 to Redshift Table. This is regular Python approach with out using Spark APIs.
```python
import boto3
import json
sm_client = boto3.client('secretsmanager')
secret_value = sm_client.get_secret_value(SecretId='demo/github/redshift')
credentials = json.loads(secret_value['SecretString'])

username = credentials['username']
password = credentials['password']
host = credentials['host']
port = credentials['port']
database = 'github_dm'

import psycopg2
conn = psycopg2.connect(
    host=host,
    port=port,
    database='github_dm',
    user=username,
    password=password
)

cur = conn.cursor()

s3_bucket = 's3://aigithub/github_dm/ghrepos'
aws_iam_role = 'arn:aws:iam::269066542444:role/service-role/AmazonRedshift-CommandsAccessRole-20220625T110940'
table = 'ghrepos'

cur.execute(f'TRUNCATE TABLE {table}')
copy_command = f'''COPY {table}
    FROM '{s3_bucket}'
    IAM_ROLE '{aws_iam_role}'
    FORMAT AS PARQUET
'''

cur.execute(copy_command)
```
