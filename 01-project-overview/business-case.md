# Business Case — PromoLeak Radar

**Organization:** Northline Market  
**Document status:** Draft — for internal discussion with Finance and Growth  
**Owners:** Finance (primary narrative) + Growth (policy and customer impact)

---

## Current situation

Northline Market is a **mid-sized e-commerce** retailer: big enough to run serious promo volume, still light on dedicated promo governance and deep fraud tooling compared to what Growth would like when campaigns get aggressive.

Promotions include sitewide and targeted coupons, **first-time buyer** discounts, and a **referral** program that pays out when referees hit defined milestones. Rules live partly in the commerce promo tool, partly in legacy configuration, and partly in “how we’ve always run the campaign” spreadsheets. Finance closes the books each month with a growing list of **why did margin after promo miss plan?** questions that cannot be answered from one dashboard.

---

## Business pain points

- **Duplicate accounts** and related identities used to claim first-time offers or referral rewards more than once.
- **First-time coupon reuse** across accounts that share payment, address, or device patterns (exact detection TBD with Engineering).
- **Referral misuse** — self-referrals, closed loops among linked accounts, or payouts before the business considers the referee “real.”
- **Coupon stacking** or ordering issues so effective discount exceeds what Growth thought they published, especially on **low-margin** products.
- **High discounts on low-margin SKUs** — either through category exclusions not enforced, or through combinations nobody tested before go-live.

Pain is not only “bad customers.” **Config mistakes** and **unclear ownership** of who can publish a stackable code show up in the same incident reviews as abuse.

---

## Impact on teams

| Team | How they feel it |
|------|------------------|
| **Finance / FP&A** | Margin variance explanations are slow; board asks get answered with partial data and caveats. |
| **Growth / Promotions** | Defensive about “Finance says we’re leaking” without a number they trust; afraid blunt caps will tank conversion. |
| **Engineering** | Interrupt-driven fixes; unclear priority between new features and promo guardrails. |
| **Data / BI** | Ad hoc pulls every time there’s a fire; no durable mart for “promo leakage” everyone agrees on. |
| **Customer Service** | Agents lack a single case view; goodwill credits patch over inconsistent internal decisions. |
| **Legal** | Brought in late when customer comms about clawbacks or restrictions were already drafted informally. |

---

## Proposed direction

Finish the **PromoLeak Radar** analysis phase: documented problem, stakeholders, requirements, processes, dashboard/data needs, UAT approach, and KPI framework.

Implementation direction (not decided in this document alone) is expected to combine:

1. **Rule and process fixes** where Growth and Legal agree — caps, stacking clarity, category exclusions, referral milestone tightening.
2. **Visibility** — reporting/dashboard so Finance and ops see flagged volume, campaign concentration, and queue depth without waiting for month-end.
3. **Workflow** — who investigates, how cases close, how CS learns disposition, how escalation runs when a code misbehaves at scale.

Heavy **fraud platform** spend stays off the table until requirements show it’s necessary; Northline Market may get far with better rules + reporting first.

---

## Expected benefits

- **Fewer dollars left on the table** from known failure modes (stacking, wrong category, referral gaming) once rules and monitoring match intent.
- **Less time in cross-team arguments** when everyone references the same definitions and extracts.
- **Faster containment** when a campaign runs hot — kill-switch, cap, or pause path with audit trail.
- **Cleaner handoff to Engineering** — sized backlog tied to acceptance criteria instead of reactive tickets only.
- **Better customer experience** when restrictions follow a documented path and CS has aligned scripts.

Quantified NPV and payback belong here after FP&A assigns a leakage range and Engineering/vendor quotes implementation. Until then, treat dollar claims as **TBD**.

---

## Risks of doing nothing

- Margin pressure continues; Finance loses confidence in promo-led growth narratives.
- Growth runs bigger campaigns without guardrails; each peak season **widens** exposure.
- Engineering stays in reactive mode; technical debt around promos compounds.
- Customer trust erodes if enforcement feels random; Legal exposure if comms don’t match terms.

---

## Recommendation

**Approve the analysis phase** and staff it with a named BA plus sponsor time for workshops. Use the deliverables in this repo (and the parallel folders under `02-` through `10-`) as the working package.

For **investment** beyond analysis: steer leadership toward **rule fixes + monitoring + investigation workflow** first; defer large vendor fraud buys until Northline Market knows which signals and volumes justify the cost.

---

## Approvals (business case)

| Name | Role | Agree / concerns | Date |
|------|------|------------------|------|
| | Finance sponsor | | |
| | Growth / Product delegate | | |
