# Spark

## How to run

1. Clone an EMR cluster without steps
1. Connect using SSM `aws ssm start-session --region us-west-2 --target i-02dac787662a68baa`
1. `sudo su hadoop`
1. `cd`
1. Run script

Script example

`spark-submit --master yarn --deploy-mode client --conf spark.yarn.maxAppAttempts=1 --conf spark.dynamicAllocation.enabled=true --conf spark.shuffle.service.enabled=true --conf spark.executor.instances=0 --driver-memory 10g --jars s3://adroll-releases/data/core-spark/core-spark.jar --py-files s3://adroll-test-sandbox-2/lucasnvp/kappa/kappa.zip s3://adroll-test-sandbox-2/lucasnvp/kappa/jobs/crossdevice/crossdevice_snapshot.py --namespace email_liveramp --logs-date 2025-04-22 --output-prefix s3://adroll-crossdevice/tmp/test/snapshots/namespace=email_liveramp/date=2025-04-22/`

## How to run interactive

1. Clone an EMR cluster without steps
1. Connect using SSM
1. `sudo su hadoop`
1. `cd`
1. Run script

Script example

`pyspark --master yarn --deploy-mode client --conf spark.yarn.maxAppAttempts=1 --conf spark.dynamicAllocation.enabled=true --conf spark.shuffle.service.enabled=true --conf spark.executor.instances=0 --driver-memory 10g --jars s3://adroll-releases/data/core-spark/core-spark.jar --py-files s3://adroll-test-sandbox-2/lucasnvp/kappa/kappa.zip`

## Links

Cluster to test - [Test cluster](https://us-west-2.console.aws.amazon.com/emr/home?region=us-west-2#/clusterDetails/j-3LJKSV8MB9HRK)
