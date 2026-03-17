#Programing 

Como buscar los PID de las querys que se estan ejecutando
```sql
SELECT  
  pid,  
  now() - pg_stat_activity.query_start AS duration,  
  query,  
  state  
FROM pg_stat_activity  
WHERE (now() - pg_stat_activity.query_start) > interval '5 minutes';
```

Como cancelarlos
```sql
SELECT pg_cancel_backend(pid);
```

VACUUM Stats
```python
async def aurora_vacuum_stats(conn):  
    table = 'idn_spartan'  
    q = f'''SELECT relname, n_live_tup, trunc(100*n_dead_tup/(n_live_tup+1))::float "ratio%" FROM pg_stat_all_tables WHERE relname='{table}' '''  
    return await conn.fetchrow(q)
```

Tamaño de tablas
```SQL
SELECT pg_size_pretty( pg_total_relation_size('table_name') );
```

Check Invalid Index

```SQL
SELECT * FROM pg_class, pg_index WHERE pg_index.indisvalid = false AND pg_index.indexrelid = pg_class.oid;
```
