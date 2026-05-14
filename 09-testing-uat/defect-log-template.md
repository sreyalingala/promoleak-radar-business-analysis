# Defect Log Template

**Project:** PromoLeak Radar  
Copy these columns into Jira / Excel / whatever you actually use. I kept a copy here so the portfolio shows what we tracked.

## Defect record fields

| Field | Description |
|-------|-------------|
| ID | Unique defect id (e.g., DEF-1024) |
| Date raised | |
| Raised by | Name / role |
| Environment | UAT / Staging / other |
| Severity | Sev-1 … Sev-4 (define with team) |
| Priority | Fix now / next build / backlog |
| Status | New / Triaged / In fix / Ready to retest / Closed / Deferred |
| Component | Dashboard / Pipeline / Promo admin / Auth / Other |
| Requirement ref | FR-/US-/TC- id |
| Summary | One line |
| Steps to reproduce | Numbered steps |
| Expected result | |
| Actual result | |
| Evidence | Screenshot link, query id (no PII in public attachments) |
| Owner | Dev assignee |
| Target fix version | |
| Regression test needed? | Y/N |
| Business impact note | Plain language for sponsor if needed |

## Log (placeholder rows — delete when using real tool)

| ID | Summary | Status | Severity | Req ref |
|----|---------|--------|----------|---------|
| DEF-0001 | Example: stale banner missing on pipeline fail | New | 2 | TC-EDGE-01 |
| DEF-0002 | Example: export includes PII column for CS role | New | 1 | NFR-10 |

## Triage rules of thumb

- **Sev-1:** wrong money numbers at aggregate level without warning, or open PII leak.
- **Sev-2:** investigator cannot complete primary workflow; workaround painful.
- **Sev-3:** cosmetic or minor inconsistency with spec.
- **Sev-4:** typo, polish.

## Weekly summary (for steering)

| Week ending | Open | New | Closed | Carried risk |
|-------------|------|-----|--------|--------------|
| | | | | |
