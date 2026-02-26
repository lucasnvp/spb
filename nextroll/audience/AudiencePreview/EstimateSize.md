# Estimate Size bug

API in `Sigma` repo. The UI calls the V1, but for the Audience Estimation use V2 (For third party info. Expirience - Clickhouse)

## Useful Links

- (PR For AudiencePreview)[https://github.com/SemanticSugar/sigma/pull/180/changes]
- (Audience Preview Household counts per attributes)[https://docs.google.com/spreadsheets/d/1Tt6aCXbUMyDKWOYjeOV3wPySkI57ubx3bFZMvsWWAW4/edit?gid=1169113960#gid=1169113960]
- (Unique households per segment)[https://docs.google.com/spreadsheets/d/1F8bR2jgHNCFvi-XIjLuHQs-TE5sVPwwCS0QvaqAkeak/edit?gid=534922182#gid=534922182]
- (EstimateSizeOfAudience function)[https://github.com/SemanticSugar/sigma/blob/main/sigma-go/internal/api/audience_preview_handler.go#L57]
