## Setup Data in s3 for Redshift Copy

Here are the AWS CLI Commands to Setup Data in s3 to eventually Copy into Redshift Tables. We are going to copy files from the local folder on our system into s3.

```shell
aws s3 rm s3://itv-retail/retail_db/ --recursive
aws s3 cp retail_db s3://itv-retail/retail_db --recursive
aws s3 ls s3://itv-retail/retail_db/ --recursive
```
