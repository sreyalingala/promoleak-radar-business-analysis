# UAT Test Cases: PromoLeak Radar (Northline Market)

**Project:** PromoLeak Radar  
**Traceability:** IDs **TC-001 through TC-032** match `07-traceability/requirements-traceability-matrix.md`.  
**Requirement IDs:** Only **FR-001 to FR-018**, **NFR-001 to NFR-012**, **BR-001 to BR-018**, and **US-001 to US-022** from existing BRD and user story files.

**Important:** These scripts are drafted for this portfolio and for a rehearsal-style UAT. A real Northline program would need fixture ids, final thresholds, Legal-approved copy, and SME sign-off on steps before anyone treats this pack as binding.

---

## Test case catalog

| Test Case ID | Requirement ID | Related User Story | Scenario | Preconditions | Test Steps | Expected Result | Priority | Owner | Status |
|--------------|----------------|--------------------|----------|---------------|------------|-----------------|----------|-------|--------|
| TC-001 | FR-003, BR-005 | US-003 | Coupon stacking prevention, published order | Stack policy and golden-path carts exist in UAT; test user can checkout | 1) Open stack policy doc for version id. 2) Build cart with two promos that violate published stack. 3) Complete or attempt checkout per pilot rule (block or warn). 4) Open order in OMS or PromoLeak detail. | Checkout outcome matches policy (block or warn). Order stores policy version id. Reason code visible in investigator view if warn path. | High | Marketing / Growth Manager | Draft |
| TC-002 | FR-001, BR-001, BR-002 | US-001 | First-time coupon restriction, suspected reuse | Two accounts meet synthetic blocked linkage; first-time code active | 1) Place first order with first-time code on account A. 2) Place second order with same code pattern on account B that hits linkage rule. 3) Open PromoLeak flag detail. | Second order flagged with reuse-related reason code. False positive disposition available if business marks test noise. | High | Fraud / Risk Analyst | Draft |
| TC-003 | FR-002, BR-007 | US-002 | Duplicate account detection, shared payment | Two accounts share payment surrogate within policy window | 1) Confirm payment hash present for both accounts. 2) Apply first-time or high-value promo on second account. 3) View flags. | Flag raised with shared payment signal type. If signal missing, UI states unavailable per US-002, not a false green state. | High | Fraud / Risk Analyst | Draft |
| TC-004 | FR-002, BR-008, BR-009 | US-002 | Shared device and shared shipping address signals | Device velocity and address hash fixtures loaded | 1) Trigger device velocity pattern per BR-008. 2) Trigger address hash pattern per BR-009. 3) Review flags and reason list. | Distinct reason codes or labels for device vs address where design supports it. Conservative behavior documented if combined into one signal family. | Medium | Fraud / Risk Analyst | Draft |
| TC-005 | FR-005, BR-006 | US-005 | Low-margin SKU discount checks | Exclusion list SKU with trusted COGS and one line with missing COGS | 1) Place order breaching margin floor on trusted line. 2) Place order on missing COGS line with deep discount. 3) Open leakage or line detail. | Trusted line flags margin floor. Missing COGS line tagged margin unknown and excluded from headline leakage unless Finance test pack says include. | High | Finance Manager | Draft |
| TC-006 | FR-004, BR-003, BR-004, BR-012 | US-004 | Referral abuse flagging and refund netting | Referral test personas and refund event available | 1) Run self-referral or closed loop scenario. 2) Run milestone-not-met scenario. 3) Post payout, trigger full refund inside BR-012 window. 4) Check referral hold or netting entries Finance cares about. | Self or closed loop held or flagged per policy. Refund creates reversal or netting signal with audit correlation where designed. | High | Finance Manager | Draft |
| TC-007 | FR-006, BR-018 | US-012, US-013, US-014 | Campaign dashboard and exec strip KPIs | Finance signed definition version vTest; sample campaigns loaded | 1) Open campaign leakage view. 2) Note headline totals and footnote version. 3) Open ROI slice if in build (US-013). 4) Open exec strip if in build (US-014). | Footnote shows agreed definition version. Tiles match sample within agreed tolerance or show pending sign-off state per US-014. | High | Finance Manager | Draft |
| TC-008 | FR-007, BR-011 | US-006 | Promotion risk score explainability | Scoring enabled; weights version id visible | 1) Open flagged order with multiple signals. 2) Expand score or tier detail. 3) Note score version id. | Tier or score shown with breakdown of which signals fired. No unexplained blank tier on scored orders. | Medium | Fraud / Risk Analyst | Draft |
| TC-009 | FR-008, BR-011 | US-007 | Manual review queue routing | Pipeline healthy; at least one new flag | 1) Open queue. 2) Confirm new item appears with links to order and campaign. 3) Simulate pipeline lag if safe; observe banner behavior. | New items visible when pipeline succeeds. Stale or failure state shows banner, not empty healthy queue. | High | Fraud / Risk Analyst | Draft |
| TC-010 | FR-009, BR-011 | US-008 | Case assignment and reassignment | Investigator and pool exist; case in New | 1) Assign case to investigator A. 2) Save. 3) Reassign to investigator B for PTO scenario. 4) Open history or audit slice for assignment. | Assignment and reassignment recorded with user and time per acceptance story. | High | Operations Manager | Draft |
| TC-011 | FR-010, BR-011 | US-009 | SLA tracking and breach indicator | SLA classes configured; case near breach | 1) Open queue sorted by due time. 2) Age case past due in test clock or fixture. 3) Observe breach styling and breach report if present. | Breach visible on row and on breach summary if in scope. New SLA defaults apply only to new cases unless sponsor approved retro. | Medium | Operations Manager | Draft |
| TC-012 | FR-011, BR-013 | US-010 | Review decision capture, mandatory fields | Case in review; investigator role | 1) Attempt close high-risk outcome with blank required field. 2) Fill required fields and close as false positive with reason. 3) Save. | Save blocked until required fields complete. Disposition stored with reason for tuning. | High | Compliance / Legal Representative | Draft |
| TC-013 | FR-012, BR-016 | US-011 | Audit trail for case and config change | Admin or investigator can change a threshold or disposition in test | 1) Make a controlled config or status change. 2) Open audit view for object. 3) Export audit slice if allowed. | Row shows actor, time, old and new values where applicable. Export attempt itself logged if in FR-012 scope. | High | Engineering Lead | Draft |
| TC-014 | FR-013, BR-018 | US-015 | Dashboard filters | User has dashboard access; mixed campaigns in data | 1) Apply date, campaign, code, category, channel, flag type filters one at a time then combined. 2) Clear filters. | Results narrow as expected. Out-of-retention dates show validation message. Refresh timestamp visible. | High | Data Analyst | Draft |
| TC-015 | FR-014, BR-018, NFR-003 | US-016 | Exportable reports, column control | Investigator role with Legal-approved column set | 1) Request export of limited order list. 2) Open file. 3) Confirm columns match matrix. | Only approved columns export. Export logged. No extra PII columns. | High | Finance Manager | Draft |
| TC-016 | FR-015, BR-017 | US-017 | Role-based access, happy path per role | Test accounts for aggregate, investigator, Growth read-only, admin | 1) Log in as each role. 2) Navigate to pages each role should reach. 3) Record pass or blocked as expected. | Each role sees only permitted areas. Growth read-only cannot change disposition if that is policy. | High | Engineering Lead | Draft |
| TC-017 | FR-016, BR-017 | US-018 | Policy exception approval separation | CS requester and different approver accounts | 1) Create exception request as agent. 2) Attempt approve as same person. 3) Complete with valid approver. 4) Check active window and expiry if designed. | Same-person approval blocked. Valid path records requester, approver, window, scope. | Medium | Customer Support Manager | Draft |
| TC-018 | FR-017, BR-014 | US-019 | Campaign kill-switch and rollback | Authorized Growth test user; live test code in UAT | 1) Note audit state. 2) Apply cap or disable code. 3) Place new checkout with that code. 4) Roll back change. 5) Recheck checkout. | New carts obey cap or disable within agreed latency. Audit rows for change and rollback. | High | Marketing / Growth Manager | Draft |
| TC-019 | FR-018, BR-014 | US-020 | Redemption spike alert | Alert thresholds set to low values for test; channel wired | 1) Generate redemption or flag volume above threshold. 2) Wait for monitor cycle. 3) Open alert payload. | Alert received on agreed channel with campaign id and deep link. Dedup behavior matches spec if two breaches fire close together. | Medium | Operations Manager | Draft |
| TC-020 | NFR-001, BR-018 | US-015 | Dashboard response within agreed window | Reference dataset loaded; timer available | 1) Apply default filter set on primary dashboard. 2) Measure until results render (stopwatch or tooling). 3) Record batch completion time if shown. | Within TBD target documented for UAT or variance logged with Engineering owner. | High | Engineering Lead | Draft |
| TC-021 | NFR-002, BR-016 | US-017 | SSO login and session timeout | Corporate IdP test user | 1) Log in via SSO. 2) Idle past session policy or use forced timeout tool if available. 3) Attempt protected action. | Re-auth required per policy. No unexpected standalone prod password prompt for admin path. | High | Engineering Lead | Draft |
| TC-022 | NFR-003, BR-015 | US-016, US-017 | Privacy masking and investigation panes | Legal masking table examples available | 1) Open investigator view as investigator. 2) Compare to Legal table. 3) Open same order reference as aggregate-only if such role exists. | Masking matches examples. Aggregate role lacks full pane or sees redacted fields only. | High | Compliance / Legal Representative | Draft |
| TC-023 | NFR-004 | US-021 | Monitoring UI graceful handling when data partial | Engineering simulates partial load failure in non-prod | 1) Open dashboard during simulated partial failure. 2) Read messaging. 3) Attempt export if enabled. | User sees graceful message, not misleading all-green state. | Medium | Engineering Lead | Draft |
| TC-024 | NFR-005, BR-016 | US-011 | Append-only audit configuration evidence | Config doc from Engineering | 1) Review sample audit export with Compliance. 2) Confirm append-only claim for configured event types matches runbook. | Compliance accepts evidence for UAT record or logs gap as defect. | High | Compliance / Legal Representative | Draft |
| TC-025 | NFR-006, BR-018 | US-021 | Guided UAT usability, Finance and Fraud tasks | Printed script from BL-022 style checklist | 1) Shadow Finance tester through primary tasks without SQL. 2) Shadow Fraud tester through queue tasks without SQL. 3) Record pass or fail with notes. | Trained users complete script tasks or failures logged with UX defect id. | High | Product Manager | Draft |
| TC-026 | NFR-007 | US-021 | Scalability evidence for pilot | Capacity statement from Engineering | 1) Read capacity one-pager. 2) Confirm headroom vs expected pilot peak. 3) Log risk if optional load test not run. | Written statement on file or optional test result attached to UAT pack. | Low | Engineering Lead | Draft |
| TC-027 | NFR-008, BR-016 | US-011 | Retention and legal hold awareness | Legal retention schedule excerpt | 1) Walk cases and exports against retention table. 2) Confirm purge job owner named. 3) Note legal hold exception path. | Owners named; gaps logged if purge not implemented in UAT env. | High | Compliance / Legal Representative | Draft |
| TC-028 | NFR-009, BR-016 | US-006 | Threshold change without code deploy | Config path available in pilot | 1) Change a threshold in admin path. 2) Save. 3) Verify audit row. 4) Run one flagging job or wait for next cycle. | Change applies per design; audit captures old and new values. | Medium | Fraud / Risk Analyst | Draft |
| TC-029 | NFR-010, BR-018 | US-012, US-022 | Reporting definition alignment and Finance tie-out | Finance tie-out sample with expected flag and dollar posture | 1) Record dashboard definition version. 2) Run Finance sample of N orders. 3) Compare to dashboard or export. 4) Log variance beyond tolerance with cause. | Match within agreed tolerance or documented variance with owner sign-off. | High | Finance Manager | Draft |
| TC-030 | NFR-011, BR-017 | US-017 | Role-based deny and logging | Deep link to investigator-only URL | 1) Log in as aggregate-only user. 2) Paste investigator URL. 3) Ask Engineering for deny log line. | Access denied. Deny attempt logged per NFR-011. | High | Engineering Lead | Draft |
| TC-031 | NFR-012, BR-013 | US-021 | Legal template checklist before enforcement comms | Legal owns template ids for test | 1) Open release checklist item for templates tied to disposition or reversal. 2) Confirm version ids for any comms triggered in test. | No production customer comms without Legal approval record, or test uses stub channel only. | High | Compliance / Legal Representative | Draft |
| TC-032 | BR-010, BR-014 | None in US-001 to US-022 | Second approver on high-risk campaign publish | Growth user and peer approver in test, or gap documented | 1) Attempt publish campaign with attributes that trigger BR-010 (deep discount, sitewide, or stackable per BRD). 2) Observe whether second approver is enforced. 3) If feature missing, log as scope gap not as silent pass. | Either second approver is required and audit shows both approvers, or defect or formal deferral captures missing tooling. | High | Marketing / Growth Manager | Draft |

---

## Coverage map (topics from UAT prep)

| Topic | Test cases |
|-------|------------|
| First-time coupon restriction | TC-002 |
| Duplicate account detection | TC-003, TC-004 |
| Shared payment | TC-003 |
| Shared device | TC-004 |
| Shared shipping address | TC-004 |
| Coupon stacking prevention | TC-001 |
| Referral abuse flagging | TC-006 |
| Low-margin SKU discount checks | TC-005 |
| Promotion risk score | TC-008 |
| Manual review queue routing | TC-009 |
| Case assignment | TC-010 |
| SLA tracking | TC-011 |
| Review decision capture | TC-012 |
| Audit trail | TC-013, TC-024 |
| Dashboard filters | TC-014 |
| Exportable reports | TC-015 |
| Role-based access | TC-016, TC-030 |
| Policy exception approval | TC-017 |
| Campaign kill-switch | TC-018 |
| Redemption spike alert | TC-019 |
| Dashboard KPI accuracy | TC-007, TC-029 |
| Reporting definition alignment | TC-007, TC-029 |
| Privacy and access rules | TC-015, TC-022, TC-030 |
| UAT sign-off readiness | TC-025, TC-031 |

---

## Change log

| Version | Note |
|---------|------|
| 0.2 | TC-001 to TC-032 aligned to RTM; business-language steps |
| 0.1 | Replaced older TC-REPORT style sample ids |
