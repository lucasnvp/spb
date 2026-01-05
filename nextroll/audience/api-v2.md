# Audience API V2

## Useful pages

- [Swagger](https://editor-next.swagger.io/)
- [Json Compare](https://jsoncompare.org/)
- [Bug bash](https://adroll.atlassian.net/wiki/spaces/EN/pages/4180508691/2025-09-18+Audience+API+V2)

## Audience definition

You can use swagger to see the api definition.

V1 -> [https://app.adroll.com/audience/v1/definition.json]

V2 -> [https://app.adroll.com/audience/v2/definition.admin.json]

## Queries

https://redash.internal.adroll.com/queries/41868/source

```sql
with spending_customers as (
    select distinct advertisable_eid
    from hive.bi.uhura_deliveries
    where date = '2025-09-15'
)

select sp.advertisable_eid, count(*)
from hive.bi.segment_metadata s
inner join spending_customers sp on sp.advertisable_eid = s.advertisable_eid
where s.rule_match_method in ('video_viewer')
      and s.rule_active
      and s.segment_active
group by sp.advertisable_eid
order by 2 desc
-- having count(*) < 100 AND count(distinct s.rule_match_method) = 3
```

https://redash.internal.adroll.com/queries/41867/source?p_type=video_viewer
SegmentDB Customers by Type

```sql
with spending_customers as (
    select distinct advertisable_eid
    from hive.bi.uhura_deliveries
    where date = '2025-09-15'
)

select s.advertisable_eid, count(*)
from segmentdb.public.segments s
inner join spending_customers sc on sc.advertisable_eid = s.advertisable_eid
where
    type = '{{ type }}'
    and is_active
group by s.advertisable_eid
having count(*) < 100
order by 2 desc
limit 10
```
