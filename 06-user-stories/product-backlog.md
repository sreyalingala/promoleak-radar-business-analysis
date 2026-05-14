# Product Backlog — PromoLeak Radar (MVP-oriented)

**Notes:** Priority column is for planning fights, not a contract. IDs are just for tracing.

## Backlog

| ID | Theme | Short title | Priority | Notes |
|----|-------|-------------|----------|-------|
| PB-01 | Visibility | Daily leakage summary dashboard | Must | Finance + ops |
| PB-02 | Visibility | Drill-down to orders with reason codes | Must | Permissions model |
| PB-03 | Detection | Configurable thresholds with owner | Should | Phased if complex |
| PB-04 | Workflow | Investigation queue with statuses | Must | May start as spreadsheet-backed process |
| PB-05 | Workflow | False positive feedback capture | Should | Feeds tuning |
| PB-06 | Rules | Enforce stacking policy in checkout | Must | Eng-heavy; may split spikes |
| PB-07 | Rules | Category margin floor flags | Should | Needs reliable COGS |
| PB-08 | Referral | Payout delay / additional checks | Should | Policy + eng |
| PB-09 | CS | Agent view of case + disposition | Should | Integration TBD |
| PB-10 | Governance | Pre-flight campaign checklist | Could | Process + light tooling |
| PB-11 | Alerting | Email/Slack alert on threshold breach | Should | Avoid noise |
| PB-12 | Audit | Export case history for audit | Must | Scope columns with Legal |

## Dependencies (high level)

- PB-01/02 depend on data model in `08-solution-design/data-requirements.md`.
- PB-06 may be prerequisite or parallel to PB-03 depending on architecture choice.

## Parking lot

- Partner marketplace-specific backlog items — deferred until scope includes partners.

## Refinement log

| Date | Change |
|------|--------|
| | Initial placeholder backlog |
