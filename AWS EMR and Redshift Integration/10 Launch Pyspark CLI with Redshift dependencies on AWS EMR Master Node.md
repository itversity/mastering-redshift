## Launch Pyspark CLI with Redshift dependencies on AWS EMR Master Node

Here are the instructions to launch Pyspark CLI with required dependencies.
* Location: **/usr/share/aws/redshift/**
* We need to specify at least have the below mentioned Jar files to connect to Databases in Redshift Cluster.
  * **/usr/share/aws/redshift/jdbc/RedshiftJDBC.jar**
  * **/usr/share/aws/redshift/spark-redshift/lib/spark-redshift.jar**
  * **/usr/share/aws/redshift/spark-redshift/lib/spark-avro.jar**
  * **/usr/share/aws/redshift/spark-redshift/lib/minimal-json.jar**
```
pyspark \
  --jars /usr/share/aws/redshift/jdbc/RedshiftJDBC.jar,/usr/share/aws/redshift/spark-redshift/lib/spark-redshift.jar,/usr/share/aws/redshift/spark-redshift/lib/spark-avro.jar,/usr/share/aws/redshift/spark-redshift/lib/minimal-json.jar
```
* Here is the sample code to validate.
```python
import boto3
import json
sm_client = boto3.client('secretsmanager')
secret_value = sm_client.get_secret_value(SecretId='demo/aigithub/redshift')
credentials = json.loads(secret_value['SecretString'])

username = credentials['username']
password = credentials['password']
host = credentials['host']
port = credentials['port']
database = 'github_dm'
url = f"jdbc:redshift://{host}:{port}/{database}?user={username}&password={password}"

df = spark. \
    read. \
    format('io.github.spark_redshift_community.spark.redshift'). \
    option(
        'aws_iam_role', 
        'arn:aws:iam::269066542444:role/service-role/AmazonRedshift-CommandsAccessRole-20220625T110940'
    ). \
    option('url', url). \
    option('dbtable', 'public.ghrepos'). \
    option('tempdir', 's3://aigithub/temp/ghrepos'). \
    load()
```
