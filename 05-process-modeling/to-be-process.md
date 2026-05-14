# To-Be Process — PromoLeak Radar Operating Model

**Goal:** Still sell stuff and acquire customers — but stop funding obvious abuse and catch bad configs before they run for two weeks unchecked.

## How we want it to feel day-to-day

- Flags land in a dashboard (batch is fine at first); alerts only if thresholds are tuned so people don’t mute the channel.
- Investigator can see order lines, codes, reason codes, history — not a CSV hunt.
- Rule changes (caps, stacking) go through a small change window + CS heads-up so agents aren’t improvising.
- After a material rule change, someone actually looks at conversion and CS tags for a week instead of assuming it was fine.

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

| From | To | What gets handed off |
|------|-----|----------|
| Data | Ops | “Yesterday’s job ran clean” (or not — then banner on dashboard) |
| Investigator | CS | Short disposition note agents can read |
| Growth | All | Change log line when a cap or stack rule moves |

## Dependencies

- Checkout/OMS actually emitting the events we said we need — otherwise the dashboard is theatre.
- Bodies on the investigation queue; if it’s nobody’s job, alerts get ignored.

## Not decided yet

- New case tool vs. bolt onto whatever fraud/CRM we already pay for — reqs here stay tool-agnostic on purpose.
