## Setup Redshift Database and User

Here are the commands to Setup Database and User in Amazon Redshift Cluster. You can either use `psql` or Amazon Redshift Query Editor to run below commands.

```
CREATE DATABASE github_dm;

CREATE USER github_user WITH PASSWORD 'G1tHub!23';

GRANT ALL ON DATABASE github_dm TO github_user;
```