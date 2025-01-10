How to install in XDEV

```bash
export PYPI_USERNAME=$(aws s3 cp s3://adroll-secrets/xdev/xdev/xdev-pip-user/secret.b64 - | base64 -d)
export PYPI_PASSWORD=$(aws s3 cp s3://adroll-secrets/xdev/xdev/xdev-pip-password/secret.b64 - | base64 -d)

pipenv install --dev --deploy
```
