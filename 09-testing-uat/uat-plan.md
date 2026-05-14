# User Acceptance Test (UAT) Plan: PromoLeak Radar

**Organization:** Northline Market (fictional case study)  
**Project:** PromoLeak Radar  
**Version:** Draft for portfolio and workshop rehearsal  
**Related docs:** `04-business-requirements/`, `06-user-stories/`, `07-traceability/requirements-traceability-matrix.md`, `08-solution-design/`, `09-testing-uat/test-cases.md`

This plan is written for business testers (Finance, Marketing / Growth, Fraud / Risk, Operations, Customer Support, Compliance / Legal) and the Product Manager who coordinates the cycle. It is a realistic cut for a BA-led UAT, not a full enterprise test strategy. On a live program, Finance and Legal would tighten numbers, fixtures, and sign-off authority before anyone schedules a formal cycle.

---

## 1. UAT purpose

UAT checks that Northline Market can:

- See promotion leakage and abuse signals in a way Finance will defend (BR-018, NFR-010).
- Work flagged orders in one queue with clear ownership, SLA visibility, and structured outcomes (FR-008 to FR-011).
- Rely on access rules, masking, and exports that match policy (FR-014, FR-015, NFR-003, NFR-011).
- Respond when a code runs hot, using kill-switch and alerts where built (FR-017, FR-018, BR-014).

Passing UAT here means **the business can run the agreed scripts with acceptable outcomes**. It does not replace security pen testing, performance engineering sign-off, or Legal review of customer-facing templates (NFR-012).

---

## 2. UAT scope

**In scope**

- Detection and scoring paths tied to FR-001 through FR-018 that appear in the pilot build list (see RTM).
- Manual review queue behavior: routing, assignment, SLA display, disposition, audit (FR-008 to FR-012).
- Dashboards and filters called out in FR-006 and FR-013, plus exports under FR-014.
- Role-based access and deny paths for at least aggregate, investigator, Growth read-only, and admin (FR-015, NFR-011).
- Policy exception workflow if FR-016 is in the build (otherwise document as deferred).
- Kill-switch and redemption spike alert behavior if FR-017 and FR-018 are in the build.
- NFR smoke checks mapped in `test-cases.md` (performance window, SSO session, privacy masking, audit append behavior, usability script, tie-out sample, Legal checklist item for templates).

**Traceability**

- Test cases **TC-001 through TC-032** align with the Requirements Traceability Matrix. Execute against `test-cases.md` and log defects in `defect-log-template.md` (or your tracker).

---

## 3. Out of scope (for this UAT cycle unless sponsors expand)

- Production cutover, DR drills, and full PCI audit.
- Automated clawback execution if Legal keeps that manual.
- Marketplace partner promo detail if feeds are not in the agreed pilot (BRD parking lot).
- **BR-010** second approver on campaign publish, unless a backlog item and build exist (see TC-032 note in test cases).
- Load testing to prove NFR-007 headroom (documentary evidence only unless SRE joins).

---

## 4. Participants and roles

| Role | Name (fill at kickoff) | Responsibility |
|------|------------------------|------------------|
| UAT Lead / Product Manager | | Schedule, scope guardrails, daily triage, sign-off pack |
| Finance SME | | Tie-out sample (NFR-010), leakage definition footnotes (BR-018), export column approval |
| Marketing / Growth SME | | Golden-path carts for stacking and kill-switch (FR-003, FR-017), campaign context |
| Fraud / Risk SME | | Queue workflows, disposition sense-check, false positive marking |
| Operations SME | | Assignment, SLA breach scenarios, alert response drill |
| Customer Support SME | | Policy exception path (FR-016), read-only visibility where RACI says so |
| Compliance / Legal SME | | Template checklist (NFR-012), masking spot checks (NFR-003) |
| Engineering / QA support | | Environment health, data refresh, defect reproduction notes (not voting on business pass) |
| Executive Sponsor (optional) | | Reads exit summary; does not need to execute scripts |

---

## 5. Entry criteria

- UAT environment URL, test accounts per role, and a **role matrix** published at least two business days before kickoff (NFR-002, FR-015).
- **Test data pack** loaded: known orders for first-time reuse, shared payment, device and address patterns, stacking, referral loop, low-margin SKU, and at least one referral refund scenario (see section 8).
- `test-cases.md` reviewed by UAT Lead and one SME per tower (Finance, Growth, Fraud).
- **No open Sev-1** defects on must-have happy paths defined in section 10 (or sponsor explicitly waives with written risk).
- Finance provides a small **tie-out sample** (order ids and expected flag or dollar posture) or agrees to run TC-029 with synthetic ids only.
- Legal confirms which **customer-facing strings** are allowed in test (NFR-012); if not ready, block scripts that send real customer comms.

---

## 6. Exit criteria

- All **Must** priority functional tests for in-scope FRs are **Executed** with Pass, or Fail with a documented waiver approved by the owning SME and Product Manager.
- NFR smoke set in `test-cases.md` is **Executed** with Pass, or variance documented (example: performance target still TBD, noted with owner and date).
- **Critical defects** (Sev-1 and Sev-2 per section 10) are fixed and retested, or deferred with Executive Sponsor acknowledgment where policy allows.
- Defect log is current: no mystery tickets stuck in "New" without an assignee for more than two business days during active UAT.
- **Sign-off sheet** (or email trail per Northline policy) captured: Finance, Fraud or Ops lead, Growth delegate, Legal as needed for NFR-012 items.

---

## 7. Test environment assumptions

- **Non-production** UAT or staging stack that mirrors production **promo rules shape**, not necessarily full volume.
- Checkout and promo engine either hit the UAT stack or a stubbed service that still persists **policy version ids** on orders (FR-003).
- Warehouse refresh at least daily; if near-line feeds exist, document lag so testers do not file false defects on timing alone.
- Corporate **SSO test tenants** work for PromoLeak URLs (NFR-002). Break-glass local logins, if any, are documented and not the default path.
- Email or Slack for FR-018 alerts lands in a test channel, not customer inboxes.

---

## 8. Test data needs

| Theme | What testers need | Owner to prepare |
|-------|-------------------|------------------|
| First-time coupon | Two accounts that meet BR-001 / BR-002 "blocked linkage" synthetic pattern | Fraud / Data |
| Shared payment | Two accounts sharing a surrogate payment token in policy window (BR-007) | Fraud / Payments liaison |
| Shared device | Multiple new accounts from same device id in rolling window (BR-008) | Fraud |
| Shared address | Matching ship-to hash with conservative pattern (BR-009) | Fraud |
| Stacking | Carts that should allow vs block per published stack order (BR-005) | Growth |
| Referral | Self-referral, closed loop, and post-payout full refund (BR-003, BR-004, BR-012) | Growth / Finance |
| Low margin | SKU on exclusion list with trusted COGS and one with missing COGS (BR-006) | Finance / Merch |
| Campaign reporting | At least two campaigns with known flagged dollars for tie-out (BR-018) | Finance |
| Queue | Cases in New, In review, near SLA breach (BR-011) | Ops |
| Exceptions | Draft exception request with two different people for approver separation (BR-017) | CS |

All ids should be synthetic or masked per Legal. No real customer PII in attachments.

---

## 9. UAT schedule (template)

Adjust to Northline calendars. Example for a two-week rehearsal:

| Day | Activity |
|-----|----------|
| Day 0 | Kickoff (60 min): scope, roles, where to log defects, how to mark "blocked" |
| Day 1 to 3 | Cycle 1: TC-001 to TC-020 core detection, queue, dashboards, access |
| Day 4 | Triage and fix window; retest Sev-1 / Sev-2 |
| Day 5 to 6 | Cycle 2: TC-021 to TC-032, NFR smoke, tie-out, Legal checklist |
| Day 7 | Buffer, retest, exit review |
| Day 8 | Sign-off due (or adjust if sponsor needs more Finance time on TC-029) |

---

## 10. Defect severity definitions (business language)

| Severity | Meaning | Typical response time during active UAT |
|----------|---------|----------------------------------------|
| **Sev-1** | Wrong headline money with no warning, or sensitive PII exposed to the wrong role, or audit missing for a kill-switch or export that should be logged | Same day escalation to Engineering lead and UAT Lead; stop relevant scripts until fixed or waived |
| **Sev-2** | Investigator or Ops cannot complete primary queue or disposition flow; workaround exists but is unsafe or impractical at volume | Fix within agreed build window; retest before exit |
| **Sev-3** | Incorrect label, confusing filter, minor calculation mismatch on a secondary tile with footnote still correct | Schedule in backlog unless trivial same-day fix |
| **Sev-4** | Cosmetic, typo, nice-to-have copy | Pool for polish |

**Priority** (fix order) can differ from severity: a Sev-3 blocking a Legal demo might get Priority 1 by sponsor call.

---

## 11. Sign-off process

1. UAT Lead exports **test execution summary** (pass, fail, blocked, not run) with links to defect ids.
2. Each SME initials their tower on the sign-off sheet (or email) after retests they care about are closed or waived.
3. Finance signs **BR-018 definition version** used during UAT and any variance on TC-029.
4. Legal signs **NFR-012** checklist if any script touched customer-facing enforcement or reversal language.
5. Product Manager files the pack in the project record and communicates "go / no-go / pilot with limits" to the Executive Sponsor.

---

## 12. Risks and mitigations

| Risk | Mitigation |
|------|------------|
| TBD thresholds in BRs cause noisy flags | Freeze a UAT threshold sheet for the cycle; log waivers when behavior is "as coded, not as final policy" |
| Thin referral or payment test data | Block TC-006 / TC-003 with clear "data gap" status instead of fake passes |
| Tester fatigue on queue scripts | Split TC-009 to TC-012 across Fraud and Ops with shared checklist |
| Dashboard numbers move mid-cycle after a definition edit | Lock definition version for UAT window; if it changes, rerun TC-007 and TC-029 |

---

## 13. Open items before UAT

- Confirm which FRs are actually in the build for cycle 1 (especially FR-007, FR-010, FR-016, FR-018 as Should items in the BRD).
- Confirm **BR-010** status: if no story exists, run TC-032 as "document expected behavior gap" only.
- Finalize **tie-out sample** size and tolerance for NFR-010 (Finance).
- Confirm alert channel for FR-018 (email vs Slack) and who is on call during UAT.

---

## Change log

| Date | Author | Note |
|------|--------|------|
| 2026-05-14 | BA case study | Expanded plan for stakeholder-led UAT aligned to TC-001 to TC-032 |
