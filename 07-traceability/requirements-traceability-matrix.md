# Requirements Traceability Matrix (RTM)

**Project:** PromoLeak Radar (Northline Market)  
**Sources:** `04-business-requirements/` (FR, NFR, BR), `06-user-stories/` (BL, US)

---

## 1. Purpose

This RTM ties Northline Market's written requirements to backlog items, user stories, and planned UAT test IDs. It is meant for validation workshops and UAT prep, not as a promise that every path is built. When a cell shows multiple IDs, read left to right as primary then supporting links.

---

## 2. How to read the matrix

- **Requirement ID:** Only IDs that already exist in the BRD files (FR-001 to FR-018, NFR-001 to NFR-012, BR-001 to BR-018). No new requirement IDs are introduced here.
- **Requirement type:** FR (functional), NFR (non-functional), or BR (business rule).
- **Related Business Rule / Backlog / User Story / Test Case:** Trace forward into delivery and test. **Test Case IDs (TC-xxx)** are planned UAT pack placeholders; scripts will be written in the UAT section later.
- **Priority:** Pulled from the functional or non-functional requirement tables where applicable; BR rows use the owning rule's intent (Must for policy that blocks leakage, Should where workshop still owes numbers).
- **Owner:** Named role accountable for sign-off or validation of that row, aligned to the stakeholder mix in the BRD tables.
- **Status:** Where discovery left the item. "Ready for UAT" does not mean production ready; it means the requirement set is stable enough to script against pending open items.

Functional and non-functional rows are the **authoritative test spine** for UAT. Business rule rows show **policy to requirement** mapping so Legal and Finance can see which FR or NFR enforces each rule.

---

## 3. Traceability matrix tables

### 3.1 Functional requirements (FR-001 to FR-018)

| Requirement ID | Requirement Type | Requirement Summary | Business Objective | Related Business Rule | Related Backlog Item | Related User Story | Related Test Case ID | Priority | Owner | Status |
|----------------|------------------|----------------------|--------------------|------------------------|----------------------|--------------------|------------------------|----------|-------|--------|
| FR-001 | FR | First-time coupon reuse detection | Cut welcome-offer leakage across accounts or weak identity matches | BR-001, BR-002 | BL-002 | US-001 | TC-002 | Must | Fraud / Risk Analyst | Reviewed |
| FR-002 | FR | Duplicate account detection | Surface payment, device, and address farm patterns for review | BR-007, BR-008, BR-009 | BL-003, BL-005 | US-002 | TC-003, TC-004 | Must | Fraud / Risk Analyst | Needs stakeholder validation |
| FR-003 | FR | Coupon stacking validation | Enforce published stack policy at the agreed lifecycle point | BR-005 | BL-001 | US-003 | TC-001 | Must | Marketing / Growth Manager | Ready for UAT |
| FR-004 | FR | Referral abuse flagging | Protect referral budget from self-deals, loops, and bad payouts | BR-003, BR-004, BR-012 | BL-006, BL-007 | US-004 | TC-006 | Must | Marketing / Growth Manager | Needs stakeholder validation |
| FR-005 | FR | Low-margin product discount checks | Flag discount depth that breaches margin floor on excluded categories | BR-006 | BL-004 | US-005 | TC-005 | Must | Finance Manager | Reviewed |
| FR-006 | FR | Campaign-level leakage reporting | One campaign and code view Finance and Growth can argue from without two exports | BR-018 | BL-014, BL-016 | US-012, US-013, US-014 | TC-007 | Must | Finance Manager | Needs stakeholder validation |
| FR-007 | FR | Risk scoring logic | Rank orders or accounts into tiers so review work sorts by risk | BR-011 | BL-008 | US-006 | TC-008 | Should | Fraud / Risk Analyst | Draft |
| FR-008 | FR | Manual review queue | Single queue for promo flags with clear New state and search | BR-011 | BL-009 | US-007 | TC-009 | Must | Fraud / Risk Analyst | Ready for UAT |
| FR-009 | FR | Case assignment | Assign and reassign cases to people or pools with accountability | BR-011 | BL-010 | US-008 | TC-010 | Must | Operations Manager | Reviewed |
| FR-010 | FR | SLA tracking | Age, due time, and breach visibility for queue items | BR-011 | BL-011 | US-009 | TC-011 | Should | Operations Manager | Draft |
| FR-011 | FR | Review decision capture | Structured outcomes and mandatory fields for high-risk closes | BR-013 | BL-012 | US-010 | TC-012 | Must | Compliance / Legal Representative | Reviewed |
| FR-012 | FR | Audit trail | Defensible history for config, kill-switch, case, and export events | BR-016 | BL-013 | US-011 | TC-013 | Must | Engineering Lead | Ready for UAT |
| FR-013 | FR | Dashboard filters | Self-serve slices by date, campaign, code, category, channel, flag type | BR-018 | BL-015 | US-015 | TC-014 | Must | Data Analyst | Reviewed |
| FR-014 | FR | Exportable reports | Role-controlled exports for board and investigation packs | BR-018 | BL-017 | US-016 | TC-015 | Must | Finance Manager | Needs stakeholder validation |
| FR-015 | FR | Role-based access | Least privilege for views, investigation panes, and admin paths | BR-017 | BL-018 | US-017 | TC-016 | Must | Engineering Lead | Reviewed |
| FR-016 | FR | Policy exception handling | Recorded exception path with approver separation and time window | BR-017 | BL-020 | US-018 | TC-017 | Should | Customer Support Manager | Draft |
| FR-017 | FR | Kill-switch for high-risk campaigns | Pause or cap a code with audit and checkout obeying within latency | BR-014 | BL-021 | US-019 | TC-018 | Must | Marketing / Growth Manager | Reviewed |
| FR-018 | FR | Alerts for unusual redemption spikes | Notify Ops or Finance when thresholds breach so response is early | BR-014 | BL-021 | US-020 | TC-019 | Should | Operations Manager | Draft |

### 3.2 Non-functional requirements (NFR-001 to NFR-012)

| Requirement ID | Requirement Type | Requirement Summary | Business Objective | Related Business Rule | Related Backlog Item | Related User Story | Related Test Case ID | Priority | Owner | Status |
|----------------|------------------|----------------------|--------------------|------------------------|----------------------|--------------------|------------------------|----------|-------|--------|
| NFR-001 | NFR | Performance for dashboards and batch windows | Adoption and incident response stay usable under load | BR-018 | BL-015 | US-015 | TC-020 | Must | Engineering Lead | Needs stakeholder validation |
| NFR-002 | NFR | SSO and session policy for admin paths | Central identity and MFA, no stray prod passwords | BR-016 | BL-018 | US-017 | TC-021 | Must | Engineering Lead | Reviewed |
| NFR-003 | NFR | Privacy masking and export gating | Investigators see enough context without oversharing PII | BR-015 | BL-017, BL-019 | US-016, US-017 | TC-022 | Must | Compliance / Legal Representative | Needs stakeholder validation |
| NFR-004 | NFR | Availability target for monitoring UI | Teams do not revert to spreadsheets every outage | None in BR-001 to BR-018 | None in BL-001 to BL-022 | US-021 | TC-023 | Should | Engineering Lead | Draft |
| NFR-005 | NFR | Append-only audit configuration | Disputes can rely on tamper-evident event history | BR-016 | BL-013 | US-011 | TC-024 | Must | Compliance / Legal Representative | Reviewed |
| NFR-006 | NFR | Usability for trained Finance and Fraud users | Primary tasks completable from the guided UAT script | BR-018 | BL-022 | US-021 | TC-025 | Must | Product Manager | Draft |
| NFR-007 | NFR | Scalability headroom | Peak promos and queue spikes do not force a schema redesign | None in BR-001 to BR-018 | None in BL-001 to BL-022 | US-021 | TC-026 | Should | Engineering Lead | Draft |
| NFR-008 | NFR | Data retention and legal hold | Retention mistakes do not create privacy or Legal exposure | BR-016 | BL-013 | US-011 | TC-027 | Must | Compliance / Legal Representative | Needs stakeholder validation |
| NFR-009 | NFR | Maintainability of thresholds | Fraud and Finance can tune within config paths where design allows | BR-016 | BL-008 | US-006 | TC-028 | Should | Fraud / Risk Analyst | Draft |
| NFR-010 | NFR | Reporting accuracy and Finance tie-out | Headline leakage reconciles to Finance sample or variance is documented | BR-018 | BL-014, BL-022 | US-012, US-022 | TC-029 | Must | Finance Manager | Needs stakeholder validation |
| NFR-011 | NFR | Access control least privilege | Aggregate roles cannot open full investigation panes; denies logged | BR-017 | BL-018 | US-017 | TC-030 | Must | Engineering Lead | Reviewed |
| NFR-012 | NFR | Legal approval on customer-facing enforcement copy | Enforceability and brand risk stay controlled | BR-013 | BL-022 | US-021 | TC-031 | Must | Compliance / Legal Representative | Needs stakeholder validation |

### 3.3 Business rules (BR-001 to BR-018)

| Requirement ID | Requirement Type | Requirement Summary | Business Objective | Related Business Rule | Related Backlog Item | Related User Story | Related Test Case ID | Priority | Owner | Status |
|----------------|------------------|----------------------|--------------------|------------------------|----------------------|--------------------|------------------------|----------|-------|--------|
| BR-001 | BR | One first-time redemption per eligible customer | Stop double welcome discounts | (self) | BL-002 | US-001 | TC-002 | Must | Marketing / Growth Manager | Needs stakeholder validation |
| BR-002 | BR | Blocked linkage blocks first-time reuse | Close the "new account, same person" path | BR-001 | BL-002 | US-001 | TC-002 | Must | Fraud / Risk Analyst | Needs stakeholder validation |
| BR-003 | BR | Referral pays only after milestone and checks | Pay acquisition rewards on real orders, not ghosts | BR-004 | BL-006 | US-004 | TC-006 | Must | Marketing / Growth Manager | Needs stakeholder validation |
| BR-004 | BR | Self-referral and closed loops ineligible | Kill obvious referral loops | BR-003 | BL-006 | US-004 | TC-006 | Must | Compliance / Legal Representative | Needs stakeholder validation |
| BR-005 | BR | Stacking cap and application order | Margin control when multiple promos combine | (self) | BL-001 | US-003 | TC-001 | Must | Marketing / Growth Manager | Reviewed |
| BR-006 | BR | Margin floor flag on excluded categories | Stop deep cuts on SKUs Finance never meant to promote hard | (self) | BL-004 | US-005 | TC-005 | Must | Finance Manager | Needs stakeholder validation |
| BR-007 | BR | Shared payment token duplicate signal | Fast farm detection Finance already trusts in gut checks | BR-001, BR-002 | BL-003 | US-002 | TC-003 | Must | Fraud / Risk Analyst | Needs stakeholder validation |
| BR-008 | BR | Device velocity duplicate signal | Catch volume without pretending graph is perfect | BR-007 | BL-005 | US-002 | TC-004 | Should | Fraud / Risk Analyst | Draft |
| BR-009 | BR | Address hash duplicate signal | Catch shared ship-to abuse with conservative tuning | BR-007, BR-008 | BL-005 | US-002 | TC-004 | Should | Fraud / Risk Analyst | Draft |
| BR-010 | BR | Second approver on high-risk campaign attributes | Stop single-click publish mistakes on deep or sitewide promos | BR-014 | None in BL-001 to BL-022 | None in US-001 to US-022 | TC-032 | Must | Marketing / Growth Manager | Draft |
| BR-011 | BR | Manual review trigger for high risk or breaches | No silent drop when rules fire | BR-005, BR-006, BR-016 | BL-009 | US-007 | TC-009 | Must | Fraud / Risk Analyst | Reviewed |
| BR-012 | BR | Refund window nets referral payout | Do not fund acquisition on revenue that walked back | BR-003 | BL-007 | US-004 | TC-006 | Must | Finance Manager | Needs stakeholder validation |
| BR-013 | BR | Reward reversal uses Legal-approved script | Customer comms stay enforceable | BR-003, BR-012 | BL-012 | US-010 | TC-012, TC-031 | Must | Compliance / Legal Representative | Needs stakeholder validation |
| BR-014 | BR | Campaign pause or cap within hours on spike | Limit weekend bleed when a code runs hot | BR-010 | BL-021 | US-019, US-020 | TC-018, TC-019 | Must | Marketing / Growth Manager | Needs stakeholder validation |
| BR-015 | BR | Legal sign-off before sensitive new signals | Fair lending and marketing law guardrails | BR-007, BR-008, BR-009 | BL-019 | US-017 | TC-022 | Must | Compliance / Legal Representative | Needs stakeholder validation |
| BR-016 | BR | Append-only audit on threshold and kill-switch changes | Answer "who moved the goalposts" | BR-011 | BL-013 | US-011 | TC-013, TC-024 | Must | Engineering Lead | Reviewed |
| BR-017 | BR | Policy exception requester plus approver | No same-person shadow credits | BR-018 | BL-020 | US-018 | TC-017 | Should | Customer Support Manager | Draft |
| BR-018 | BR | Versioned leakage definition for dashboards | When the number moves, the footnote explains why | BR-005, BR-006 | BL-014, BL-016 | US-012, US-022 | TC-007, TC-029 | Must | Finance Manager | Needs stakeholder validation |

---

## 4. Coverage notes

- **Must Have FRs:** Each FR-001 to FR-006, FR-008, FR-009, FR-011 to FR-015, and FR-017 has at least one **user story** and at least one **planned test case** in the tables above. FR-007, FR-010, FR-016, and FR-018 are Should priorities in the BRD; they still have story and test hooks for pilot planning.
- **NFR spine:** Security and privacy NFRs trace to **US-017** and **US-016** with negative tests (TC-021, TC-022, TC-030). Reporting NFRs trace to **US-012**, **US-015**, and **US-022** (TC-029).
- **Business rules:** BR-001 to BR-018 appear in section 3.3. Most trace to an FR or NFR enforcement row; **BR-010** is called out honestly as leaning on **campaign publish tooling** that is not yet expressed as its own backlog item in `06-user-stories/` (see gaps).
- **Test cases:** TC-001 to TC-032 are the **planned UAT catalog** for the next documentation pass. Several FR rows share a TC where one script covers multiple checks (for example FR-017 and FR-018 both exercise **BL-021** with TC-018 and TC-019 split by kill-switch vs. alert).

---

## 5. Open traceability gaps

| Gap | Why it matters | Suggested next step |
|-----|----------------|---------------------|
| **BR-010 second approver on publish** | Governance rule exists; no dedicated BL or US in `06-user-stories/` yet | Add a backlog item and story for campaign approval workflow, or mark BR-010 out of MVP scope in the BRD |
| **FR-002 device and address vs. US-002** | **US-002** is written around shared payment; **BL-005** carries device and address expansion | Either split a second user story for device or address, or extend US-002 acceptance criteria so UAT explicitly covers BL-005 |
| **Marketplace and partner orders** | BRD parking lot; affects BR-018 denominator | Footnote exclusion in BR-018 and RTM once sponsors decide |
| **TBD thresholds** | BR and NFR tables still carry TBD for windows, floors, and tolerances | Workshop sign-off sheet; until then rows stay **Needs stakeholder validation** or **Draft** |
| **NFR-004 and NFR-007** | Light trace to product backlog; mostly hosting and capacity evidence | Link to runbook and capacity memo IDs when Engineering publishes them |
| **BR-010 has TC-032 only** | Second approver on publish is not in the current user story set | Either add BL or US, or exclude BR-010 from MVP UAT scope with sponsor sign-off |

---

## 6. UAT readiness notes

- **Ready to script first:** FR-003, FR-008, FR-009, FR-011, FR-012, FR-015, and NFR-011 (clear pass or fail paths, strong audit story). Pair with **US-003, US-007, US-008, US-010, US-011, US-017** and TC-001, TC-009, TC-010, TC-012, TC-013, TC-016, TC-030.
- **Blocked on numbers or Legal:** FR-001, FR-002, FR-004, FR-005, FR-014, NFR-010, NFR-012 (TBD windows, tie-out tolerance, template approvals). Run **US-021** as the gate for "script exists" and **US-022** for definition versioning before exec readout.
- **Exit criteria reminder:** **BL-022** ties the guided UAT pack to the FR list and NFR smoke; keep **BR-018** and **NFR-010** on the same exit checklist so headline dollars do not ship without a tie-out story.

---

## Change log

| Date | Author | Change |
|------|--------|--------|
| 2026-05-14 | BA case study | Replaced skeleton with full FR, NFR, and BR traceability, planned TC-001 to TC-032, coverage and gap notes |
