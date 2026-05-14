# Dashboard Requirements: PromoLeak Radar (Northline Market)

**Project:** PromoLeak Radar  
**Audience:** Finance, Marketing / Growth, Fraud / Risk, Operations, Compliance / Legal, Product, Data  
**Status:** Solution design draft after discovery and process modeling. Numbers and thresholds stay TBD until sponsors sign.

This document describes what each dashboard page is for, who uses it, and which BRD items it supports. It does not pick a BI vendor or prescribe SQL.

---

## Global behavior (all pages)

- **Footnotes:** Headline dollars use the Finance-approved leakage definition (BR-018, FR-006, US-012, US-022). When the definition version changes, the UI shows version and effective date.
- **Filters (MVP):** Date range, campaign, coupon code, category or department, channel, flag type (FR-013). Default window is something Ops can defend (example: rolling 7 days plus yesterday close).
- **Freshness:** Show last successful warehouse refresh and a banner if a feed is late (FR-008 stale banner pattern applies to read models, not only the queue screen).
- **Access:** Role-based views and exports (FR-014, FR-015, NFR-003, NFR-011). Aggregate-only roles never see full investigation panes.
- **Exports:** Only where Legal approved column sets exist; export is logged (FR-014, FR-012).

---

## 1. Executive Overview

**Purpose:** Give the Executive Sponsor a short, Finance-aligned read on whether promotion leakage is getting worse and where to ask follow-up questions.

**Primary users:** Executive Sponsor, Finance Manager (read), Product Manager.

**Key questions answered**

- Are estimated leakage dollars and abuse rates up or down vs the prior period?
- Which single campaign or code most deserves a conversation this week?
- Did manual review volume or SLA breaches spike in a way that signals operational strain?

**KPIs shown (examples)**

- Estimated revenue leakage (Finance definition, BR-018)
- Coupon abuse rate (flagged promo discount dollars divided by a Finance-owned denominator; footnoted)
- Gross margin impact (directional, where COGS is trusted on flagged orders)
- Manual review volume (new plus in-review)
- SLA breach count
- Redemption spike count (from alert log or threshold crossings, FR-018)

**Filters needed**

- Date, channel, high-level category rollup (fewer slices than analyst pages).

**Drill-down needs**

- Link to **Campaign Performance** or **Revenue Leakage** for one campaign (authorized roles only).
- No raw PII on this page for aggregate-only roles.

**Related requirement IDs**

- FR-006, FR-013, FR-014, FR-015, FR-018, BR-018, NFR-001, NFR-010

**Business decisions supported**

- Go or pause escalation on a live code (pairs with FR-017 and BR-014 in ops practice).
- Whether to fund a deeper Fraud or Data investigation based on trend, not one noisy day.

---

## 2. Campaign Performance

**Purpose:** One place for Marketing / Growth and Finance to look at the same campaign and code outcomes, including promo cost, revenue attribution, and leakage proxy.

**Primary users:** Marketing / Growth Manager, Finance Manager, Data Analyst.

**Key questions answered**

- Which campaigns paid back and which ones bought low-quality or abusive demand?
- How deep were discounts on average, and how does that compare to plan?
- Where does the leakage proxy sit relative to spend so we do not confuse a big campaign with a bad campaign?

**KPIs shown**

- Campaign ROI (definition agreed with Finance; footnote if Marketing still uses a secondary view, FR-006, US-013)
- Average discount per order (campaign scope)
- Estimated revenue leakage attributed to the campaign (subset of BR-018 numerator)
- Gross margin impact on flagged orders within the campaign
- Redemption spike count (per campaign)

**Filters needed**

- Date, campaign, code, channel, category, flag type (FR-013).

**Drill-down needs**

- From campaign row to **Revenue Leakage** detail for that campaign.
- From campaign to **Abuse Detection** reason mix for that campaign.
- Optional link to **Manual Review Queue** pre-filtered to the campaign (FR-008).

**Related requirement IDs**

- FR-006, FR-013, FR-014, FR-017, FR-018, BR-010, BR-014, BR-018, NFR-010

**Business decisions supported**

- Change caps, audience, or stack rules on the next drop.
- Trigger kill-switch or cap (FR-017) when redemption or flags cross policy (BR-014).

---

## 3. Revenue Leakage

**Purpose:** Quantify suspected leakage dollars and trends using the signed definition, so Finance can tie out and Marketing cannot argue from a different export.

**Primary users:** Finance Manager, Fraud / Risk Analyst, Data Analyst.

**Key questions answered**

- How much flagged promo discount sits in the numerator for the period, and what did we exclude (cancelled, test, margin unknown)?
- Which campaigns and codes moved the week?
- How much of the total is referral-related vs coupon vs stacking vs margin floor?

**KPIs shown**

- Estimated revenue leakage (BR-018)
- Gross margin impact (trusted COGS subset)
- Average discount per order on flagged orders
- Coupon abuse rate (Finance-owned formula, labeled clearly)
- Duplicate account rate (orders with duplicate signal divided by eligible orders, definition footnoted)
- Referral abuse rate (referral-flagged events over eligible referral orders, footnoted)

**Filters needed**

- Date, campaign, code, category, channel, flag type, reason code family (FR-013).

**Drill-down needs**

- Order list for investigators (FR-006 drill, role gated).
- Toggle to include or exclude policy exceptions if Finance publishes that rule (FR-016, BR-017, BR-018).

**Related requirement IDs**

- FR-005, FR-006, FR-013, FR-014, FR-015, FR-016, BR-006, BR-012, BR-018, NFR-010

**Business decisions supported**

- Month-end accrual conversations, board pack numbers, and prioritizing which rule families to tune first.

---

## 4. Abuse Detection

**Purpose:** Show pattern health for duplicate accounts, first-time reuse, stacking, referral abuse, and margin floor breaches so Fraud and Growth can tune with Ops.

**Primary users:** Fraud / Risk Analyst, Marketing / Growth Manager, Operations Manager.

**Key questions answered**

- Which signal types fired most often, and what is the false positive review rate from queue dispositions?
- Are first-time or referral issues concentrated in a channel or category?
- Is stacking concentrated on a small set of codes?

**KPIs shown**

- Coupon abuse rate (by signal family)
- Duplicate account rate
- Referral abuse rate
- False positive review rate (dispositions marked false positive over closed cases in period, FR-011)
- Counts by reason code (stack, margin floor, referral loop, shared payment, device, address)
- Redemption spike count (global or by code)

**Filters needed**

- Date, campaign, code, category, channel, flag type, signal type (FR-013).

**Drill-down needs**

- From a reason code bucket to **Manual Review Queue** filtered view.
- Optional account-level rollups for investigator roles only (FR-002, FR-007, NFR-003).

**Related requirement IDs**

- FR-001, FR-002, FR-003, FR-004, FR-005, FR-007, FR-008, FR-011, FR-018, BR-001, BR-002, BR-005, BR-007, BR-008, BR-009, NFR-001

**Business decisions supported**

- Threshold changes, allowlist updates, and referral policy edits backed by observed volume and false positives.

---

## 5. Manual Review Queue

**Purpose:** Single working list for triage, assignment, SLA visibility, and disposition (FR-008 through FR-011).

**Primary users:** Fraud / Risk Analyst, Operations Manager, Customer Support Manager (read or limited actions per RACI).

**Key questions answered**

- What is new, what is assigned to whom, and what is about to breach SLA?
- Which cases need Growth or Legal before we message a customer?
- What did we already decide, and can we trust the notes for a dispute later?

**KPIs shown**

- Manual review volume (new, in review, waiting on Growth, waiting on Legal, closed)
- SLA breach count
- False positive review rate (for tuning, not for investigator scorecards)
- Average age of open cases
- Optional: risk tier mix if FR-007 is in scope (FR-007, BR-011)

**Filters needed**

- Date, assignee or pool, status, campaign, code, flag type, SLA state, risk tier (FR-008, FR-009, FR-010, FR-013).

**Drill-down needs**

- Order and case detail with reason codes, score version id if present, assignment history, disposition form (FR-011).
- Link out to customer account context within policy (FR-015).

**Related requirement IDs**

- FR-007, FR-008, FR-009, FR-010, FR-011, FR-012, FR-015, FR-016, BR-011, BR-013, BR-017, NFR-003, NFR-005, NFR-006

**Business decisions supported**

- Staffing the queue, escalation to Marketing or Legal, and closing the loop with structured outcomes for CS and Finance.

---

## 6. Customer Risk Segments

**Purpose:** Summarize how many accounts or customers sit in coarse risk buckets so Product and Fraud can talk about volume without opening every account.

**Primary users:** Fraud / Risk Analyst, Product Manager, Data Analyst.

**Key questions answered**

- How many accounts are in each risk tier or score band?
- Which segments drive most flagged dollars?
- After a rule change, did the distribution shift the way we expected?

**KPIs shown**

- Account or customer counts by risk tier (FR-007)
- Estimated revenue leakage by tier (subset, BR-018)
- Duplicate account rate within tier (labeled methodology)
- Referral abuse rate within tier (where referral flags apply)

**Filters needed**

- Date, channel, category, campaign (optional), score version id (FR-007 explainability).

**Drill-down needs**

- From a tier to **Abuse Detection** reason mix, then to **Manual Review Queue** for that segment (role gated).
- No public customer identifiers on aggregate-only roles (FR-015).

**Related requirement IDs**

- FR-002, FR-007, FR-013, FR-015, BR-011, NFR-003, NFR-011

**Business decisions supported**

- Whether to widen or narrow review, and whether Marketing should change acquisition incentives for a risky segment.

---

## 7. Policy Exceptions

**Purpose:** Make goodwill and VIP exceptions visible so they do not look like silent shadow promos (FR-016, BR-017).

**Primary users:** Customer Support Manager, Compliance / Legal Representative, Finance Manager.

**Key questions answered**

- Which exceptions are active, who approved them, and when do they expire?
- How much discount or benefit sat under exceptions in the period?
- Are any exceptions missing approver separation or reason codes?

**KPIs shown**

- Active exception count and expired in period
- Estimated financial exposure under exceptions (Finance definition)
- Manual review volume tied to exception-related orders (if tagged)

**Filters needed**

- Date, requester, approver, scope (account or order), status (FR-016).

**Drill-down needs**

- To related case or order in **Manual Review Queue** when linked.
- To **Revenue Leakage** with Finance toggle for include or exclude exceptions (FR-016, BR-018).

**Related requirement IDs**

- FR-016, FR-012, FR-014, BR-017, BR-018, NFR-005

**Business decisions supported**

- Audit readiness, policy tightening, and clear accountability when exceptions drive margin surprises.

---

## Open items (solution design)

- Exact KPI formulas and denominators: Finance publishes and versions (BR-018, NFR-010).
- Whether **Customer Risk Segments** ships in pilot v1 or right after queue stabilization (FR-007 is Should in the BRD).
- Marketplace orders: exclude or footnote until data is trustworthy (BRD parking lot).
