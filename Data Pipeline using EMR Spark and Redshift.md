Here are the steps involved in developing data pipeline using EMR Spark and Redshift.
* Setup Retail Data Sets such as **orders** and **order_items** in AWS s3.
* Come up with Script using Spark SQL Queries to compute daily product revenue and write to s3.
* Upload the Script to AWS s3.
* Create Table in Redshift Serverless Namespace to populate daily product revenue data.
* Develop Lambda Function to copy data from s3 to Redshift using boto3.
* Develop a pipeline or State Machine using AWS Step Functions.
  * Validate if the files exists in AWS s3 or not.
  * Create EMR Cluster if files exists.
  * Add a step with Spark SQL Query to the EMR Cluster created.
  * Terminate EMR Cluster once the job is executed.
  * Trigger AWS Lambda Function to copy the output to Redshift Table.