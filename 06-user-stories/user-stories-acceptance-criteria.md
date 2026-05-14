# User Stories and Acceptance Criteria: PromoLeak Radar (Northline Market)

> **Note:** Stories below map to **FR-001 through FR-018**, **NFR-001 through NFR-012**, and **BR-001 through BR-018** in `04-business-requirements/`. They are written for portfolio review, not as a signed sprint commitment. TBD values need sponsor, Data, and Legal input on a real program.

---

## US-001

| Field | Content |
|-------|---------|
| **Story ID** | US-001 |
| **Related requirement ID** | FR-001, BR-001, BR-002 |
| **Priority** | Must Have |
| **User story** | As a **Fraud / Risk Analyst**, I want **first-time coupon reuse flagged against the agreed customer definition**, so that **Northline Market stops paying multiple welcome discounts to the same person behind fresh accounts**. |
| **Acceptance criteria** | **Given** an order uses a first-time or new-customer code, **when** the order is evaluated against the published customer definition and lookback window, **then** the system attaches a reason code when reuse is suspected and never drops the row silently if the job fails. **Given** a false positive, **when** I mark it as such with a short reason, **then** the disposition is stored and available for tuning. |
| **Business notes** | Legal must approve enriched signals before they block checkout in v1; BR-002 lookback is still TBD. |

---

## US-002

| Field | Content |
|-------|---------|
| **Story ID** | US-002 |
| **Related requirement ID** | FR-002, BR-007 |
| **Priority** | Must Have |
| **User story** | As a **Fraud / Risk Analyst**, I want **duplicate account signals based on shared payment**, so that **I can queue obvious payment-farm patterns without waiting for Finance close**. |
| **Acceptance criteria** | **Given** two accounts share a stored payment token or card hash within the policy window, **when** either account applies a first-time or high-value promo, **then** a flag is raised with signal type “shared payment.” **Given** PCI constraints, **when** the signal is unavailable, **then** the UI shows “signal not available” instead of a wrong green check. |
| **Business notes** | Coordinate with Data on hash availability; BR-007 thresholds are TBD. |

---

## US-003

| Field | Content |
|-------|---------|
| **Story ID** | US-003 |
| **Related requirement ID** | FR-003, BR-005 |
| **Priority** | Must Have |
| **User story** | As a **Marketing / Growth Manager**, I want **stacking validated against the published stack policy at capture**, so that **customers cannot combine codes in ways we never approved**. |
| **Acceptance criteria** | **Given** a cart with two promos, **when** checkout evaluates stack order, **then** the outcome matches the published allow or deny list and stores the **policy version id** on the order. **Given** a stack that violates BR-005, **when** policy says block, **then** checkout blocks with a customer-safe message; **when** policy says warn only in v1, **then** the order stores a warn flag for review. |
| **Business notes** | Marketing must supply golden orders for UAT; “warn vs block” is a sponsor call. |

---

## US-004

| Field | Content |
|-------|---------|
| **Story ID** | US-004 |
| **Related requirement ID** | FR-004, BR-003, BR-004, BR-012 |
| **Priority** | Must Have |
| **User story** | As a **Finance Manager**, I want **referral abuse patterns flagged and refund-aware**, so that **referral dollars do not pay out on self-deals or on orders that fully refund inside the policy window**. |
| **Acceptance criteria** | **Given** a referral pattern matches BR-004 (self-referral or closed loop), **when** the referral job runs, **then** the payout path is held or flagged per Legal-approved rules. **Given** a full refund within the BR-012 window after a referral payout event, **when** netting runs, **then** Finance sees a reversible or netting entry with an audit id. |
| **Business notes** | BR-012 timing must match what Legal wrote in customer terms. |

---

## US-005

| Field | Content |
|-------|---------|
| **Story ID** | US-005 |
| **Related requirement ID** | FR-005, BR-006 |
| **Priority** | Must Have |
| **User story** | As a **Finance Manager**, I want **low-margin SKUs flagged when discount depth breaches the floor**, so that **we catch category promos that were never supposed to go that deep**. |
| **Acceptance criteria** | **Given** a line on the exclusion list with trusted COGS, **when** effective margin after promo falls below the floor, **then** the order or line is flagged with reason “margin floor.” **Given** COGS is missing, **when** the job runs, **then** the line is tagged “margin unknown” and excluded from headline leakage $ unless Finance opts in via BR-018 footnote. |
| **Business notes** | Merchandising may need to own category list updates with Finance. |

---

## US-006

| Field | Content |
|-------|---------|
| **Story ID** | US-006 |
| **Related requirement ID** | FR-007, BR-011 |
| **Priority** | Should Have |
| **User story** | As an **Operations Manager**, I want **a risk score or tier on each flagged order**, so that **the team works highest risk first during a spike**. |
| **Acceptance criteria** | **Given** configured weights for stacking, margin breach, referral, and duplicate signals, **when** scoring runs, **then** each order shows a tier and the **score version id**. **Given** I open the score detail, **when** I expand it, **then** I see which signals fired (no black box). |
| **Business notes** | Start with a small weight set; BR-011 ties manual review triggers to score tier TBD. |

---

## US-007

| Field | Content |
|-------|---------|
| **Story ID** | US-007 |
| **Related requirement ID** | FR-008, BR-011 |
| **Priority** | Must Have |
| **User story** | As a **Fraud / Risk Analyst**, I want **one manual review queue for promo flags**, so that **I am not chasing tickets, DMs, and spreadsheets for the same incident**. |
| **Acceptance criteria** | **Given** a new flag from any detection path, **when** the pipeline succeeds, **then** a queue item appears in **New** with links to order and campaign. **Given** the pipeline fails, **when** I open the dashboard, **then** I see a stale-data banner and no empty queue that looks “healthy.” |
| **Business notes** | Queue owner still needs Ops or Fraud head to name in charter. |

---

## US-008

| Field | Content |
|-------|---------|
| **Story ID** | US-008 |
| **Related requirement ID** | FR-009 |
| **Priority** | Must Have |
| **User story** | As an **Operations Manager**, I want **cases assigned to people or pools**, so that **PTO and shift handoffs do not strand work**. |
| **Acceptance criteria** | **Given** I assign a case to an investigator, **when** I save, **then** the assignment is logged with user and timestamp. **Given** I reassign for PTO, **when** I save, **then** the prior assignee can still read history but cannot close without permission if policy says so. |
| **Business notes** | Ties to FR-012 for assignment audit. |

---

## US-009

| Field | Content |
|-------|---------|
| **Story ID** | US-009 |
| **Related requirement ID** | FR-010 |
| **Priority** | Should Have |
| **User story** | As an **Operations Manager**, I want **SLA clocks on cases**, so that **nothing sits for days while a code is still bleeding**. |
| **Acceptance criteria** | **Given** SLA parameters configured per priority class, **when** a case ages past its due time, **then** the row shows breach styling and appears on a breach report. **Given** I change SLA defaults, **when** I save, **then** only **new** cases pick up the new SLA unless sponsor approves retroactive apply. |
| **Business notes** | Start with simple P3 and P2 classes; align to escalation doc P levels later. |

---

## US-010

| Field | Content |
|-------|---------|
| **Story ID** | US-010 |
| **Related requirement ID** | FR-011 |
| **Priority** | Must Have |
| **User story** | As a **Fraud / Risk Analyst**, I want **structured disposition with required fields**, so that **Customer Support and Finance see the same outcome story**. |
| **Acceptance criteria** | **Given** I try to close a high-risk disposition, **when** required fields are blank, **then** save is blocked with inline errors. **Given** I close with “false positive,” **when** I save, **then** the reason code is mandatory and stored for tuning (FR-001 / FR-007 feedback loop). |
| **Business notes** | Legal reviews customer-facing outcomes tied to certain disposition codes (NFR-012). |

---

## US-011

| Field | Content |
|-------|---------|
| **Story ID** | US-011 |
| **Related requirement ID** | FR-012, BR-016, NFR-005 |
| **Priority** | Must Have |
| **User story** | As a **Compliance / Legal Representative**, I want **an append-style audit trail for config, kill-switch, and case changes**, so that **Northline Market can answer “who changed what and when.”** |
| **Acceptance criteria** | **Given** a user changes a threshold or fires a kill-switch, **when** the change commits, **then** an audit row records user, time, old value, new value. **Given** an auditor exports the trail for a date range, **when** export completes, **then** the export itself is logged per FR-012 scope. |
| **Business notes** | Retention follows NFR-008; Engineering confirms append-only config in prod. |

---

## US-012

| Field | Content |
|-------|---------|
| **Story ID** | US-012 |
| **Related requirement ID** | FR-006, BR-018 |
| **Priority** | Must Have |
| **User story** | As a **Finance Manager**, I want **a campaign-level leakage dashboard using the signed leakage definition**, so that **Marketing and I stop exporting different cuts of the same week**. |
| **Acceptance criteria** | **Given** Finance-approved definition version **v**, **when** I open the campaign view, **then** totals match the documented formula for that version including exclusions for cancelled and test orders. **Given** I drill to orders, **when** I have investigator rights, **then** I see the order list with reason codes. |
| **Business notes** | BR-018 numerator and denominator must be spelled out in the UI footnote. |

---

## US-013

| Field | Content |
|-------|---------|
| **Story ID** | US-013 |
| **Related requirement ID** | FR-006 |
| **Priority** | Should Have |
| **User story** | As a **Marketing / Growth Manager**, I want **a campaign ROI slice that uses fields I trust**, so that **I can defend spend without pretending leakage does not exist**. |
| **Acceptance criteria** | **Given** a campaign id, **when** I open the ROI view, **then** I see promo spend, attributed revenue, and the same leakage proxy Finance uses (or a footnoted delta if Marketing still uses a secondary metric). **Given** data is incomplete, **when** I load the view, **then** missing fields show “not available” instead of zero. |
| **Business notes** | Same marts as US-012; avoid two sources of truth for promo spend. |

---

## US-014

| Field | Content |
|-------|---------|
| **Story ID** | US-014 |
| **Related requirement ID** | FR-006 |
| **Priority** | Could Have |
| **User story** | As an **Executive Sponsor**, I want **a tiny headline strip (three tiles max)**, so that **I can see directionally if leakage is worse than last week without a forty-slide pack**. |
| **Acceptance criteria** | **Given** Finance has signed the three headline metrics, **when** I open the exec strip, **then** only those metrics render with the version footnote. **Given** Finance has not signed, **when** I open the strip, **then** the UI shows “pending Finance sign-off” placeholders. |
| **Business notes** | Could ship after US-012 if time is tight. |

---

## US-015

| Field | Content |
|-------|---------|
| **Story ID** | US-015 |
| **Related requirement ID** | FR-013, NFR-001 |
| **Priority** | Must Have |
| **User story** | As a **Finance Manager**, I want **dashboard filters that match how I run investigations**, so that **I can slice by campaign, code, category, channel, and flag type without asking Data for a new pull**. |
| **Acceptance criteria** | **Given** I apply a valid filter combination, **when** results return, **then** response time stays within the NFR-001 target on the reference dataset. **Given** I pick an out-of-retention date, **when** I apply, **then** I get a clear validation error. |
| **Business notes** | Data sets the max retention window per policy. |

---

## US-016

| Field | Content |
|-------|---------|
| **Story ID** | US-016 |
| **Related requirement ID** | FR-014, NFR-003 |
| **Priority** | Must Have |
| **User story** | As a **Finance Manager**, I want **exports with role-appropriate columns**, so that **I can take a board pack slice without leaking PII to people who should only see aggregates**. |
| **Acceptance criteria** | **Given** my role is aggregate-only, **when** I request an export, **then** PII columns are absent and the attempt is logged. **Given** my role is investigator, **when** I export, **then** I only see Legal-approved columns and the export is logged. |
| **Business notes** | Legal attaches the approved column matrix to the release record (NFR-012 culture, not only templates). |

---

## US-017

| Field | Content |
|-------|---------|
| **Story ID** | US-017 |
| **Related requirement ID** | FR-015, NFR-002, NFR-011, NFR-003 |
| **Priority** | Must Have |
| **User story** | As an **Engineering Lead**, I want **SSO plus least-privilege roles for PromoLeak**, so that **Northline Market does not create another shadow admin surface**. |
| **Acceptance criteria** | **Given** a user without investigator rights, **when** they deep link to an investigation URL, **then** access is denied and the deny is logged (NFR-011). **Given** a session sits idle past policy, **when** the user returns, **then** re-auth is required per NFR-002 session rules. **Given** investigator view, **when** PII is masked per NFR-003, **then** masking matches the Legal table examples in UAT. |
| **Business notes** | Negative matrix is part of exit criteria. |

---

## US-018

| Field | Content |
|-------|---------|
| **Story ID** | US-018 |
| **Related requirement ID** | FR-016, BR-017 |
| **Priority** | Should Have |
| **User story** | As a **Customer Support Manager**, I want **policy exceptions captured with requester, approver, and window**, so that **goodwill credits do not look like secret shadow promos**. |
| **Acceptance criteria** | **Given** an agent requests an exception, **when** they submit without a second approver, **then** the workflow blocks. **Given** an approver is the same person as requester, **when** they try to approve, **then** the system blocks per BR-017. **Given** an exception is active, **when** Finance runs leakage totals, **then** Finance can include or exclude exceptions per their published rule. |
| **Business notes** | Finance must publish how exceptions hit BR-018. |

---

## US-019

| Field | Content |
|-------|---------|
| **Story ID** | US-019 |
| **Related requirement ID** | FR-017, BR-014 |
| **Priority** | Must Have |
| **User story** | As a **Marketing / Growth Manager**, I want **a kill-switch or cap on a live code**, so that **Northline Market can stop the bleeding without waiting for a full deploy cycle every time**. |
| **Acceptance criteria** | **Given** I have authority, **when** I cap or disable a code, **then** new checkouts honor the change within the agreed latency and an audit row is written. **Given** I roll back the change, **when** I save, **then** audit captures rollback with user and time. |
| **Business notes** | Latency target belongs in NFR-001 discussion with Engineering. |

---

## US-020

| Field | Content |
|-------|---------|
| **Story ID** | US-020 |
| **Related requirement ID** | FR-018, BR-014 |
| **Priority** | Should Have |
| **User story** | As an **Operations Manager**, I want **alerts when redemptions or flags spike**, so that **I open the dashboard before Finance finds the problem at close**. |
| **Acceptance criteria** | **Given** a threshold breach for a campaign or global window, **when** the monitor runs, **then** alert fires to the agreed channel with campaign id and deep link. **Given** two breaches in ten minutes, **when** dedupe rules apply, **then** I do not get twenty identical pages unless sponsor asked for that. |
| **Business notes** | BR-014 may also force Marketing pause; coordinate alert vs. human process. |

---

## US-021

| Field | Content |
|-------|---------|
| **Story ID** | US-021 |
| **Related requirement ID** | NFR-006, NFR-010, FR-001 to FR-018 (smoke) |
| **Priority** | Should Have |
| **User story** | As a **Product Manager**, I want **a guided UAT pack that walks primary FR flows**, so that **we do not “go live” with only happy-path QA**. |
| **Acceptance criteria** | **Given** the UAT script for Finance and Fraud, **when** testers finish, **then** pass or fail is recorded per story with evidence links. **Given** NFR-006 usability tasks, **when** a tester cannot finish without SQL, **then** the story fails UAT until UX is fixed or waived in writing by sponsor. |
| **Business notes** | Include NFR-012 checklist for any story that touches customer comms. |

---

## US-022

| Field | Content |
|-------|---------|
| **Story ID** | US-022 |
| **Related requirement ID** | BR-018, NFR-010 |
| **Priority** | Must Have |
| **User story** | As a **Finance Manager**, I want **reporting definitions versioned and tied to the dashboard**, so that **when someone asks why the number moved, we can point to a definition change, not a bug hunt**. |
| **Acceptance criteria** | **Given** Finance publishes definition version **v+1**, **when** the dashboard loads, **then** the footnote shows **v+1** and the effective timestamp. **Given** a tie-out sample of **N** orders, **when** Finance reruns the check, **then** variance is inside the NFR-010 tolerance or a written variance note is attached. |
| **Business notes** | This story is the paperwork friend of US-012; do not ship headline tiles without it. |
