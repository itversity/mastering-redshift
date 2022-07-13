## Setup Amazon Redshift Cluster

Here are the instructions to setup Amazon Redshift Serverless Workgroup to go through the details related to integration of AWS EMR and Amazon Redshift.
* Make sure both workgroup and namespace are created with names aigithub-wg and aigithub-ns respectively.
* Get the end point of the workgroup and validate by using telnet from the Master Node of the EMR Cluster. This will validate connectivity between AWS EMR Master Node and Redshift Workgroup.
* Validate connectivity using `psql`. You have to install **postgresql-devel** using `sudo yum -y install postgresql-devel` and then use following command to validate.

```shell
psql -h aigithub-wg.269066542444.us-east-1.redshift-serverless.amazonaws.com \
  -p 5439 \
  -U admin \
  -d dev \
  -W
```
