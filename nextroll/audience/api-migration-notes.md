# How to migrate endpoints from V1 to V2

## GET /audience/v1/ideal_customer_profile/

### Previous analysis

```sql
select *
from targetaccounts.public.target_accounts
limit 5
```

Get request in Bruno `{{base_url}}/audience/v1/ideal_customer_profile?advertisable_eid=GT6UQRSK2NDJDNBN45OPIP`

### Repository

1. Looked icp table `DESCRIBE targetaccounts.public.icp_details`
1. Add a good amount of test

### Type

### Adapter

### Service

### Handler
