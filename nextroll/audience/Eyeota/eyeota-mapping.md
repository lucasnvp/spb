# Eyeota Mapping

## Logic

Ejemplo de GEO con magellan -> ["https://github.com/SemanticSugar/kappa/blob/main/kappa/jobs/ctv/build_parquet_dump.py"]

Magellan path

`"MAGELLAN_MMDB_PATH = "s3://adroll-geoservice/production/magellan.mmdb.gz"`

## Runs

[Cluster](https://us-west-2.console.aws.amazon.com/emr/home?region=us-west-2#/clusterDetails/j-3NDVLU8YRYTSB)

Como entrar al cluster: `aws ssm start-session --region us-west-2 --target i-00b47a20ba5da1860`

```shell
sudo su hadoop
cd
```

## 2026-06-08

`pyspark --master yarn --deploy-mode client --conf spark.yarn.maxAppAttempts=1 --conf spark.dynamicAllocation.enabled=true --conf spark.shuffle.service.enabled=true --conf spark.executor.instances=0 --driver-memory 10g --jars s3://adroll-releases/data/core-spark/core-spark.jar --py-files s3://adroll-test-sandbox-2/lucas.visser/kappa/kappa.zip`

```
from kappa.jobs.audience_eyeota.eyeota_mapping import *
from datetime import datetime

class SparkArgs:
    execution_date = datetime.now().strftime("%Y-%m-%d")
    input_path = "s3://adroll-us-west-2-logs/logs"
    output_dir = "s3://adroll-test-sandbox-2/eyeota_mapping/test-1"
    lookback_days = 3
    num_files = 128

job = EyeotaMapping(SparkArgs())

job.run(spark)
```

## 2026-06-15

### Sample rate 16

Cluster -> ["https://us-west-2.console.aws.amazon.com/emr/home?region=us-west-2#/clusterDetails/j-2NE98HSSAXT45"]

`pyspark --master yarn --deploy-mode client --conf spark.yarn.maxAppAttempts=1 --conf spark.dynamicAllocation.enabled=true --conf spark.shuffle.service.enabled=true --conf spark.executor.instances=0 --driver-memory 10g --jars s3://adroll-releases/data/core-spark/core-spark.jar --py-files s3://adroll-test-sandbox-2/lucas.visser/kappa/kappa.zip`

```
from kappa.jobs.audience_eyeota.eyeota_mapping import *
from datetime import datetime

class SparkArgs:
    execution_date = datetime.now().strftime("%Y-%m-%d")
    input_path = "s3://adroll-us-west-2-logs/logs"
    output_dir = "s3://adroll-test-sandbox-2/eyeota_mapping/test-sample-16"
    lookback_days = 90
    num_files = 128
    magellan_mmdb_path = "s3://adroll-geoservice/production/magellan.mmdb.gz"
    sample_rate = 16

job = EyeotaMapping(SparkArgs())

job.run(spark)
```

### Sample rate 32

Cluster -> ["https://us-west-2.console.aws.amazon.com/emr/home?region=us-west-2#/clusterDetails/j-LJ57J4DIYET6"]

`pyspark --master yarn --deploy-mode client --conf spark.yarn.maxAppAttempts=1 --conf spark.dynamicAllocation.enabled=true --conf spark.shuffle.service.enabled=true --conf spark.executor.instances=0 --driver-memory 10g --jars s3://adroll-releases/data/core-spark/core-spark.jar --py-files s3://adroll-test-sandbox-2/lucas.visser/kappa/kappa.zip`

```
from kappa.jobs.audience_eyeota.eyeota_mapping import *
from datetime import datetime

class SparkArgs:
    execution_date = datetime.now().strftime("%Y-%m-%d")
    input_path = "s3://adroll-us-west-2-logs/logs"
    output_dir = "s3://adroll-test-sandbox-2/eyeota_mapping/test-sample-32"
    lookback_days = 90
    num_files = 128
    magellan_mmdb_path = "s3://adroll-geoservice/production/magellan.mmdb.gz"
    sample_rate = 32

job = EyeotaMapping(SparkArgs())

job.run(spark)
```


