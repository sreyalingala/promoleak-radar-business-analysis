# Non-Functional Requirements (NFRs)

**Project:** PromoLeak Radar  
**Note:** Targets are starting points for discussion with Engineering and Security. Replace TBD with agreed SLAs.

## Performance

| ID | Statement |
|----|------------|
| NFR-01 | Dashboard primary views shall load within **TBD seconds** for typical date ranges on standard office networks. |
| NFR-02 | Overnight batch completion before **TBD local time** for prior-day metrics used in morning ops review. |

## Security & privacy

| ID | Statement |
|----|------------|
| NFR-10 | Role-based access: only fraud/investigation roles see PII needed for case review; finance sees aggregates unless approved. |
| NFR-11 | Audit logs retained per **organizational retention policy** (link TBD). |
| NFR-12 | No production customer data in development environments without masking approval. |

## Availability & reliability

| ID | Statement |
|----|------------|
| NFR-20 | Target uptime for monitoring UI: **TBD** (e.g., 99.5% excluding planned maintenance). |
| NFR-21 | If the “near real-time” path dies, batch numbers should still load with a clear “stale / partial” banner — not a silent wrong day. |

## Usability

| ID | Statement |
|----|------------|
| NFR-30 | Primary dashboards usable by a trained finance or ops analyst **without SQL**. |
| NFR-31 | Filters and reason codes use the same words CS and Growth use in meetings; glossary doc still TBD. |

## Maintainability & support

| ID | Statement |
|----|------------|
| NFR-40 | Threshold and rule metadata versioned; users can see **what version** produced a flag for a given date. |
| NFR-41 | Runbook location documented for on-call (owner TBD). |

## Compliance

| ID | Statement |
|----|------------|
| NFR-50 | Customer comms templates for enforcement actions reviewed by Legal before production use. |

## Observability

| ID | Statement |
|----|------------|
| NFR-60 | Pipeline jobs emit success/failure metrics and alerts to **TBD channel**. |
