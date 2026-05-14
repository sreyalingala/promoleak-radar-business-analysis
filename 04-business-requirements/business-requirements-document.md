# Business Requirements Document (BRD)

**Project:** PromoLeak Radar — Promotion abuse & revenue leakage detection  
**Version:** 0.1 draft  
**Audience:** Product, Engineering, Finance, Operations

## 1. Document control

| Field | Value |
|-------|--------|
| Author | BA (portfolio) |
| Reviewers | TBD |
| Related docs | FRD slice in `functional-requirements.md`, NFRs, business rules |

## 2. Business context

Northline Commerce uses coupons, first-time buyer incentives, and referral rewards as part of acquisition and retention. Finance and operations believe a meaningful portion of promotional value is captured by behavior that violates policy or exploits technical gaps (duplicate accounts, stacking, category misuse). The organization needs clarity, monitoring, and controlled responses without shutting down legitimate marketing.

## 3. Business objectives

1. Establish agreed definitions and categories for promotion-related leakage.
2. Provide visibility into volume, trend, and concentration (customer, SKU, campaign, channel).
3. Enable timely operational response (review queue, alerts, rule adjustments) with audit trail.
4. Reduce repeat abuse while documenting trade-offs on conversion and customer experience.

## 4. In scope

- Requirements for detection signals, dashboards, workflows, and rule changes **as a BA package**.
- UAT themes and acceptance aligned to business outcomes.

## 5. Out of scope

- Production code, vendor selection (captured as assumptions only).
- Full enterprise identity overhaul unless later approved as separate initiative.

## 6. Business capabilities required (summary)

| Capability | Description | Priority |
|------------|-------------|----------|
| Leakage visibility | Reports/dashboards on suspected abuse and margin impact | Must |
| Case handling | Queue or integration path for human review | Must |
| Rule governance | Who can publish/change codes; approval checkpoints | Should |
| Alerting | Threshold-based notifications to defined roles | Should |
| Historical audit | Explain why an order was flagged | Must |

## 7. Stakeholder needs (condensed)

- **Finance:** credible numbers, month-over-month trend, drill to campaign.
- **Growth:** ability to exempt or tune rules by segment with guardrails.
- **CS:** scripts and visibility when customers challenge decisions.
- **Engineering:** stable interfaces, clear priority on which signals first.

## 8. Acceptance at BRD level

BRD is “ready for solutioning” when: objectives and scope are signed; capability table prioritized; open questions list has owners.

## 9. Open questions

- Single owner for post-live rule changes?
- Geographic or legal differences for referral clawback?
