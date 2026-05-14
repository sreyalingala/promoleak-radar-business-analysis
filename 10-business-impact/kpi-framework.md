# KPI Framework — PromoLeak Radar

**Intent:** Measure whether we are reducing leakage without silently damaging growth or customer experience. Numbers are examples until baseline captured.

## North star (pick one with sponsor)

**Candidate:** *Gross margin after promotions on high-risk categories* — week over week, with abuse flags explained.

## Operational KPIs

| KPI | Definition sketch | Owner | Frequency | Notes |
|-----|-------------------|-------|-----------|-------|
| Flagged order volume | Count of orders meeting suspicion criteria | Ops | Daily | Watch false positives |
| Estimated leakage $ | Sum of flagged promo $ adjusted by confirmation rate | Finance | Weekly | Method transparent |
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

- **Weekly ops huddle:** flagged volume, queue, top campaigns.
- **Monthly exec:** margin after promo, confirmation rate, one story on a prevented loss if available.

## Ethics / fairness note

If rules touch sensitive attributes, add fairness review steps — **only if applicable** after Legal/Data ethics input.
