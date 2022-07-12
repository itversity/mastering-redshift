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