# Microsoft Sentinel Threat Detection

A portfolio-ready Microsoft Sentinel detection engineering project featuring Kusto Query Language (KQL) analytics, threat-hunting queries, sample security events, and incident-response playbooks.

> **Status:** Example configurations and synthetic data. Not deployed to or validated in a Microsoft Sentinel workspace. No Azure subscription is needed to review this repository.

## What this demonstrates
- Detection logic for repeated failed sign-ins and suspicious successful authentication
- KQL hunting for unusual sign-in geography and privileged role activity
- Microsoft Sentinel scheduled analytics rule configuration examples
- Incident triage and investigation documentation
- CI checks for repository structure and example data

## Repository layout
```
detections/        KQL queries and example analytics rule YAML
hunting/           Investigation queries
sample-data/       Synthetic sign-in events (CSV)
workbooks/         Workbook design notes
docs/              Architecture, triage, deployment, and limitations
.github/workflows/ Automated repository checks
```

## Quick review (no installation)
1. Read `docs/architecture.md` for the detection pipeline and Mermaid diagrams.
2. Inspect the `.kql` queries under `detections/` and `hunting/`.
3. Compare detection intent with the synthetic events in `sample-data/signins.csv`.
4. Review `docs/incident-response.md` for analyst procedures.
5. Inspect the GitHub Actions validation workflow.

## Deploying in a real environment (optional)
A Microsoft Sentinel-enabled Log Analytics workspace and appropriate permissions are required. Confirm your table schemas, licensing, retention, and query performance. Open **Microsoft Sentinel → Analytics → Create → Scheduled query rule**, paste a query from `detections/`, configure schedule, threshold, entity mapping, and incident settings. Review `docs/deployment.md` first. The YAML files are illustrative rule specifications, not directly importable ARM templates.

## Example detection: password spray
`detections/password_spray.kql` aggregates failed sign-ins by source IP over 1 hour, counting distinct targeted users. Tune thresholds to your environment and exclude trusted testing infrastructure only after review.

## Technology
Microsoft Sentinel · Microsoft Entra ID sign-in logs · KQL · YAML · GitHub Actions · MITRE ATT&CK concepts

## Responsible use
All identities, IP addresses and events in this repository are synthetic. IPs use documentation-only address ranges. Do not treat sample detections as production-ready without testing, baselining, and privacy review.

## License
MIT — see `LICENSE`.
