Replace snapshot from IDN_YELP_V2 in IDN_YELP

`aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2024-08-29/ --summarize --human-readable --recursive`

Total Objects: 1321
Total Size: 74.8 GiB

`aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2024-09-01/ --summarize --human-readable --recursive`

Total Objects: 1321
Total Size: 78.1 GiB

---------------------

`aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp_v2/date=2024-08-29/ --summarize --human-readable --recursive`

Total Objects: 1261
Total Size: 82.5 GiB

`aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp_v2/date=2024-09-01/ --summarize --human-readable --recursive`

Total Objects: 1261
Total Size: 83.3 GiB

-----------------
Sync old IDN_YELP
`aws s3 sync s3://DOC-EXAMPLE-BUCKET-SOURCE s3://DOC-EXAMPLE-BUCKET-TARGET
`
`aws s3 sync s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2024-09-01/ s3://adroll-crossdevice/tmp/production/snapshots/namespace=idn_yelp/date=2024-09-01/`

-----------------------------------------------
Delete Old snapshot
`aws s3 rm s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2024-09-01/ --recursive`

------------------------
Copy v2 snapshot
`aws s3 sync s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp_v2/date=2024-09-01/ s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2024-09-01/`

