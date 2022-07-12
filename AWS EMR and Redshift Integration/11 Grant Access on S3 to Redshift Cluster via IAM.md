## Grant Access on S3 to Redshift Cluster via IAM

Here are the details of granting access on s3 to Redshift Cluster via IAM.
* When we try to write Spark Data Frame to Redshift Table, it will copy the files to temporary location in s3 using Avro format.
* Once the the files are copied to temporary location in s3, COPY Command will be issued internally. The Redshift Cluster will try to run the COPY Command.
* To ensure COPY Command work, we need to provide at least read access on the s3 bucket where the temporary location is used for the files. We can grant the permissions using IAM Role.
* We can either attach IAM policy with required permissions to the role which is already attached to Redshift Cluster or create a new role with the policy and attach the role to the Redshift Cluster.