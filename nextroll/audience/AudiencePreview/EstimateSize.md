# Estimate Size bug

API in `Sigma` repo. The UI calls the V1, but for the Audience Estimation, use V2. 
V2 is used for third-party info like Experience. The info is in Clickhouse

## Useful Links

- [PR For AudiencePreview](https://github.com/SemanticSugar/sigma/pull/180/changes)
- [Audience Preview Household counts per attributes](https://docs.google.com/spreadsheets/d/1Tt6aCXbUMyDKWOYjeOV3wPySkI57ubx3bFZMvsWWAW4/edit?gid=1169113960#gid=1169113960)
- [Unique households per segment](https://docs.google.com/spreadsheets/d/1F8bR2jgHNCFvi-XIjLuHQs-TE5sVPwwCS0QvaqAkeak/edit?gid=534922182#gid=534922182)
- [EstimateSizeOfAudience function](https://github.com/SemanticSugar/sigma/blob/main/sigma-go/internal/api/audience_preview_handler.go#L57)

## Clickhouse

[Clickhouse](https://console.clickhouse.cloud/services/26c52fce-78ff-460b-84f7-52f761188a14/console/query/c3c92fdd-2fad-4851-8925-7d5165a9ed2b) I have an account already.

```SQL
select distinct count(luid) 
from experian_ctv_graph_sample_20260221 
where id in ( select cookie from cookie_segments_sample where segment_id=77203478)
```
