## Create IAM Role for Redshift to access s3

Here are the instructions Create AWS IAM Role with s3 full access so that data can be copied from files in AWS s3 to Redshift Table.

* Create role for Redshift Service with s3 full access policy.
* Add role to Redshift cluster (Actions -> Manage Permissions -> Manage IAM).
* Wait until the server is modified and in available state.