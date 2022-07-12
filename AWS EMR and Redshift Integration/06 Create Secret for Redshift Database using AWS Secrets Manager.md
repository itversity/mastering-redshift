## Create Secret for Redshift Database using AWS Secrets Manager

Here are the instructions to create secret for Redshift Database using AWS Secrets Manager.
* Go to AWS Web Console and then to Secrets Manager.
* Choose Redshift and enter required details to create Secret.
* Make sure to update permissions on the role **EMR_EC2_DefaultRole** to read the value for the secret **demo/github/redshift**. Make sure to specify the Secret Id from ARN.