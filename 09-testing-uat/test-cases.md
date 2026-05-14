# Test Cases (Sample Set)

Starter pack for UAT — extend when fixtures and real campaign codes exist.

**Project:** PromoLeak Radar  
**Prefix:** TC-* maps to RTM when filled.

## Reporting

### TC-REPORT-01 — Daily summary loads for standard date

| Field | Value |
|-------|--------|
| Preconditions | Pipeline successful for D-1; user has finance analyst role |
| Steps | 1. Open dashboard. 2. Select yesterday. 3. Record headline numbers. |
| Expected | Totals visible; footnote for “at risk” present; refresh timestamp ≤ SLA |
| Priority | High |

### TC-REPORT-02 — Filter by campaign

| Field | Value |
|-------|--------|
| Preconditions | Known synthetic campaign `TEST-SUMMER` has flagged orders in fixture set |
| Steps | 1. Open overview. 2. Filter campaign = `TEST-SUMMER`. |
| Expected | Only relevant orders/campaigns appear; totals reconcile to detail export (tolerance TBD) |
| Priority | High |

## Workflow

### TC-WF-01 — Status transition audit

| Field | Value |
|-------|--------|
| Preconditions | Investigator role; open case C-100 |
| Steps | 1. Set status In review → Confirmed abuse. 2. Save. 3. Reopen history. |
| Expected | Two entries with timestamps and user IDs; prior status preserved |
| Priority | High |

### TC-WF-02 — Unauthorized access denied

| Field | Value |
|-------|--------|
| Preconditions | CS role without investigator grant |
| Steps | 1. Attempt deep link to investigator-only order pane. |
| Expected | Access denied message; attempt logged |
| Priority | High |

## Rules / promo admin

### TC-RULE-01 — Cap change applies to new carts

| Field | Value |
|-------|--------|
| Preconditions | Authorized growth test user; code `TEST-CAP` active |
| Steps | 1. Note current cap. 2. Lower cap. 3. Place new checkout using code until cap. |
| Expected | New cap enforced within agreed latency; audit row written |
| Priority | High |

## Negative / edge

### TC-EDGE-01 — Pipeline failure banner

| Field | Value |
|-------|--------|
| Preconditions | Simulate failed promo facts job in non-prod |
| Expected | Dashboard shows maintenance / stale banner; does not show misleading “green” day |
| Priority | Medium |

## Data reconciliation (finance)

### TC-FIN-01 — Tie-out sample

| Field | Value |
|-------|--------|
| Preconditions | Finance provides 10 anonymized order IDs with expected flag state |
| Steps | Compare dashboard/export to expected |
| Expected | Match rate ≥ **TBD %** or discrepancies logged as defects |
| Priority | High |

---

Additional cases to add after workshops: referral-only abuse, partial refunds, marketplace orders.
