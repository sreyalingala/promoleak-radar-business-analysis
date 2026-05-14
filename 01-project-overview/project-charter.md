# Project Charter: PromoLeak Radar

**Organization:** Northline Market (fictional mid-sized e-commerce, portfolio case study)  
**Document status:** Draft, discovery phase, sponsor sign-off pending  
**Version:** 0.2  
**Last updated:** [Date]

---

## Project background

Northline Market runs coupons, first-time buyer incentives, and a customer referral program to stay competitive with larger marketplaces. Over the last few planning cycles, Finance has flagged that **margin after promotions** on several categories sits below plan, and the gap is not fully explained by traffic mix or list-price moves alone.

Customer service and the small fraud-adjacent team (where it exists) keep seeing the same complaint themes: rewards blocked, discounts removed, or customers insisting codes "used to work." Engineering has patched individual incidents, but there is no **one agreed view** for how much value is leaking through promos, where it clusters, or who owns the response when a campaign or rule set misbehaves.

PromoLeak Radar is the name given to this **business analysis** effort: document the problem, stakeholders, requirements, process changes, and what a monitoring/UAT path would look like **before** the company locks a build-or-buy decision for tooling.

---

## Problem statement

Northline Market is losing revenue through **promotion-related leakage**: duplicate accounts, reuse of first-time coupons, referral reward misuse, coupon stacking (including cases where application order or config does not match policy intent), and high discounts applied to **low-margin** SKUs that merchandising never meant to deep-discount.

The business lacks a shared, trusted view of leakage volume and drivers, and lacks a consistent operating model for detection, escalation, and rule changes. That gap drives rework, disputes between Growth and Finance, and late discovery after campaigns have already run hot.

*(A longer narrative lives in `problem-statement.md`.)*

---

## Business objectives

1. **Describe and bound** the leakage problem in business language Finance and Growth can both use.
2. **Produce requirements** (business, functional, non-functional, rules) so Engineering can size work and dependencies instead of guessing from tickets.
3. **Define reporting and dashboard needs** so ops and finance can see daily/weekly signals, not only month-end packs.
4. **Model as-is and to-be processes** including escalation when abuse or misconfiguration spikes.
5. **Prepare UAT themes and traceability** so whatever solution ships can be accepted against written criteria.
6. **Frame KPIs and cost/benefit** so leadership can weigh margin protection against conversion and customer experience.

---

## In scope

- BA discovery and documentation: charter, problem statement, business case, stakeholder analysis, elicitation, BRD/FR/NFR, business rules, process models, user stories, traceability, dashboard/data requirements at BA level, UAT plan and sample tests, KPI and impact notes.
- Explicit assumptions, constraints, risks, and open questions.
- Handoff pack suitable for **estimation** and **UAT planning**, not production implementation in this repo.

---

## Out of scope

- Writing or deploying production code, standing up pipelines, or selecting a vendor (analysis may *inform* vendor RFP later).
- Replacing Northline Market's core commerce platform or identity provider as part of this charter (separate initiative if ever).
- Legal/criminal fraud prosecution strategy; this effort documents **business rules** and **policy**; Legal reviews customer-facing enforcement separately.
- Redesign of marketing creative or full loyalty program strategy beyond what's needed to explain promo economics and controls.

---

## Success criteria

Charter phase is in good shape when:

- Executive sponsor and product owner names are filled in and **problem statement** is agreed at least at "directionally correct" level.
- **Top 3-5** priority scenarios (e.g., stacking on low-margin SKUs, referral self-dealing, duplicate first-time use) are written down with owners for business rules.
- BRD + FR/NFR drafts exist and Engineering has had one read-through for **feasibility flags** (not final estimate).
- Traceability matrix links main requirements to **test themes**; gaps are visible, not missing.
- Stakeholders accept that **Option** for tooling (build vs. extend vs. buy) stays open until requirements stabilize.

---

## Key stakeholders

| Role / group | Why they matter |
|--------------|-----------------|
| **VP Finance / CFO delegate** | Sponsor for margin story, budget, and board narrative |
| **Director, Growth / Promotions** | Owns campaign rules, caps, stacking policy, customer-facing trade-offs |
| **E-commerce / Product** | Checkout, cart, promo UX, release timing |
| **Engineering** | Promo engine, OMS integration, identity hooks, technical debt |
| **Data / BI** | Marts, dashboards, definitions of "flagged" orders |
| **Customer Service** | Tickets, goodwill credits, scripts when discounts change |
| **Legal / Compliance** | Terms, clawback language, what we can say to customers |
| **Fraud / Risk** (if separate from CS) | Investigations, case tooling, escalation patterns |
| **Merchandising / Category** | SKU margin floors, excluded categories |

Names and exact titles: **TBD**, replace with Northline Market org chart when formalizing.

---

## Assumptions

- Northline Market can access **order-level** promo application history for a meaningful lookback (target 12+ months; confirm with Data).
- A stable **customer account** key exists for most DTC orders; edge cases (guest checkout, marketplace) documented separately.
- Referral program rules (milestones, payout timing) exist in **writing** somewhere retrievable, if not, discovery takes longer.
- A **pilot** can narrow to one category or region if the business refuses a big-bang rule change.
- Legal will participate before any **customer-visible** enforcement copy goes live.

---

## Constraints

- **Peak season freeze:** Engineering has limited change windows near major shopping peaks, rule changes may need to wait or go through exception path.
- **BI capacity:** Dashboard work competes with other priorities; MVP reporting must stay small.
- **No PII in public portfolio copies** of docs if Northline Market later mirrors this structure externally, use masked examples outside internal systems.
- Promo rules and codes still sit in **more than one system**, the analysis has to spell out which tool is authoritative for which rule until someone funds a real consolidation.

---

## Risks

| Risk | What happens | Mitigation (working) |
|------|----------------|----------------------|
| Finance vs. Growth deadlock on caps | No decision; leakage continues | Sponsor-led session; pilot on worst category with agreed KPIs |
| Bad or incomplete data | Under-count leakage, wrong priorities | Manual sample on high-risk SKUs; document data gaps in BRD |
| Over-tight rules in a panic | Conversion drop, CS spike | Phased rollout; watch conversion and ticket tags weekly after changes |
| Scope creep into full payment fraud | Timeline and politics blow up | Keep charter boundaries visible; log out-of-scope asks |
| Key engineer only available near releases | Requirements holes | Book technical walkthrough early; record decisions |

---

## High-level timeline

Rough calendar for the **analysis phase** only (not implementation). Adjust once sponsor assigns dates.

| Phase | Duration (indicative) | Output |
|-------|----------------------|--------|
| Kickoff + charter / problem alignment | 1-2 weeks | Signed charter (target), agreed problem statement v1 |
| Stakeholder interviews + workshop | 2-3 weeks | Notes, decision log, updated assumptions/risks |
| Requirements + process | 3-4 weeks | BRD, FR/NFR, business rules, as-is/to-be |
| Solution-facing BA specs | 2 weeks | Dashboard reqs, data reqs, context diagram |
| UAT + impact pack | 1-2 weeks | UAT plan, test themes, KPI/CBA draft for sponsor |

**Total:** on the order of **8-12 weeks** of focused BA time, often parallelized with workshops, slips if holiday freeze or if Data cannot deliver sample extracts on time.

---

## Approval section

| Name | Role | Signature | Date |
|------|------|-----------|------|
| | Executive sponsor (Finance) | | |
| | Product owner (Growth / E-com) | | |
| | BA lead | | |

**Notes:** Charter does not obligate capital spend; it authorizes analysis work and sets expectations for handoff. Budget for implementation is a separate approval after estimates land.
