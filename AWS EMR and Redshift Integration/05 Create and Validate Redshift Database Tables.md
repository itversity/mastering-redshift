## Create Redshift Database Tables


* Create required tables in Redshift. Use github_user to connect to github_dm database on Redshift Cluster to create the table.
```
CREATE TABLE public.ghrepos (
  repo_id BIGINT DISTKEY,
  repo_name VARCHAR,
  actor_id BIGINT,
  actor_login VARCHAR,
  actor_display_login VARCHAR,
  ref_type VARCHAR,
  type VARCHAR,
  created_at VARCHAR,
  year INT,
  month INT,
  day INT
);
```
