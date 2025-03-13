Table size

```sql

SELECT pg_size_pretty( pg_total_relation_size('table_name') );
```

Check Invalid Index

```sql

SELECT * FROM pg_class, pg_index WHERE pg_index.indisvalid = false AND pg_index.indexrelid = pg_class.oid;
```

