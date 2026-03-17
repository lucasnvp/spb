```SQL
SELECT 
    type,
    COUNT(DISTINCT id) as ids
FROM bi.crossdevice_snapshots_parquet
WHERE namespace='email_liveramp'
    AND date = '2025-02-04'
GROUP BY 1
ORDER BY 1
```

[Dashboar xdev](https://redash.internal.adroll.com/dashboards/4225-cross-device-clusters-and-identifiers?p_Namespace=email_liveramp&p_w5199_Date=2025-02-04&p_w5200_Date=2025-02-04)

```SQL
select cookie, identifier, email_domain, device_id, device_id_type
from adroll.log_lines 
where date='2025-02-04' 
    and line_type='idn' 
    and event_source='sendrolling' 
    and (device_id is not null)
limit 5
```

#### Tests B2B hashed emails
```SQL
-- SELECT cookie
-- FROM hive.b2b.cookie_to_hashed_emails c1
-- WHERE date = '2024-06-01'
-- AND NOT EXISTS (
--     SELECT 1
--     FROM hive.b2b.cookie_to_hashed_emails c2
--     WHERE c2.cookie = c1.cookie AND c2.date = '2025-01-01'
-- )

-- SELECT c1.cookie
-- FROM hive.b2b.cookie_to_hashed_emails c1
-- LEFT JOIN hive.b2b.cookie_to_hashed_emails c2
--     ON c1.cookie = c2.cookie AND c2.date = '2024-06-01'
-- WHERE c1.date = '2025-01-01'
-- AND c2.cookie IS NULL


-- SELECT cookie
-- FROM hive.b2b.cookie_to_hashed_emails c1
-- WHERE date = '2024-06-01'
-- LIMIT 10

-- SELECT *
-- FROM hive.b2b.cookie_to_hashed_emails c1
-- WHERE date = '2024-06-01'
--     AND cookie = 'f2eeae1fe73dae9e058bb2bd502fd8d9'

-- f2eeae1fe73dae9e058bb2bd502fd8d9
-- 8de4d9ffce11642e87d7fac70462af9e
-- 8fb81b9d5c61d974a77b12e6cd945cc9
-- 0e7cf8615e2c0c046b596b8eca0c3fe5

SELECT *
FROM hive.b2b.cookie_to_hashed_emails
WHERE date = '2025-01-01'
    AND cookie = '0e7cf8615e2c0c046b596b8eca0c3fe5'
```

