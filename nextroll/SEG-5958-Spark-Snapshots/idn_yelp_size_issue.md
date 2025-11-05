# Tips

For run it interactive

```shel
pyspark --master yarn --deploy-mode client --conf spark.yarn.maxAppAttempts=1 --conf spark.dynamicAllocation.enabled=true --conf spark.shuffle.service.enabled=true --conf spark.executor.instances=0 --driver-memory 10g --jars s3://adroll-releases/data/core-spark/core-spark.jar --py-files s3://adroll-test-sandbox-2/lucas.visser/kappa/kappa.zip
```

`from kappa.jobs.crossdevice.crossdevice_snapshot_parquet import *`

# 2025-10-07

Cluster -> https://us-west-2.console.aws.amazon.com/emr/home?region=us-west-2#/clusterDetails/j-3RHGPUMYM9N2F

```python
execution_date = datetime.strptime('2025-09-23', "%Y-%m-%d")

job = CrossdeviceSnapshotParquet(
        spark,
        'idn_yelp',
        execution_date,
        's3://adroll-crossdevice/tmp/production/snapshots-parquet/',
        1000000
    )

txlogs_df = job.load(job.txlogs_path)

txlogs_df.count()  # 1.099.131.192

previous_snapshot_df = job.load(job.previous_snapshot) 

previous_snapshot_df.count()  # 1.548.684.454

combined_df = txlogs_df.unionByName(previous_parquet_snapshot_df, allowMissingColumns=True)

combined_df.count()  # 2.647.815.646

combined_df = job._filter_old(combined_df)

combined_df.count()  # 1.099.131.192

combined_df = combined_df.orderBy(TransactionLogColumn.Id.value)

dedup_df = job._deduplicate(combined_df)

dedup_df.count()  # 303.090.871
```

# 2025-10-08

## First test `2025-09-23`

Cluster -> https://us-west-2.consoleraws.amazon.com/emr/home?region=us-west-2#/clusterDetails/j-2I5LRUQ7EYMCN

```python
execution_date = datetime.strptime('2025-09-23', "%Y-%m-%d")

job = CrossdeviceSnapshotParquet(
        spark,
        'idn_yelp',
        execution_date,
        's3://adroll-crossdevice/tmp/production/snapshots-parquet/',
        1000000
    )

txlogs_df = job.load(job.txlogs_path)

txlogs_df.count()  # 1.099.131.192

previous_snapshot_df = job.load("s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2025-09-22/")

previous_snapshot_df.count()  # 2.873.480.142

combined_df = txlogs_df.unionByName(previous_snapshot_df, allowMissingColumns=True)

combined_df.count()  # 2.647.815.646

combined_df = job._filter_old(combined_df)

combined_df.count()  # 3.972.611.334

combined_df = combined_df.orderBy(TransactionLogColumn.Id.value)

dedup_df = job._deduplicate(combined_df)

dedup_df.count()  # 2.878.473.370

```

## Second test `2025-09-24`

```python
execution_date = datetime.strptime('2025-09-24', "%Y-%m-%d")

job = CrossdeviceSnapshotParquet(
        spark,
        'idn_yelp',
        execution_date,
        's3://adroll-crossdevice/tmp/production/snapshots-parquet/',
        1000000
    )

txlogs_df = job.load(job.txlogs_path)

txlogs_df.count()  # 1.328.235.468

previous_snapshot_df = job.load(job.previous_parquet_snapshot)
# previous_snapshot_df = job.load("s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2025-09-23/")

previous_snapshot_df.count()  # 1.550.775.774

combined_df = txlogs_df.unionByName(previous_snapshot_df, allowMissingColumns=True)

combined_df.count()  # 2.879.011.242

combined_df = job._filter_old(combined_df)

combined_df.count()  # 1.328.235.468

combined_df = combined_df.orderBy(TransactionLogColumn.Id.value)

dedup_df = job._deduplicate(combined_df)

dedup_df.count()  # 
```

## Test 2025-10-14 Increase driver memory

```shel
pyspark --master yarn --deploy-mode client --conf spark.yarn.maxAppAttempts=1 --conf spark.dynamicAllocation.enabled=true --conf spark.shuffle.service.enabled=true --conf spark.executor.instances=0 --driver-memory 16g --jars s3://adroll-releases/data/core-spark/core-spark.jar --py-files s3://adroll-test-sandbox-2/lucas.visser/kappa/kappa.zip
```

`from kappa.jobs.crossdevice.crossdevice_snapshot_parquet import *`

```python
# execution_date = datetime.strptime('2025-09-24', "%Y-%m-%d")
# execution_date = datetime.strptime('2025-09-29', "%Y-%m-%d")
execution_date = datetime.strptime('2025-10-14', "%Y-%m-%d")

job = CrossdeviceSnapshotParquet(
        spark,
        'idn_yelp',
        execution_date,
        's3://adroll-crossdevice/tmp/production/snapshots-parquet/',
        1000000
    )

txlogs_df = job.load(job.txlogs_path)

txlogs_df = txlogs_df.drop("shard")

txlogs_df.count()  # 1.328.235.468

# previous_snapshot_df = job.load(job.previous_parquet_snapshot)
# previous_snapshot_df = job.load("s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2025-09-23/")
# previous_snapshot_df = job.load("s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2025-09-28/")
previous_snapshot_df = job.load("s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2025-10-16/")

previous_snapshot_df.count()  # 

combined_df = txlogs_df.unionByName(previous_snapshot_df)

combined_df.count()  # 2.879.011.242

combined_df = job._filter_old(combined_df)

combined_df.count()  # 1.328.235.468

combined_df = combined_df.orderBy(TransactionLogColumn.Id.value)

dedup_df = job._deduplicate(combined_df)

dedup_df.count()  # 306.851.612 // 2.881.111.337
```

## Tests

### Testing 2025-10-17

before_dedup_count      3.929.093.171
after_dedup_count       2.953.630.626

### Testing 2025-10-18

txlogs_counts           940.020.840
snapshot_counts         1.586.353.397

previous_snapshot_df = spark.read.schema(TransactionLogSchema).parquet(job.previous_parquet_snapshot)

previous_snapshot_df = previous_snapshot_df.select(
        col("id"),
        col("type").alias("id_type"),
        col("cluster_id"),
        col("modts").alias("ts"),
        col("txts").alias("transaction_log_ts"),
        col("meta").alias("metadata")
)

df_count                2.953.630.626

before_dedup_count      3.892.819.961
after_dedup_count       2.957.130.494

### Fix Email_liveramp graph

```shel
pyspark --master yarn --deploy-mode client --conf spark.yarn.maxAppAttempts=1 --conf spark.dynamicAllocation.enabled=true --conf spark.shuffle.service.enabled=true --conf spark.executor.instances=0 --driver-memory 16g --jars s3://adroll-releases/data/core-spark/core-spark.jar --py-files s3://adroll-test-sandbox-2/lucas.visser/kappa/kappa.zip
```

`from kappa.jobs.crossdevice.crossdevice_snapshot_parquet import *`

```python

execution_date = datetime.strptime('2025-10-22', "%Y-%m-%d")

job = CrossdeviceSnapshotParquet(
        spark,
        'email_liveramp',
        execution_date,
        's3://adroll-crossdevice/tmp/production/snapshots-parquet/',
        1000000
    )

txlogs_df = job.load(job.txlogs_path)

previous_snapshot_df = job.load("s3://adroll-crossdevice/production/snapshots/namespace=email_liveramp/date=2025-10-21/")

combined_df = txlogs_df.unionByName(previous_snapshot_df)

combined_df = job._filter_old(combined_df)

combined_df = combined_df.orderBy(TransactionLogColumn.Id.value)

dedup_df = job._deduplicate(combined_df)
```

### Ip-to-domain

```shel
pyspark --master yarn --deploy-mode client --conf spark.yarn.maxAppAttempts=1 --conf spark.dynamicAllocation.enabled=true --conf spark.shuffle.service.enabled=true --conf spark.executor.instances=0 --driver-memory 16g --jars s3://adroll-releases/data/core-spark/core-spark.jar --py-files s3://adroll-test-sandbox-2/lucas.visser/kappa/kappa.zip
```

`from kappa.jobs.crossdevice.crossdevice_snapshot_parquet import *`

```python

execution_date = datetime.strptime('2025-10-24', "%Y-%m-%d")

job = CrossdeviceSnapshotParquet(
        spark,
        'ip_to_domain',
        execution_date,
        's3://adroll-crossdevice/tmp/production/snapshots-parquet/',
        1000000
    )

txlogs_df = job.load(job.txlogs_path)

previous_snapshot_df = job.load("s3://adroll-crossdevice/production/snapshots/namespace=ip_to_domain/date=2025-10-23/")

combined_df = txlogs_df.unionByName(previous_snapshot_df)

combined_df = job._filter_old(combined_df)

combined_df = combined_df.orderBy(TransactionLogColumn.Id.value)

dedup_df = job._deduplicate(combined_df)

job.write_parquet_snapshot(dedup_df)
```
