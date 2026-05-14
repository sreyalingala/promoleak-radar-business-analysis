# Assumptions, Constraints, Risks — PromoLeak Radar

**Organization:** Northline Market  
**Project:** PromoLeak Radar (duplicate accounts, first-time coupon reuse, referral misuse, stacking, low-margin discount leakage)  
**Owner:** BA (maintain); Finance + PM sponsor updates after workshops.

Refresh this doc after major interviews, the future-state workshop, or any data sampling that proves an assumption wrong.

---

## Assumptions

| ID | Assumption | If this is wrong |
|----|------------|------------------|
| A-01 | Northline Market can access **order-level** promo application history for at least **12 months** in prod or cold storage. | Timeline slips; historical baselines shrink or require a rebuild. |
| A-02 | Most DTC orders tie to a **stable customer account id**; edge cases (guest, marketplace) are documented separately. | Identity resolution and rules scope balloon. |
| A-03 | Referral program rules (milestones, timing, eligibility) exist in **written** policy or admin docs, not only in one person’s head. | Extra discovery cycles; Legal may need to reconstruct terms. |
| A-04 | A **pilot** can narrow to one category, region, or campaign family without company-wide promo shutdown. | Big-bang pressure; harder to prove value with controlled risk. |
| A-05 | Growth and Finance will both attend at least one **joint** session to align on metric definitions. | BRD metrics section stays contested; UAT acceptance unclear. |
| A-06 | Fraud / Risk has capacity to review a **bounded** sample of flagged orders during pilot design — not infinite volume. | Queue design must be more conservative or staffing added. |

---

## Constraints

| ID | Constraint | Source | Notes |
|----|------------|--------|-------|
| C-01 | **Legal review** before customer-facing enforcement copy or mass messaging. | Legal | Build time into UAT and launch comms. |
| C-02 | **Peak season** engineering freeze or limited change windows for promo core. | Engineering | Schedule rule changes and releases around blackout dates. |
| C-03 | **BI / Data** hours for Northline Market are capped; MVP dashboard must stay small. | Data leadership | Three-to-five headline views first, not twenty tiles. |
| C-04 | **PII** handling: investigation views follow role-based access; no raw exports to unsecured drives. | Security / Legal | Applies to internal workpapers and portfolio copies. |
| C-05 | Promo rules and metadata still sit in **more than one system** until a consolidation project exists. | Current state | Requirements must name **authoritative** source per rule type. |
| C-06 | **Portfolio / public repo** must not hold real customer data — fictional or masked examples only. | This case study | Internal Northline Market wiki may hold real samples under policy. |

---

## Risks

| ID | Risk | Likelihood | Impact | Notes |
|----|------|------------|--------|-------|
| R-01 | **Metric definition fights** between Finance and Growth stall decisions. | Med | High | Naming a “headline” metric with footnotes buys time. |
| R-02 | **Data quality** under-counts leakage or hides category-specific holes. | Med | Med | Manual sample on known bad SKUs; document gaps in BRD. |
| R-03 | **Over-tight rules** hurt conversion; Growth pulls support for the program. | Med | High | Phased rollout; watch conversion and CS tags weekly after changes. |
| R-04 | **Alert fatigue** — too many flags → team mutes alerts or ignores queue. | Med | High | Start with fewer triggers; tune weekly in pilot. |
| R-05 | **Scope creep** into full payment fraud or identity replacement. | Med | Med | Charter boundaries; log out-of-scope requests for another initiative. |
| R-06 | **Key engineer** unavailable during discovery → gaps in as-is technical truth. | Med | Med | Book Eng Lead early; written follow-ups to understudies. |
| R-07 | **Legal delay** on comms templates blocks UAT exit for customer-visible flows. | Low–Med | Med | Early legal slot in communication plan. |

---

## Mitigation plan

| Risk ID | Mitigation | Owner | When |
|---------|------------|-------|------|
| R-01 | Joint **KPI review** session with pre-read; unresolved items escalated to Executive Sponsor within **5 business days**. | Finance Manager + BA | Before BRD sign-off track |
| R-02 | **Data review** session with Eng + Data + Fraud; parallel **manual sample** on 20–50 anonymized high-discount orders on low-margin SKUs. | Data Analyst | Week 2–3 of discovery |
| R-03 | **Pilot** on one category or code family; Growth agrees guardrail KPIs up front; rollback path documented. | Product Manager + Growth | Before rule changes hit prod |
| R-04 | MVP trigger list **capped** (e.g., max N rule types); weekly tuning meeting first month of pilot. | Fraud Analyst + Ops | Pilot window |
| R-05 | **Out-of-scope** list in workshop notes and charter; PM gates backlog. | Product Manager | Ongoing |
| R-06 | **Written** technical questions to Engineering if expert is absent; spike stories for unknowns. | BA + Eng Lead | Discovery |
| R-07 | Legal **checkpoint** scheduled in comms plan; templates drafted before UAT execution starts. | Legal + PM | Pre-UAT |

*(Add rows as new risks appear.)*

---

## Items needing stakeholder confirmation

Check off when confirmed; owner in parentheses.

- [ ] **Headline leakage metric** Finance will use in steering (and Growth can live with as a starting point) — *(Finance Manager, Executive Sponsor)*  
- [ ] **Pilot scope** — category, region, or campaign family for first controls — *(Growth + Finance + Sponsor)*  
- [ ] **“One customer”** definition for first-time and referral limits (account-only vs. enriched signals) — *(Legal, Eng Lead, Fraud)*  
- [ ] **Referral payout timing** vs. Finance recognition — documented single rule — *(Finance + Growth)*  
- [ ] **Marketplace / partner orders** in or out of v1 detection scope — *(Product + Data)*  
- [ ] **Kill-switch authority** and audit requirements when a code is capped mid-flight — *(Growth + Eng + Legal)*  
- [ ] **Investigation queue owner** and backup for PTO / weekends — *(Ops or Fraud + Sponsor)*  
- [ ] **Retention period** for investigation notes and exports — *(Legal)*  

---

## Sign-off (optional for this working document)

No formal sign-off required for the portfolio copy. At Northline Market, copy **high risks and mitigations** into the official risk register if the PMO requires it — avoid two conflicting versions.
