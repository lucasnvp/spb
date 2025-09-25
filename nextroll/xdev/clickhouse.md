# ClickHouse

How to upload data from s3

```sql
-- Load UAT data into cookie_domains_sample_tmp
INSERT INTO test.cookie_domains_sample_tmp (
  domain, geo2_country_code, seniority, functional_areas, cookie, decision_maker, household_income, gender, age, 
  education, intent_categories, company_industry, company_revenue,company_size, networth, languages, professional_groups, install_data, interests, manufacturing)
SELECT
  domain,
  geo2_country_code,
  seniority,
  functional_areas,
  cookie,
  decision_maker,
  household_income,
  gender,
  age,
  education,
  intent_categories,
  company_industry,
  company_revenue,
  company_size,
  networth,
  splitByChar(',', assumeNotNull('languages')) AS languages,
  splitByChar(',', assumeNotNull('professional_groups')) AS professional_groups,
  splitByChar(',', assumeNotNull('install_data')) AS install_data,
  splitByChar(',', assumeNotNull('interests')) AS interests,
  splitByChar(',', assumeNotNull('manufacturing')) AS manufacturing
FROM s3(
  'https://adroll-data.s3.us-west-2.amazonaws.com/audience-preview-clickhouse/uat_offload_sample/date=2025-05-20/id_type=cookie/*.parquet',
  'user', 'pass',
  'Parquet',
  auto
);
```
