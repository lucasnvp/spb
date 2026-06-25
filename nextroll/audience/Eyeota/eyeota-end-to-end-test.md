# Eyeota End to End test

El job corre en el Airflow de audience `DAG: segmentation.eyeota_uat`

La segmentacion que corre el job de Airflow esta en ["https://github.com/SemanticSugar/data/blob/main/segmentation-emr-7/src/main/java/eyeota/EyeotaUATSegmentation.java"]

## Inputs files para la segmentacion.

Inputs files para el job: `s3://adroll-data/audience-data/uat-eyeota-segmentation/`

## EyeotaUATSegmentation

Ver los outputs files. 

## CPM

Checkear el `publish_external_cpm_fee` es un csv.

Path: `s3://adroll-data/segmentation/audience-data/external_cpm_fee/`

## Seg lines

```SQL
SELECT
  date,
  segment_eid,
  cookie_type,
  count(cookie_type) AS types_count,
  count(*)           AS total_events
FROM hive.adroll.organized_log_lines
WHERE type = 'seg'
  AND advertisable = '3QOM4TKN4RD7TO3HCPYRKV'
  AND date BETWEEN '2026-05-20' AND '2026-05-27'
  AND segment_eid IN (
    'IWWEWHM2GNCRBB2BD58SEG',
    'N3XGN4QLKFHU5CMDQN8SEG'
  )
GROUP BY 1, 2, 3
ORDER BY date DESC, segment_eid, cookie_type
```

```sql
select cookie, cookie_type
from hive.adroll.log_lines
where line_type = 'seg'
    and date = '2026-05-28'
    and segment_eid in ('G4TTRDBN4BEJ5NTGAK8SEG', 'IWWEWHM2GNCRBB2BD58SEG')
    and method != 'r'
limit 10
```
