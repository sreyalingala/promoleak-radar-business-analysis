# Project Charter — PromoLeak Radar

**Document status:** Draft v0.1 — not yet signed off by sponsor  
**Last updated:** [Date TBD]

## What this charter is for

Sets boundaries for the BA work on promotion abuse / revenue leakage at a mid-sized retailer (working name **Northline Commerce**). Sponsor, product, finance, and ops should agree on what’s in and out of this phase. It does not pick architecture or vendors.

## Background

Finance keeps flagging a gap between “margin after promos” in the plan vs. what closes on certain categories. CS and fraud see the same stories on repeat: duplicate accounts, codes that stack when they shouldn’t, referral payouts that don’t line up with real new buyers. This effort is the paperwork side: problem statement, requirements, and what we’d want from detection + controls before build starts.

## Objectives

1. Quantify where leakage occurs (coupons, referrals, first-time buyer offers) and which product lines are most exposed.
2. Produce business and functional requirements for monitoring, alerting, and process changes.
3. Define dashboard and reporting needs so operations and finance can act on signals without waiting for ad hoc extracts.
4. Leave UAT themes and acceptance clear enough that whichever solution we pick (build vs. buy still open) can be exercised properly.

## Scope (in)

- Business analysis, process modeling, requirements, traceability, UAT planning, and impact/KPI framing.
- Assumptions and risks documented explicitly; dependencies on data quality and legacy promo engine called out.

## Scope (out)

- Implementation of production software (handled by engineering/vendor after handoff).
- Legal determination of “fraud” vs. “policy abuse” — we document business rules; legal reviews separately.

## Sponsor & decision rights

| Role | Name / area | Notes |
|------|-------------|--------|
| Executive sponsor | TBD — VP Finance or CFO delegate | Budget and policy trade-offs |
| Product owner | TBD — Promotions / Growth | Rule changes and customer-facing impact |
| BA lead | TBD | This documentation set |

## Success criteria (BA phase)

- Problem statement and top use cases aren’t stuck in “we’ll know it when we see it.”
- BRD + attachments are readable by eng for rough sizing (even if answers are still TBD).
- RTM links main asks to test themes; holes are labeled, not invisible.

## Open items

- Exact sponsor names and sign-off date.
- Whether “referral” scope includes partner/channel programs or DTC only.
