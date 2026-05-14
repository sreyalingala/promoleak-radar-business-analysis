# Business Requirements Document (BRD): PromoLeak Radar

> **Note:** This BRD is a portfolio artifact for **Northline Market** (fictional). Content reflects discovery **assumptions** and BA judgment. A live engagement would need sign-off from Finance, Growth, Legal, and Product on scope, metrics, and rules before build.

**Project:** PromoLeak Radar (promotion abuse and revenue leakage)  
**Organization:** Northline Market  
**Version:** 0.3 draft  
**Audience:** Product, Engineering, Finance, Fraud or Risk, Data, Customer Support, Operations, Legal  
**Related artifacts:** `functional-requirements.md`, `non-functional-requirements.md`, `business-rules.md`, process and solution design folders

---

## Document purpose

Give Northline Market a single place to read **what** PromoLeak Radar must achieve in business terms, **who** it serves, **what** is in and out of scope, and **how** we will know it succeeded. Detailed behavior sits in functional requirements, NFRs, and business rules. This BRD is the bridge between charter or problem statement and those lower-level specs.

---

## Project background

Northline Market is a mid-sized e-commerce company. Promotions (first-time discounts, coupons, referrals) drive acquisition and repeat purchase. Finance has seen **margin after promotions** miss plan on several categories. Customer support and fraud-related roles see repeat issues: duplicate accounts, first-time code reuse, referral reward misuse, coupon stacking that does not match what Growth intended, and discounts that land too deep on **low-margin** SKUs.

Engineering has fixed incidents one at a time. There is no durable program tying **policy**, **data**, **monitoring**, and **human review** together. PromoLeak Radar is the analysis and requirements package to fix that gap before Northline Market commits to a specific product build or vendor.

---

## Business problem

Revenue leaks through promotion mechanics. The company lacks a **shared** view of how much is at risk, which campaigns or SKUs concentrate the pain, and how to **detect**, **review**, and **respond** without constant ad hoc spreadsheets and Slack threads. Growth and Finance can talk past each other because definitions and systems do not line up.

---

## Current-state summary

- Promo rules and campaign config may live in **more than one** system or spreadsheet; checkout behavior does not always match the runbook Growth thought they published.
- **Leakage signals** are found late (often month-end), via manual pulls or CS volume spikes.
- **Investigation** is inconsistent: sometimes Fraud, sometimes Finance, sometimes no owner; evidence and outcomes are not always visible to CS.
- **Kill or cap** a code may require an engineering emergency; audit of who changed what is weak in places.
- **Reporting** for “suspected abuse” is not a first-class product; definitions differ by team.

---

## Future-state summary

Northline Market agrees on **written** business rules and detection triggers (see `business-rules.md` and functional requirements). **Batch or near-time** scoring flags suspicious orders or campaigns. Finance and ops see **campaign-level leakage** and redemption trends on a dashboard with filters and exports. A **manual review queue** supports assignment, SLA visibility, decisions, and an **audit trail**. Authorized roles can use a **kill-switch** or cap on high-risk campaigns when thresholds breach. **Alerts** fire on unusual redemption spikes. **Role-based access** limits PII. **Policy exceptions** follow an approval path instead of informal overrides.

Exact tooling (build, extend, buy) stays open until engineering sizes this BRD.

---

## Business objectives

1. Reduce promotion-related revenue leakage from duplicate accounts, first-time coupon reuse, referral misuse, stacking, and inappropriate discounts on low-margin products, within agreed conversion guardrails.
2. Give Finance and leadership **credible** reporting on suspected leakage and campaign concentration (definitions owned and documented).
3. Give Fraud or Risk and Operations a **repeatable** review path with clear ownership, SLAs, and disposition visible to Customer Support where needed.
4. Tie technical changes to **published** policy and legal constraints so customer-facing actions are defensible.
5. Prepare the organization for **UAT** and post-go monitoring with explicit success metrics.

---

## In scope

- Business requirements for detection, scoring, review workflow, dashboard and exports, alerts, kill-switch behavior, audit, and access control at the **requirements** level.
- Cross references to functional and non-functional requirements and business rules.
- Assumptions, constraints, dependencies, and risks that affect delivery or policy.
- Success metrics for the program (not only for one release).

---

## Out of scope

- Production implementation, vendor selection, or contract negotiation (informed by this BRD, not replaced by it).
- Full replacement of Northline Market’s commerce platform, identity provider, or payment processor as part of PromoLeak Radar.
- Criminal fraud prosecution or law enforcement coordination (separate track if ever).
- Creative redesign of loyalty or referral **marketing** beyond what is needed for controls and messaging.

---

## Stakeholder needs

| Stakeholder | Need |
|-------------|------|
| **Executive Sponsor** | Short proof that money and reputation risk are managed; decisions when Finance and Growth disagree |
| **Marketing / Growth Manager** | Ability to run promos without surprise caps; clear rules for kill-switch; visibility before customer-visible changes |
| **Finance Manager** | Trusted metrics, drill to campaign and SKU, audit for numbers shown to leadership |
| **Fraud / Risk Analyst** | Queue, reason codes, evidence pack, false positive feedback, manageable volume |
| **Product Manager** | Clear priorities, acceptance criteria, phasing that fits roadmap |
| **Engineering Lead** | Stable requirements, explicit “TBD until spike” items, NFRs that match reality |
| **Data Analyst** | Feasible definitions, pipeline ownership, limited MVP scope |
| **Customer Support Manager** | Agent-visible disposition, scripts aligned to policy, training lead time |
| **Compliance / Legal Representative** | Review of enforcement language, retention, and fair treatment |
| **Operations Manager** | Runbook for monitoring, escalation, and who is on call |

---

## Business requirements

| ID | Requirement statement |
|----|-------------------------|
| BRQ-01 | Northline Market shall **detect** first-time coupon reuse patterns against the agreed definition of “customer” (see business rules). |
| BRQ-02 | Northline Market shall **detect** duplicate or linked accounts used to harvest promos, using agreed signals (payment, device, address, account age) where legally and technically allowed. |
| BRQ-03 | Northline Market shall **validate** coupon stacking against published stacking policy and record violations or warnings. |
| BRQ-04 | Northline Market shall **flag** referral abuse scenarios defined with Legal and Growth (self-referral, closed loops, early payout abuse). |
| BRQ-05 | Northline Market shall **evaluate** orders or lines where discount depth breaches low-margin or excluded category rules. |
| BRQ-06 | Northline Market shall produce **campaign-level** views of suspected leakage and redemption spikes for Finance and Growth. |
| BRQ-07 | Northline Market shall maintain a **manual review queue** with assignment, SLA tracking, and documented outcomes. |
| BRQ-08 | Northline Market shall retain an **audit trail** for configuration changes, case decisions, and kill-switch actions. |
| BRQ-09 | Northline Market shall support **role-based access** to sensitive investigation views versus aggregate reporting. |
| BRQ-10 | Northline Market shall define **policy exceptions** (manual overrides) with approver, reason, and time bound visibility. |
| BRQ-11 | Northline Market shall provide **alerts** when redemption or flag volume crosses thresholds so ops is not surprised after the fact. |
| BRQ-12 | Northline Market shall document **reporting definitions** (numerator, denominator, exclusions) that Finance signs off for steering. |

---

## Functional requirement summary

Functional behavior is specified in `functional-requirements.md` using IDs **FR-001** through **FR-018** (and optional extensions). Topics include first-time reuse detection, duplicate account signals, stacking validation, referral abuse flagging, low-margin checks, campaign leakage reporting, risk scoring, queue and SLA, decisions, audit, dashboard filters, exports, access, exceptions, kill-switch, and redemption spike alerts.

---

## Non-functional requirement summary

Non-functional expectations (performance, security, privacy, availability, auditability, usability, scalability, retention, maintainability, reporting accuracy, access control, compliance review) are in `non-functional-requirements.md` using IDs **NFR-001** through **NFR-012**.

---

## Business rules summary

Eligibility, stacking, thresholds, referral rules, duplicate signals, approvals, refunds, reversals, pause conditions, logging, and overrides are captured in `business-rules.md` using **BR-001** onward. Rules need Legal and Growth validation before any customer-facing enforcement.

---

## Assumptions

- Northline Market can supply **order-level** promo and referral history for a defined lookback window.
- A pilot can target a **subset** of campaigns or categories before enterprise-wide enforcement.
- Fraud or Risk and Customer Support staffing can absorb a **bounded** pilot queue if thresholds are tuned.
- Executive Sponsor will break **deadlocks** on metric definitions or pilot scope within an agreed time box.

---

## Constraints

- Legal review for customer messaging, clawbacks, and retention of investigation data.
- Engineering change windows and peak-season freezes may limit when rule or checkout logic changes ship.
- BI capacity caps the size of the first dashboard release.
- Multi-system promo configuration persists until a separate consolidation effort; this BRD names authoritative sources per rule type where known.

---

## Dependencies

- Accurate **promo application** and **line-level** facts in the data warehouse or lake.
- **Identity** or device signals available under Northline Market policy for duplicate detection (may be partial at v1).
- **Referral** service events and payout records available to Data with acceptable latency.
- **CRM or CS** integration if case disposition must appear to agents (optional in v1, see functional requirements).
- **Legal** calendar for template review before UAT exit on customer-visible flows.

---

## Risks

| Risk | Impact |
|------|--------|
| Metric definitions contested between Finance and Growth | Delays sign-off; rework of dashboards |
| Data quality worse than expected | Under-reporting or wrong prioritization |
| Over-alerting | Queue ignored; loss of trust in PromoLeak |
| Tight rules without conversion monitoring | Revenue or CS hit; political rollback |
| Scope creep into full payment fraud | Timeline slip; unclear ownership |

---

## Success metrics

| Metric | Target direction (pilot or first GA) |
|--------|--------------------------------------|
| Time to detect a **runaway** campaign (hours or days, not only month-end) | Down vs. baseline |
| **Volume** of suspected leakage orders reviewed per week vs. opened cases closed with disposition | Up on throughput, stable on quality |
| **False positive rate** on a defined sample | Within band agreed by Fraud and Finance |
| **Repeat** stacking or first-time abuse incidents for the same failure mode | Down after rule fix |
| **Finance confidence** (survey or steering vote) in headline leakage metric | Up |
| **CS** repeat contacts on the same promo dispute where disposition exists | Down (where measured) |

Exact baselines and targets are TBD with Data and Finance after instrumentation exists.

---

## Approval section

| Name | Role | Signature | Date |
|------|------|-----------|------|
| | Executive Sponsor | | |
| | Finance Manager | | |
| | Marketing / Growth Manager | | |
| | Product Manager | | |
| | BA lead | | |

Formal approval waits on workshop outcomes and Legal review of sensitive rules. This portfolio copy is for structure and interview practice.
