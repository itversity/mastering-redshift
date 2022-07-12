## Read Secret from AWS Secrets Manager using Python Boto3

Here is the logic to get the secret details from AWS Secrets Manager using Boto3.
```python
import boto3
sm_client = boto3.client('secretsmanager')
secret_value = sm_client.get_secret_value(SecretId='demo/github/redshift')
secret_value['SecretString']
```