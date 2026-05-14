# Assumptions, Constraints, Risks

**Project:** PromoLeak Radar  
Update this when workshops turn up new facts or when data proves an assumption wrong.

## Assumptions

| ID | Assumption | Implication if wrong |
|----|------------|----------------------|
| A-01 | Northline Market can access order-level promo application history for at least 12 months | Timeline slips if archives incomplete |
| A-02 | “Customer” can be tied to a stable account key for most DTC orders | Identity resolution work grows scope |
| A-03 | Referral program rules are documented somewhere retrievable | Extra discovery if only in people’s heads |
| A-04 | Pilot can start on one category or region without full enterprise rollout | Reprioritize if business insists on big-bang |

## Constraints

| ID | Constraint | Source | Notes |
|----|------------|--------|-------|
| C-01 | No customer PII in this portfolio GitHub repo | Security policy | Use fictional examples here |
| C-02 | Legal review before customer-facing enforcement copy | Legal | Plan buffer |
| C-03 | BI team bandwidth capped at X hours/week | Data leadership | Dashboard MVP must be small |
| C-04 | Promo engine major version freeze near peak season | Engineering | Change windows limited |

## Risks

| ID | Risk | Likelihood | Impact | Mitigation (draft) |
|----|------|------------|--------|---------------------|
| R-01 | Metrics definitions argued endlessly | Med | Med | Start with one “headline” metric + footnotes |
| R-02 | Growth and Finance deadlock on caps | Med | High | Sponsor decision forum; pilot evidence |
| R-03 | Data quality gaps understate leakage | High | Med | Parallel manual sample on high-risk SKUs |
| R-04 | Over-aggressive rules increase churn | Med | High | Gradual rollout; monitor conversion cohorts |
| R-05 | Scope creep into full payment fraud | Med | Med | Explicit out-of-scope in charter |

## Dependencies

- Identity graph or dedupe logic owned by [team TBD].
- Referral vendor API limits / webhook delays — confirm with Engineering.

## Sign-off

This page is a working note. If the company keeps a formal risk register in PMO tooling, copy the high items over — don’t maintain two conflicting lists.
