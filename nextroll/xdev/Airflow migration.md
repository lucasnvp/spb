#### IDN_YELP
aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2024-07-18/ --summarize --human-readable --recursive

Total Objects: 1111
Total Size: 54.1 GiB

aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2024-07-19/ --summarize --human-readable --recursive

Total Objects: 1112
Total Size: 54.3 GiB

#### IDN_YELP_V2
aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp_v2/date=2024-07-18/ --summarize --human-readable --recursive

Total Objects: 1046
Total Size: 67.6 GiB

| Date       | Size     |
| ---------- | -------- |
| 2024-07-19 | 67.9 GiB |
| 2024-07-20 | 68.3 GiB |
| 2024-07-21 | 68.7 GiB |
| 2024-07-22 | 69.1 GiB |
| 2024-07-23 | 69.4 GiB |
| 2024-07-24 | 69.7 GiB |
| 2024-07-25 | 70.0 GiB |
| 2024-07-26 | 70.2 GiB |
| 2024-07-27 | 70.5 GiB |
| 2024-07-28 | 70.9 GiB |
| 2024-07-29 | 71.2 GiB |
| 2024-07-30 | 71.5 GiB |

aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp_v2/date=2024-07-19/ --summarize --human-readable --recursive

Total Objects: 1051
Total Size: 67.9 GiB

#### IP_TO_DOMAIN
aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=ip_to_domain/date=2024-07-18/ --summarize --human-readable --recursive

Total Objects: 121
Total Size: 6.1 GiB

aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=ip_to_domain/date=2024-07-19/ --summarize --human-readable --recursive

Total Objects: 121
Total Size: 6.2 GiB

#### mvp_idn_email_weighted_v3
aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=mvp_idn_email_weighted_v3/date=2024-07-18/ --summarize --human-readable --recursive

Total Objects: 1081
Total Size: 68.4 GiB

aws s3 ls s3://adroll-crossdevice/production/snapshots/namespace=mvp_idn_email_weighted_v3/date=2024-07-19/ --summarize --human-readable --recursive

Total Objects: 1081
Total Size: 68.4 GiB

-----------------------------
#### Sync snapshots

s3://adroll-crossdevice/production/snapshots/namespace=email_liveramp/
s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/
s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp_v2/
s3://adroll-crossdevice/production/snapshots/namespace=ip_to_domain/
s3://adroll-crossdevice/production/snapshots/namespace=mvp_idn_email_weighted_v3/

```bash
aws s3 sync s3://adroll-crossdevice/production/snapshots/namespace=email_liveramp/date=2024-07-21/ s3://adroll-crossdevice/staging/snapshots/namespace=email_liveramp/date=2024-07-21/

aws s3 sync s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp/date=2024-07-21/ s3://adroll-crossdevice/staging/snapshots/namespace=idn_yelp/date=2024-07-21/

aws s3 sync s3://adroll-crossdevice/production/snapshots/namespace=idn_yelp_v2/date=2024-07-21/ s3://adroll-crossdevice/staging/snapshots/namespace=idn_yelp_v2/date=2024-07-21/

aws s3 sync s3://adroll-crossdevice/production/snapshots/namespace=ip_to_domain/date=2024-07-21/ s3://adroll-crossdevice/staging/snapshots/namespace=ip_to_domain/date=2024-07-21/

aws s3 sync s3://adroll-crossdevice/production/snapshots/namespace=mvp_idn_email_weighted_v3/date=2024-07-21/ s3://adroll-crossdevice/staging/snapshots/namespace=mvp_idn_email_weighted_v3/date=2024-07-21/
```




