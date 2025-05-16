# Secrets 

How to create a secret 

`printf 'yoursecret' | base64 | tr -d '\n' > secret.b64`

How to Store un S3
```bash
aws s3 cp \  
	secret.b64 \  
	s3://BUCKET/NAMESPACE/SERVICE/ACCOUNT/secret.b64 \ 
	--sse-kms-key-id "arn:aws:kms:us-east-1:771945457201:key/8beba0c6-6296-4714-b75e-f94d2184a3cd" \
	--sse aws:kms \ 
	--content-type text/plain
```

`printf 'pip-v2' | base64 | tr -d '\n' > secret.b64`

## Retrieve

`aws s3 cp s3://BUCKET/NAMESPACE/SERVICE/ACCOUNT/secret.b64 - | base64 --decode`

`aws s3 cp s3://adroll-secrets/xdev/xdev/xdev-trino-password/secret.b64 - | base64 --decode`
