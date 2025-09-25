# Audience Preview

Confluence page for [Audience preview](https://adroll.atlassian.net/wiki/spaces/EN/pages/3826253971/Audience+Pillar+Audience+Preview)

[Diagram](https://app.diagrams.net/#G1JZ1pFKbB6XCma5ZQB2rKcMixNa7Gv4vY#%7B%22pageId%22%3A%22VYPdLxk8rHpUHXZWrkEl%22%7D)

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

Here you can add S3 Permissions [audience_preview_access](https://us-east-1.console.aws.amazon.com/iam/home?region=us-west-2#/users/details/cdpplus-clickhouse-staging/editPolicy/audience_preview_access?step=addPermissions)

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

## Sigma - Audience Preview API

Here is the code for the API. The API is written in GO

[Audience preview API](https://adroll.atlassian.net/wiki/spaces/EN/pages/3824910366/Audience+preview+API)

Here is an example for the old [API](https://app.adroll.com/segments/new/?advertisable=5L5IV3X4ZNCUZFMLN5KKOD) 

[Proposal](https://adroll.atlassian.net/wiki/spaces/EN/pages/3987996674/API+Changes+for+Audience+Preview+RW+UAT+Segments)

[Audience preview handler](https://github.com/SemanticSugar/sigma/blob/main/sigma-go/internal/api/audience_preview_handler.go)

## TODO

- [ ] Update The Audience Preview APi to accept attributes & domains
- [ ] Update Audience_Orchestration
- [X] Create skeleton in Kappa
- [X] Create skeleton in Audience-Orchestration
- [X] Setup Sigma
