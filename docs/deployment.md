# Optional deployment and validation

**Prerequisites:** Azure subscription, Log Analytics workspace, Microsoft Sentinel onboarding, Entra ID diagnostic settings sending `SigninLogs` and `AuditLogs` to the workspace, sufficient permissions and awareness of potential charges.

1. Verify that `SigninLogs` and `AuditLogs` tables contain expected fields.
2. Open Logs in the workspace and run each `.kql` query after adjusting the time range and thresholds.
3. Create a scheduled analytics rule for the password-spray query, using the YAML specification as a guide.
4. Set entity mapping for IP address and review incident grouping, alert suppression, and automated actions.
5. Generate approved test sign-in events or use a dedicated nonproduction tenant. Synthetic CSV is not automatically ingested by these queries.
6. Review alerts for false positives and document tuning before production use.

## Caveats
- Table availability and schema depend on connector configuration.
- Queries use `ago()` and will not find old synthetic CSV records unless ingested with suitable timestamps.
- Role-change operation names can vary; confirm in your tenant.
- Never use sample thresholds without measuring a baseline.
