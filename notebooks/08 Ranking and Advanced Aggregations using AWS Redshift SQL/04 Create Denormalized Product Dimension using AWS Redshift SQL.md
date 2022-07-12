```sql
CREATE TABLE public.product_dim
AS
SELECT p.*,
    c.category_name,
    c.category_department_id,
    d.department_name
FROM retail_db.products AS p
    JOIN retail_db.categories AS c
        ON p.product_category_id = c.category_id
    JOIN retail_db.departments AS d
        ON c.category_department_id = d.department_id;
```