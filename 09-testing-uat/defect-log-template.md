# Defect Log Template: PromoLeak Radar UAT

**Project:** PromoLeak Radar (Northline Market)  
**Use:** Copy columns into Excel, Google Sheets, or your work tracker. This file stays in the repo as the **shape** Northline testers would use during UAT.

---

## Severity definitions (same meaning as `uat-plan.md`)

| Severity | Meaning |
|----------|---------|
| **Sev-1** | Wrong headline totals without warning, sensitive PII exposed to wrong role, or missing audit for kill-switch or export when policy requires it |
| **Sev-2** | Primary queue or disposition flow blocked for investigator or Ops with no safe workaround |
| **Sev-3** | Wrong secondary label, confusing filter, small mismatch on non-headline tile when footnote still correct |
| **Sev-4** | Cosmetic or typo |

**Priority** (fix order): **P1** fix during active UAT if possible, **P2** next build, **P3** backlog. Priority can differ from severity if Legal or Finance escalates.

---

## Defect workflow (simple)

1. **New:** Tester logs defect with steps and test case id.  
2. **Triaged:** UAT Lead assigns owner and sets severity or sends back for more detail.  
3. **In fix:** Engineering or vendor works item.  
4. **Ready to retest:** Fix deployed to UAT; original tester notified.  
5. **Closed:** Retest passed, or closed as duplicate or not a defect.  
6. **Deferred:** Sponsor accepts risk; must include reason and date for revisit.

Retest uses the **same test case id** when possible so traceability stays clean.

---

## Defect log (column reference)

| Column | Description |
|--------|-------------|
| Defect ID | Unique id, example DEF-2026-014 |
| Date logged | Calendar date |
| Logged by | Name and role (example: Jordan Lee, Finance SME) |
| Related Test Case ID | TC-001 to TC-032 from `test-cases.md` |
| Requirement ID | FR, NFR, BR, or US id from existing BRD files |
| Defect summary | One plain-language line |
| Steps to reproduce | Numbered steps another tester can follow |
| Expected result | What the script or policy said should happen |
| Actual result | What happened instead |
| Severity | Sev-1 to Sev-4 |
| Priority | P1, P2, or P3 |
| Assigned owner | Person fixing or coordinating |
| Status | New, Triaged, In fix, Ready to retest, Closed, Deferred |
| Resolution notes | What changed, build id or release tag if known |
| Retest result | Pass, Fail, or Blocked with short note |
| Sign-off owner | SME who accepts closure for their tower |

---

## Example defect rows (sample data, delete when live)

| Defect ID | Date logged | Logged by | Related Test Case ID | Requirement ID | Defect summary | Steps to reproduce | Expected result | Actual result | Severity | Priority | Assigned owner | Status | Resolution notes | Retest result | Sign-off owner |
|-----------|-------------|-----------|----------------------|----------------|------------------|---------------------|-----------------|---------------|----------|----------|----------------|--------|------------------|---------------|----------------|
| DEF-2026-001 | 2026-05-20 | A. Patel, Fraud SME | TC-009 | FR-008, US-007 | Queue shows empty when promo job failed | 1) Stop promo facts job in UAT. 2) Refresh queue. 3) Note banners and row counts. | Stale or error banner, no false empty healthy state | Empty queue, no banner | Sev-2 | P1 | Eng: R. Kim | Closed | Banner added in build UAT-12 | Pass | Fraud SME |
| DEF-2026-002 | 2026-05-21 | M. Chen, Finance SME | TC-015 | FR-014, NFR-003 | Export included full email for aggregate role | 1) Log in as aggregate-only. 2) Export campaign slice. 3) Open CSV. | No direct email column | Email column present | Sev-1 | P1 | Eng: R. Kim | Ready to retest | Column mask enforced build UAT-13 | Pending | Compliance |
| DEF-2026-003 | 2026-05-22 | L. Ortiz, Growth SME | TC-018 | FR-017, US-019 | Kill-switch audit missing rollback entry | 1) Apply cap. 2) Roll back cap. 3) Open audit for code. | Two rows, cap and rollback | Only cap row | Sev-2 | P2 | Eng: R. Kim | New | | | Marketing SME |
| DEF-2026-004 | 2026-05-23 | J. Lee, Finance SME | TC-029 | NFR-010, BR-018 | Footnote still showed old definition version after publish | 1) Publish definition v3. 2) Hard refresh dashboard. 3) Read footnote. | Footnote v3 and effective timestamp | Footnote v2 | Sev-2 | P1 | Product Manager | Triaged | Root cause: cache TTL | Pending | Finance SME |
| DEF-2026-005 | 2026-05-24 | S. Nguyen, Ops SME | TC-011 | FR-010, US-009 | Breach color missing when one minute past due | 1) Use fixture case one minute past due. 2) Observe row styling. | Breach styling on | No styling change | Sev-3 | P3 | Eng backlog | Deferred | Sponsor accepted for pilot; fix by June | N/A | Ops lead |

---

## Notes for business testers

- **Always attach the test case id (TC-xxx)** so UAT Lead can trace to requirements without guessing.
- **One defect per distinct failure.** If three steps fail for different reasons, open three tickets or clearly split sections so Engineering does not bundle unrelated fixes.
- **Screenshots:** Mask customer data. If you cannot mask, describe the issue in words and ask Engineering to reproduce in UAT with synthetic ids.
- **"Works as coded" is not always a pass.** If behavior disagrees with signed BRD or workshop notes, log it and let Product Manager decide waiver vs defect.
- **Do not mark Pass** on TC-032 if second approver is missing; log a scope gap or deferral instead so the portfolio (and a real audit) stay honest.

---

## Weekly summary (optional paste block)

| Week ending | Open defects | New | Closed | Deferred with sponsor | Notes |
|-------------|----------------|-----|--------|-------------------------|-------|
| | | | | | |
