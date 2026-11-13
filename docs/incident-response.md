# Incident triage runbook

## Scenario: suspected password spray
1. Record alert ID, detection window, source IP, targeted accounts, and failure count.
2. Validate raw `SigninLogs` records and check whether the source is a known corporate proxy or approved test.
3. Check successful sign-ins for targeted accounts, device details, MFA outcomes, and conditional access results.
4. Correlate with user reports, geographic patterns, and other relevant alerts.
5. If credible, escalate to authorized responders for containment decisions (such as session revocation or credential resets).
6. Preserve timestamps and evidence references according to retention and privacy policies.
7. Document disposition, false positives, detection tuning, and follow-up tasks.

## Sample incident summary (fictional)
- **Alert:** Password spray from single source IP
- **Source:** `192.0.2.10` (documentation address)
- **Affected identities:** 5 synthetic users
- **Evidence:** 10 failed sign-ins in 10 minutes
- **Disposition:** Simulated incident; no real systems were affected
