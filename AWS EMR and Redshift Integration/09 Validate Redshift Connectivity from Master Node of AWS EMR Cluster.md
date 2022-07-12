## Validate Redshift Connectivity from Master Node of AWS EMR Cluster

Here are the instructions to validate Redshift Connectivity from Master Node of AWS EMR Cluster.
* Check security group inbound rule for Redshift Cluster.
* Make sure to add rules for security groups associated with AWS EMR Masters and Slaves.
* Use telnet to confirm the network connectivity from AWS EMR to Redshift.
Optionally, we can also install psycopg2-binary and validate connectivity to Redshift from AWS EMR using Python.
```python
import boto3
import json
sm_client = boto3.client('secretsmanager')
secret_value = sm_client.get_secret_value(SecretId='demo/github/redshift')
credentials = json.loads(secret_value['SecretString'])
import psycopg2
conn = psycopg2.connect(
    host=credentials['host'],
    port=credentials['port'],
    database='github_dm',
    user=credentials['username'],
    password=credentials['password']
)

query = '''
    SELECT * FROM information_schema.tables
    WHERE table_schema = 'public'
'''
cur = conn.cursor()
cur.execute(query)
for rec in cur.fetchall():
    print(rec)
```