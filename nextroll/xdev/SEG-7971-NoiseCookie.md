# SEG-7971 Noise cookie

We had a noise cookie and the block table didn't work.
I applied a filter in the ingestion.

## Cookie

The noise cookie was `49d7bb7485d52b1269993aa7742af3b7` and that cookie
moves between cluster.

```SQL
SELECT 
    date, -- Included so you can see the timeline
    id, 
    cluster_id 
    -- meta
FROM bi.crossdevice_snapshots_parquet
WHERE namespace = 'email_liveramp'
    AND id = '49d7bb7485d52b1269993aa7742af3b7'
    -- Dynamically calculate the date 30 days ago from today
    AND date >= date_format(current_date - interval '5' day, '%Y-%m-%d')
ORDER BY date DESC
```

## Block table

The cookie was in the block table

```SQL
SELECT * 
FROM block_identifiers 
WHERE identifier = '49d7bb7485d52b1269993aa7742af3b7'
```
