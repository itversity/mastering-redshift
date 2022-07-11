## Troubleshoot Errors related to Redshift Copy Command

We can review the issues related to the COPY Command by running queries against `stl_load_errors`.

```sql
SELECT * FROM stl_load_errors;
```
