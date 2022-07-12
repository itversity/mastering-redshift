## Validate Python Boto3 on Master Node of AWS EMR Cluster

Here are the instructions to validate Python Boto3 on Master Node of AWS EMR Cluster.
* As we have included instructions to install Python Boto3 as part of bootstrapping, Boto3 should be available on all nodes including Master Node of AWS EMR Cluster.
* You can run `pip list|grep boto3` to confirm whether Python Boto3 is installed or not.
* We can also launch Python and run below piece of code.

```python
import boto3
s3_client = boto3.client('s3')

buckets = s3_client.list_buckets()['Buckets']
for bucket in buckets:
    print(bucket['Name'])
```