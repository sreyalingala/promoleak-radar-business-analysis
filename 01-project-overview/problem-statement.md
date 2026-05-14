# Problem Statement — Promotion Abuse & Revenue Leakage

**Organization:** Northline Market  
**Program:** PromoLeak Radar  
**Document status:** Draft v1 — for sponsor and cross-functional review

---

## Problem statement

Northline Market is experiencing **promotion-related revenue leakage**: promotional value is leaving the business through duplicate accounts, first-time coupon reuse, referral reward misuse, coupon stacking that exceeds policy intent, and high effective discounts applied to **low-margin products**. The company does not yet have a single, trusted way to measure that leakage, prioritize fixes, or run a consistent response when promos misbehave. As a result, margin outcomes are worse than plan in affected categories, internal teams spend excessive time reconciling different views of the same orders, and customers sometimes see enforcement that feels arbitrary.

---

## Evidence observed

Evidence below mixes **Finance and CS themes** with **engineering incident history** — still needs to be backed by a formal data pull; treat as the working list of what people are seeing in meetings and tickets.

- **Margin after promotions** below plan on specific categories quarter over quarter; variance memos cite “promo mix” as a recurring line item.
- **Duplicate or clustered accounts** opening orders with first-time or high-value codes in short windows; fraud/CS anecdotes (counts TBD).
- **Referral payouts** where referee behavior does not match a “normal” new customer path (e.g., immediate churn, same payment fingerprint as referrer — definitions TBD with Legal).
- **Stacking outcomes** that do not match what Growth believed they published — sometimes traced to application order, sometimes to a config push that did not match the runbook.
- **Low-margin SKUs** (e.g., consumables, accessories tied to low-list categories) showing **effective discounts** category managers describe as “not approved at that depth.”
- **Late discovery:** issues often surfaced after a campaign peaked, when Finance deep-dives or when CS volume spikes.

---

## Root cause themes

These are **themes** for discovery — not a final RCA. Engineering and Data will validate.

1. **Policy vs. system mismatch** — What Growth intends (stack rules, one-per-customer, category exclusions) is not always what checkout and the promo engine enforce.
2. **Identity and eligibility** — “One customer” is not consistently defined across account, email, device, and payment signals; duplicate account creation exploits that gap.
3. **Referral design and timing** — Payout triggers or milestones may be too early or too loose relative to genuine acquisition economics.
4. **Operational gaps** — No single owner for pre-flight checks on high-risk campaigns; weak handoff when Finance flags a code as “too hot.”
5. **Reporting gap** — No agreed mart or dashboard for “suspected leakage” orders, so decisions rely on partial exports and debate.

---

## Business impact

- **Financial:** Erosion of gross margin after promotions on affected SKUs and campaigns; harder to forecast promo ROI.
- **Operational:** Hours lost in cross-team reviews; repeated ad hoc analyses; Engineering pulled into emergency fixes.
- **Customer / brand:** Disputes over removed rewards or blocked accounts; inconsistent agent handling when internal policy is unclear.
- **Strategic:** Growth may resist scaling referral or aggressive coupons until Finance can show **controlled** economics — slowing initiatives Northline otherwise wants to run.

---

## What needs to change

- **Written definitions** of abuse categories and which team owns each rule type (Growth vs. Finance vs. Legal for customer-facing).
- **Aligned technical behavior** with those definitions — or explicit acceptance of technical limits until a fix ships.
- **Reporting and monitoring** so leakage and campaign concentration are visible on a cadence Finance and ops can act on.
- **Escalation and case handling** when automated flags or finance review identify a pattern requiring cap, pause, or investigation.
- **UAT and acceptance criteria** tied to requirements so “fixed” means measurable, not subjective.

---

## What success would look like

- Northline agrees on **one** headline definition (or small set) of “suspected leakage” for internal management, with footnotes where data is weak.
- **Top leakage modes** have named owners, documented rules, and a path to engineering backlog with priorities.
- **Dashboard or report pack v1** exists (after build) so daily/weekly review is possible without custom SQL for standard questions.
- **Fewer repeat incidents** of the same stacking or category hole; when they occur, postmortem links to a requirement or test gap.
- Growth and Finance can argue from **the same numbers** in steering meetings, even if they still disagree on policy.

---

## Out of scope (this problem statement)

- Choosing a specific fraud vendor or ML approach — out of scope **here**; may follow from requirements.
- Full replacement of Northline’s identity stack — only noted if analysis proves it’s a hard dependency.
- Criminal referral or law-enforcement process — outside this BA problem statement unless Legal opens a separate track.
