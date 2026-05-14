# Functional Requirements: PromoLeak Radar

> **Note:** These functional requirements describe intended behavior for **Northline Market** (fictional). They assume discovery findings that still need **stakeholder validation**, sizing by Engineering, and Legal sign-off on customer-facing or enforcement flows before any production commitment.

**Project:** PromoLeak Radar  
**Traceability:** Use IDs **FR-001** onward when mapping to user stories, RTM, and test cases.

---

## Functional requirements

| Requirement ID | Requirement | Description | Business reason | Priority | Source stakeholder | Acceptance notes |
|----------------|-------------|-------------|-----------------|----------|---------------------|------------------|
| FR-001 | First-time coupon reuse detection | System evaluates orders using first-time or new-customer codes against the agreed **one per customer** definition (see business rules) and flags suspected reuse across accounts or identities. | First-time abuse is a known leakage path at Northline Market. | Must | Fraud / Risk Analyst, Marketing / Growth Manager | Flag includes reason code; false positives can be marked; definition document linked in release notes. |
| FR-002 | Duplicate account detection | System flags new or existing accounts that match **duplicate signals** (shared payment, device, address, or velocity rules per policy). | Duplicate accounts harvest promos and referrals. | Must | Fraud / Risk Analyst, Engineering Lead | Signals used are documented; Legal approves any sensitive attributes; sample output reviewed with Fraud. |
| FR-003 | Coupon stacking validation | At order capture (or agreed lifecycle point), system validates applied discounts against **stacking policy** and records allow, warn, or block per Northline Market rules. | Stacking beyond intent drives margin loss. | Must | Marketing / Growth Manager, Engineering Lead | Golden-path and edge-case orders from Growth used in UAT; policy version id stored on order. |
| FR-004 | Referral abuse flagging | System flags referral events or payouts matching patterns in business rules (self-referral, closed loop, velocity, early churn). | Referral misuse drains acquisition budget. | Must | Fraud / Risk Analyst, Marketing / Growth Manager | Patterns configurable within bounds; Legal reviews customer-facing text tied to actions. |
| FR-005 | Low-margin product discount checks | System compares line-level discount depth to **margin or category exclusion** lists and flags breaches. | High discounts on low-margin SKUs were called out in discovery. | Must | Finance Manager, Product Manager | COGS or margin source documented; unknown margin paths handled explicitly (exclude or flag). |
| FR-006 | Campaign-level leakage reporting | Dashboards and reports aggregate flagged discount dollars, order counts, and trends **by campaign and code**. | Finance and Growth need the same campaign view. | Must | Finance Manager, Marketing / Growth Manager | Drill from campaign to order list for authorized roles; definitions match Finance sign-off. |
| FR-007 | Risk scoring logic | System assigns a **risk score** or tier to orders or accounts from weighted signals (stacking, margin breach, referral pattern, duplicate signals). | Prioritizes review queue and alerts. | Should | Fraud / Risk Analyst, Data Analyst | Weights and version id visible to investigators; score explainable from reason codes. |
| FR-008 | Manual review queue | All flagged items appear in a queue with status **New**, filters, and search by order id, account, campaign. | Ops and Fraud need one place to work. | Must | Fraud / Risk Analyst, Operations Manager | No silent drops when pipeline fails; banner if data stale. |
| FR-009 | Case assignment | Investigators or leads can **assign** a case to a user or pool and reassign on PTO. | Workload and accountability. | Must | Operations Manager, Fraud / Risk Analyst | Assignment and reassignment audited; unassigned SLA visible. |
| FR-010 | SLA tracking | Queue shows **age**, due time, and breach indicator per agreed SLA classes (severity or campaign tier). | Prevents cases aging out unnoticed. | Should | Operations Manager, Customer Support Manager | SLA parameters configurable with owner; reporting on breach rate. |
| FR-011 | Review decision capture | User records outcome: confirmed abuse, false positive, needs Growth, needs Legal, closed with notes; **mandatory** fields enforced by status. | Audit and CS visibility depend on structured outcomes. | Must | Fraud / Risk Analyst, Compliance / Legal Representative | Cannot close high-risk outcomes without required fields; export includes decision history. |
| FR-012 | Audit trail | System logs configuration changes to thresholds, rules, kill-switch actions, and case status changes with **user, timestamp, before/after** where applicable. | Finance and Legal need defensibility. | Must | Compliance / Legal Representative, Finance Manager | Immutable log for configured event types; retention per policy. |
| FR-013 | Dashboard filters | Users with access can filter by **date, campaign, code, category, channel, flag type**, within data limits. | Different teams slice leakage differently. | Must | Finance Manager, Data Analyst | Filter set matches BRD MVP; performance per NFR-001. |
| FR-014 | Exportable reports | Authorized users export **aggregates or limited order lists** to approved formats with column sets controlled by role. | Board packs and deep dives without ad hoc SQL for standard cuts. | Must | Finance Manager, Fraud / Risk Analyst | Legal approves columns with PII; export logged. |
| FR-015 | Role-based access | Views and exports enforce **roles** (aggregate only, investigator, admin, Growth read-only, etc.) per Northline Market security model. | Privacy and least privilege. | Must | Compliance / Legal Representative, Engineering Lead | Negative UAT tests for each role; deny paths logged. |
| FR-016 | Policy exception handling | Recorded exception path: requester, approver, **time window**, scope (account or order), and auto-expiry where possible. | Goodwill and VIP cases without silent shadow policy. | Should | Marketing / Growth Manager, Compliance / Legal Representative | Exceptions visible in audit; reports can include or exclude per Finance rule. |
| FR-017 | Kill-switch for high-risk campaigns | Authorized role can **disable or cap** a campaign or code with effective time and audit entry; new checkouts obey within agreed latency. | Stop bleeding when a code runs hot. | Must | Marketing / Growth Manager, Engineering Lead | UAT includes rollback test; latency target in NFR. |
| FR-018 | Alerts for unusual redemption spikes | System sends alert when redemptions or flags cross **threshold** for a campaign or globally within a window (email or agreed channel). | Ops learns before month-end. | Should | Operations Manager, Finance Manager | Thresholds configurable; on-call rotation documented; alert includes deep link to dashboard. |

---

## Parking lot (not in FR-001 to FR-018)

- Click-time vs. batch-only scoring (architecture decision).
- Marketplace partner orders if data not in v1 warehouse.
- Automated clawback execution (may stay manual until Legal and Risk agree).
