```
["pipenv","run","python",
"crossdevice/snapshots/merge_snapshots.py",
"--output prefix","s3://adrollcrossdevice/production/snapshots/namespace=email_liveramp/date=2024-07-03/shard=0020/",
"--split-size","1000000",
"--namespace","email_liveramp",
"--paths","@s3://adroll-crossdevice/tmp1d/snapshot-tmp-2-email_liveramp-2024-07-03/splitfiles/1d794d38d03d1d96554a28337b4613f0",
"--shard","20"]
```

aws s3 cp s3://adroll-crossdevice/tmp1d/snapshot-tmp-staging-email_liveramp-2024-07-09/splitfiles/08412d2f2366207a0225efa237797f8f - | base64 -d

aws s3 cp s3://adroll-crossdevice/tmp1d/snapshot-tmp-2-email_liveramp-2024-07-09/splitfiles/03ea6b80230002f17146141883a4f364  /dev/stdout

#### Last snapshot OK
`aws s3 ls s3://adroll-crossdevice/staging/snapshots/namespace=email_liveramp/date=2024-07-04/ --summarize --human-readable --recursive`

```
Total Objects: 4651
Total Size: 356.7 GiB
```

Delete next day to test
`aws s3 rm s3://adroll-crossdevice/staging/snapshots/namespace=email_liveramp/date=2024-07-05/ --recursive`

Tmp splitfiles
`aws s3 ls s3://adroll-crossdevice/tmp1d/snapshot-tmp-staging-email_liveramp-2024-07-05/splitfiles/`

`aws s3 cp s3://adroll-crossdevice/tmp1d/snapshot-tmp-staging-email_liveramp-2024-07-05/splitfiles/0491b841d1ef867cce357a9c8331dcca  /dev/stdout`

