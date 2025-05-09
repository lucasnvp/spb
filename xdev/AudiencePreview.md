# Audience Preview

Confluence page for [Audience preview](https://adroll.atlassian.net/wiki/spaces/EN/pages/3826253971/Audience+Pillar+Audience+Preview)

## Audience preview API

[Audience preview API](https://adroll.atlassian.net/wiki/spaces/EN/pages/3824910366/Audience+preview+API)

https://github.com/SemanticSugar/sigma/blob/main/sigma-go/internal/api/audience_preview_handler.go

## ClickHouse

### RW ClickHouse connect

1 - Get banyan up and running and run in the terminal:

```shell
nohup banyanproxy -l 18125 rollworks-clickhouse-production.8123-internal.banyan.adroll.com 8443 >/dev/null 2>&1 &
nohup banyanproxy -l 19001 rollworks-clickhouse-production.9000-internal.banyan.adroll.com 8443 >/dev/null 2>&1 &
```

2 - Set up a connection in DBEAVER:

```config
Host: localhost
Port: 18125
Username: batchgma
Password: see bellow
```

2.5 - Get the password for the database to the clipboard

`aws s3 cp s3://adroll-secrets/rollworks-clickhouse/aws-batch/batchgma/secret.b64 - | base64 --decode | pbcopy`

### Audience ClickHouse

[ClickHouse Cloud](https://console.clickhouse.cloud/)

### Info CH

[Clickhouse tables](https://github.com/SemanticSugar/sigma/blob/main/sigma-go/deployments/compose/assets/clickhouse/init.sql)
You can use this code in Sigma to test in the local enviroment the CH tables.

## Job

[Kappa job](https://github.com/SemanticSugar/kappa/tree/main/kappa/jobs/audience_preview)

Input: `s3://adroll-b2b-data/uat-normalized-offload-parquet/`

## Orchestration

In the Audience-Orchestration -> [Orchestration](https://github.com/SemanticSugar/audience-orchestration/tree/main/dags/src/audience/audience_preview)

## Slargma

In slarma, you can select the prod table [Code in slargma](https://github.com/SemanticSugar/slargma/blob/c2b0fae664197dad768325a9674f2d3c4b41968b/audience/model/segmentdb/audience_preview.py#L13)

## Sigma

Here is the code for the API. The API is written in GO

## TODO

- [ ] Update The Audience Preview APi to accept attributes & domains
- [X] Create skeleton in Kappa
- [X] Create skeleton in Audience-Orchestration
- [X] Setup Sigma
