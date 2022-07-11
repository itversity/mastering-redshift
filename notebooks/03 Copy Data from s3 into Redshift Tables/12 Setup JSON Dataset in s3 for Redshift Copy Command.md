## Setup JSON Dataset in s3 for Redshift Copy Command

Here are the commands to setup JSON data sets in AWS s3 so that we can copy the data in the JSON files into Redshift table using COPY Command.

```shell
git clone https://www.github.com/itversity/retail_db_json.git
aws s3 rm s3://itv-retail/retail_db_json/ --recursive
aws s3 cp retail_db_json s3://itv-retail/retail_db_json --recursive
aws s3 ls s3://itv-retail/retail_db_json/ --recursive
```