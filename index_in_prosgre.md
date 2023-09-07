# Index in PostgreDB

La creacion de indices es fundamental para optimizar las consulta, pero esto conlleva PROs y Contras. 
Una de las contras es que la creacion de indices consumen mucho espacio de guardado y mayor consumo en el momento de la escritura.

Se puede crear un indice con el siguiente comando

```sql
CREATE INDEX name_index on name_table(attribute);
```

Este comando Lockea la tabla, por lo que la solucion a esto cuando se esta utilizando la tabla es crearlo concurrente

```sql
CREATE INDEX CONCURRENTLY name_index on name_table(attribute);
```

Hay casos que esto puede fallar, debido a que la tabla es muy grande o ocurrio una falla, esto se puede verificar si un indice fue marcado como invalido.

```sql
SELECT * FROM pg_class, pg_index WHERE pg_index.indisvalid = false AND pg_index.indexrelid = pg_class.oid;
```

Si el indice esta marcado como invalido, la recomendacion es eliminarlo y volverlo a crear. 

Tambien es bueno verificar si el indice sigue en creacion. Esto se puede verificar con:

```sql
SELECT
    pid,
    now() - pg_stat_activity.query_start AS duration,
    query,
    state
FROM pg_stat_activity
WHERE (now() - pg_stat_activity.query_start) > interval '5 minutes';
```
