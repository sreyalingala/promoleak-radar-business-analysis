# To-Be Process — PromoLeak Radar Operating Model

**Goal:** Same business outcomes (sales, acquisition) with controlled promotional economics and faster, defensible reactions to abuse.

## Principles

- **Detect early:** batch or near-real-time flags feed a dashboard and optional alerts.
- **Decide with evidence:** investigator sees order facts, reason codes, and history.
- **Change rules deliberately:** campaign caps and stacking policy updates go through agreed change window with comms to CS.
- **Measure side effects:** watch conversion and CS volume after each material rule change.

## To-be flow (narrative)

1. **Design** — Growth proposes campaign with **pre-flight checklist**: margin floor, stack policy, sunset date, owner.
2. **Publish** — Dual-control or peer review for high-risk codes (threshold TBD by sponsor).
3. **Shop** — Checkout enforces published stacking and eligibility; edge cases logged as events for BI.
4. **Monitor** — Daily dashboard shows leakage indicators and new case volume; thresholds notify on-call role.
5. **Triage** — Cases assigned; investigators document outcome; false positives feed tuning backlog.
6. **Remediate** — Confirmed abuse paths: account restriction, clawback per policy, or code shutdown — **Legal-approved** playbooks.
7. **Retro** — Monthly review with Finance and Growth: metrics, false positive rate, and backlog of rule changes.

## Swimlane (text, to-be)

```
[Growth] checklist → publish → (monitoring)
[Engineering] events → warehouse → [Data] marts → [Dashboard]
[Investigator] queue ← alerts ← [Rules engine / scoring TBD]
[CS] updated macros + CRM case from outcome
[Finance] weekly metrics pack automated from same marts
```

## Handoffs

| From | To | Artifact |
|------|-----|----------|
| Data | Ops | Daily dashboard refresh confirmation |
| Investigator | CS | Case disposition note template |
| Growth | All | Change log entry when rule or cap changes |

## Dependencies

- Event instrumentation completeness.
- Staffing for investigation queue — if understaffed, alerts will be ignored.

## Not decided yet

- Build internal case tool vs. extend existing fraud case management — requirements written to be tool-agnostic where possible.
