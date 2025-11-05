# Analysis

We inserted the snapshots parquet into trino.

```SQL
SELECT distinct(date) 
FROM hive.bi.crossdevice_snapshots_parquet_spark_test
```

| date |
|------|
| 2025-07-12 |	
| 2025-07-21 |	
| 2025-07-13 |	
| 2025-07-14 |	
| 2025-08-01 |	
| 2025-07-20 |

```SQL
SELECT * 
FROM hive.bi.crossdevice_snapshots_parquet_spark_test
WHERE date = '2025-08-01'
LIMIT 1
```

```SQL
SELECT COUNT(*) AS diff_count
FROM (
    SELECT
        COALESCE(t1.id, t2.id) AS id,
        COALESCE(t1.cluster_id, t2.cluster_id) AS cluster_id,
        COALESCE(t1.type, t2.type) AS type,
        COALESCE(t1.modts, t2.modts) AS modts,
        COALESCE(t1.txts, t2.txts) AS txts,
        COALESCE(t1.meta, t2.meta) AS meta,
        COALESCE(t1.namespace, t2.namespace) AS namespace,
        COALESCE(t1.date, t2.date) AS date
    FROM hive.bi.crossdevice_snapshots_parquet_spark_test t1
    FULL OUTER JOIN hive.bi.crossdevice_snapshots_parquet t2
        ON t1.id = t2.id
        AND t1.cluster_id = t2.cluster_id
        AND t1.type = t2.type
        AND t1.namespace = t2.namespace
        AND t1.date = t2.date
    WHERE t1.date = '2025-08-01'
      AND t2.date = '2025-08-01'
      AND t1.namespace = 'ip_to_domain'
      AND t2.namespace = 'ip_to_domain'
      AND (
          t1.id IS NULL OR t2.id IS NULL OR
          t1.cluster_id <> t2.cluster_id OR
          t1.type <> t2.type OR
          t1.modts <> t2.modts OR
          t1.txts <> t2.txts OR
          t1.meta <> t2.meta
      )
) diffs
```

There are 247 rows. 

```SQL
SELECT count(*)
FROM hive.bi.crossdevice_snapshots_parquet
WHERE namespace = 'ip_to_domain' 
    and date = '2025-08-01'
```

The parquet for 2025-08-01 has 157.258.175 rows.

## 2025-08-27

```sql
SELECT count(*)
FROM hive.bi.crossdevice_snapshots_parquet_spark t1
WHERE t1.date = '2025-08-25'
    AND t1.namespace = 'ip_to_domain'
```

155,206,577

```sql
SELECT count(*)
FROM hive.bi.crossdevice_snapshots_parquet t1
WHERE t1.date = '2025-08-25'
    AND t1.namespace = 'ip_to_domain'
```

154,455,603

```sql
SELECT COUNT(*) AS diff_count
FROM (
    SELECT
        COALESCE(t1.id, t2.id) AS id,
        COALESCE(t1.cluster_id, t2.cluster_id) AS cluster_id,
        COALESCE(t1.type, t2.type) AS type,
        COALESCE(t1.modts, t2.modts) AS modts,
        COALESCE(t1.txts, t2.txts) AS txts,
        COALESCE(t1.meta, t2.meta) AS meta,
        COALESCE(t1.namespace, t2.namespace) AS namespace,
        COALESCE(t1.date, t2.date) AS date
    FROM hive.bi.crossdevice_snapshots_parquet_spark t1
    FULL OUTER JOIN hive.bi.crossdevice_snapshots_parquet t2
        ON t1.id = t2.id
        AND t1.cluster_id = t2.cluster_id
        AND t1.type = t2.type
        AND t1.namespace = t2.namespace
        AND t1.date = t2.date
    WHERE t1.date = '2025-08-25'
      AND t2.date = '2025-08-25'
      AND t1.namespace = 'ip_to_domain'
      AND t2.namespace = 'ip_to_domain'
      AND (
          t1.id IS NULL OR t2.id IS NULL OR
          t1.cluster_id <> t2.cluster_id OR
          t1.type <> t2.type OR
          t1.modts <> t2.modts OR
          t1.txts <> t2.txts OR
          t1.meta <> t2.meta
      )
) diffs
```

283

## 2025-10-30

```sql
SELECT *
    FROM FROM hive.bi.crossdevice_snapshots_parquet
    WHERE namespace = 'email_liveramp'
        AND date = '2025-10-27'
        AND id = '50124e5fd88998699d0556187fc45d5c';
```

