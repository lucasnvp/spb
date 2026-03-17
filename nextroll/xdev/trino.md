# Trino

## How to query S3 data

[Query your favourite data](https://adroll.atlassian.net/wiki/spaces/EN/pages/116430525/Trino+-+Querying+your+favourite+data+on+S3)
Como subir y consumir parquet files en Trino.

## Conectarse a CLI

```
trino \  
  --insecure \  
  --server https://localhost:8443 \  
  --catalog hive \  
  --user xdev.team@nextroll.com \  
  --password
```

Para acceder a la password.

`aws s3 cp s3://adroll-secrets/xdev/xdev/xdev-trino-password/secret.b64 - | base64 --decode`
