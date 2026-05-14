# Business Case — PromoLeak Radar

**Document status:** Working draft for internal discussion  
**Owner:** Finance + Growth (joint)

## Situation

Northline Commerce runs aggressive promotions to compete with larger marketplaces. Margin reports show pressure that cannot be fully explained by list-price competition alone. Internal reviews suggest a mix of intentional abuse, grey-area behavior, and process gaps (e.g., codes that were never meant to stack still stacking after a config change).

## Why act now

- Finance needs repeatable numbers for board reporting; one-off spreadsheets are slow and contested.
- Customer support escalations tied to “blocked rewards” or “removed discounts” are up quarter over quarter (exact % TBD once data pulled).
- Any future loyalty or referral expansion without controls will widen the hole.

## Options considered (high level)

| Option | Summary | Trade-off |
|--------|---------|-----------|
| A — Status quo + manual audits | Keep current tools; periodic manual reviews | Cheap short-term; does not scale; inconsistent |
| B — Process + rule tightening only | Cap discounts, tighten eligibility, no new tooling | Reduces leakage but may hurt conversion; still blind to patterns |
| C — B + monitoring dashboard + alerts | Same as B plus visibility and workflow | Requires data work and ownership; **recommended direction for analysis** |
| D — Full fraud platform | Vendor or large internal build | Higher cost; may be overkill until requirements clear |

## Financial view (placeholder)

Real NPV/payback waits on FP&A for a leakage range and eng/vendor for implementation cost. Until then:

- **Annual leakage under review:** TBD — needs finance model, not my guess.
- **Cost of delay:** each quarter without agreed metrics, the same meeting gets rerun with different spreadsheets.

## Recommendation (for charter stage)

Use **Option C** as the working story for this analysis: fix the obvious rule issues where Growth and Legal will sign, but don’t skip monitoring + escalation. Otherwise we tighten promos blind and still fight about whether it worked.

## Approvals

| Approver | Role | Signed | Comments |
|----------|------|--------|----------|
| | | | |
