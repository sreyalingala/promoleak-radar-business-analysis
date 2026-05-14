# KPI Framework: PromoLeak Radar

Rough yardsticks so we can tell if we’re plugging leaks without quietly trashing conversion or CS morale. Numbers stay TBD until FP&A and Data plug baseline.

## Headline metric (sponsor picks one)

**Candidate:** gross margin after promotions on the high-risk category set, weekly, with footnotes on what’s in the “abuse-related adjustment” bucket.

## Operational KPIs

| KPI | Definition sketch | Owner | Frequency | Notes |
|-----|-------------------|-------|-----------|-------|
| Flagged order volume | Count of orders meeting suspicion criteria | Ops | Daily | Watch false positives |
| Estimated leakage $ | Sum of flagged promo $ adjusted by confirmation rate | Finance | Weekly | Document the formula in the dashboard footnote so Growth can’t say we moved the goalposts |
| Confirmation rate | Confirmed abuse / all closed cases | Fraud/Ops | Weekly | Quality of signals |
| Mean time to contain | Time from first alert to campaign cap/kill for high-sev | Growth | Per incident | |
| Queue age | Age of oldest open case | Ops lead | Daily | Staffing signal |

## Growth / guardrail KPIs

| KPI | Why watch it |
|-----|----------------|
| Conversion on eligible segments | Catch over-tight rules |
| New customer count / CAC | Referral changes can move this |
| CS contacts tagged “discount dispute” | Customer experience pressure |

## Technical health

| KPI | Target |
|-----|--------|
| Pipeline success rate | TBD % |
| Dashboard load time | Per NFR |

## Reporting cadence

- Weekly ops huddle: flagged volume, queue depth, worst campaigns that week.
- Monthly with exec: margin after promo, confirmation rate, one concrete example if we have it (not mandatory to force a story).

## Fairness / sensitive attributes

If we start using attributes that could look like protected-class targeting, pull Legal / data ethics in **before** UAT, not a hypothetical for this doc until someone proposes those fields.
