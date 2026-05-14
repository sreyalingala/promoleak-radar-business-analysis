# Dashboard Wireframes (Text): PromoLeak Radar

**Project:** PromoLeak Radar (Northline Market)  
**Format:** Markdown tables and simple blocks for handoff to UX or BI. Not pixel specs.

**Legend:** `[ ]` dropdown or control, `( )` read-only text, `>>` primary action.

---

## Wireframe A: Executive Overview

**User action:** Scan tiles, check trend direction, jump to one campaign if something looks off (role permitting).

### Header area

| Zone | Content |
|------|---------|
| Left | `PromoLeak Radar` + subtitle `Executive Overview` |
| Center | Filters: `[ Date range ]` `[ Channel ]` (category optional, collapsed) |
| Right | `( Last refresh: ____ UTC )` `( Definition: BR-018 v__ )` `>> Open Campaign Performance` |

### KPI cards (single row)

| Card 1 | Card 2 | Card 3 | Card 4 |
|--------|--------|--------|--------|
| **Estimated revenue leakage** | **Coupon abuse rate** | **Manual review volume** | **SLA breach count** |
| `$____` | `__%` | `____ open` | `____` |
| `( vs prior period: __ )` | `( footnoted )` | `( new + in review )` | `( queue SLA )` |

### Main chart areas

| Chart block A (2/3 width) | Chart block B (1/3 width) |
|---------------------------|---------------------------|
| **Leakage trend** (line): estimated leakage vs prior week | **Top driver** (text + mini bar): top campaign by flagged dollars |
| X: day, Y: dollars | `( Campaign: ______ )` |

### Detail table area (lightweight for exec)

| Top campaigns (summary) | |
|---------------------------|--|
| Columns: Campaign, Code, Est. leakage, ROI (footnoted), Redemption spike count | |
| Max 5 rows, `>> View in Campaign Performance` on row | |

### Notes on expected user action

- User confirms whether the week looks directionally right, then either exits or drills with Finance or Growth in the next screen.
- If tiles look stale, user checks refresh chip before alerting Ops (FR-018 alert deep links can land on **Revenue Leakage** instead if we wire it that way).

**Related IDs:** FR-006, FR-013, FR-018, BR-018.

---

## Wireframe B: Revenue Leakage

**User action:** Slice by campaign and reason, validate numerator story, open order list if role allows.

### Header area

| Zone | Content |
|------|---------|
| Left | `Revenue Leakage` |
| Center | `[ Date ]` `[ Campaign ]` `[ Code ]` `[ Category ]` `[ Channel ]` `[ Flag type ]` |
| Right | `( Definition v__ )` `[ Include policy exceptions: Yes / No ]` `>> Export` (if FR-014 allowed) |

### KPI cards

| Estimated revenue leakage | Gross margin impact | Avg discount (flagged orders) | False positive review rate |
|----------------------------|---------------------|-------------------------------|------------------------------|
| `$____` | `$____` | `__%` | `__%` |

### Main chart areas

| Left chart | Right chart |
|------------|-------------|
| **Leakage by reason family** (stacked bar) | **Duplicate vs referral vs first-time** (grouped bar) |
| Categories: stack, margin, duplicate, referral, first-time | Rates footnoted |

### Detail table area

| Flagged orders (limited columns) | |
|----------------------------------|--|
| Order id, Campaign, Code, Flag types, Est. leakage $, Margin unknown Y/N | |
| Row action: `>> Case` (opens queue or case) | |

### Notes on expected user action

- Finance uses include or exclude exceptions only after the published rule is agreed (FR-016, BR-018).
- Investigator uses row drill to queue or order detail; aggregate role sees totals only.

**Related IDs:** FR-005, FR-006, FR-013, FR-014, FR-016, BR-006, BR-018, NFR-010.

---

## Wireframe C: Abuse Detection

**User action:** Compare signal volumes, check false positive rate after rule changes, jump to queue filtered by reason.

### Header area

| Zone | Content |
|------|---------|
| Left | `Abuse Detection` |
| Center | `[ Date ]` `[ Campaign ]` `[ Code ]` `[ Signal type ]` `[ Channel ]` |
| Right | `( Score version: ____ )` `>> Open Manual Review Queue` |

### KPI cards

| Coupon abuse rate | Duplicate account rate | Referral abuse rate | Redemption spike count |
|--------------------|------------------------|---------------------|------------------------|
| `__%` | `__%` | `__%` | `____` |

### Main chart areas

| Chart 1 | Chart 2 |
|---------|---------|
| **Reason code volume** (horizontal bar) | **False positive review rate trend** (line) |
| stack, margin, referral, shared payment, device, address | Uses FR-011 dispositions |

### Detail table area

| Signal detail | |
|---------------|--|
| Columns: Signal, Flags, % of total flags, Notes (static help link) | |
| Row: `>> Filter queue by this signal` | |

### Notes on expected user action

- Fraud sorts signals by volume and false positive trend before asking Data to change a threshold.
- Growth uses same page to see if a specific code drives stacking or margin flags before changing copy or caps.

**Related IDs:** FR-001, FR-002, FR-003, FR-004, FR-005, FR-007, FR-011, FR-018, BR-001, BR-002, BR-005, BR-007.

---

## Wireframe D: Manual Review Queue

**User action:** Triage new work, assign or reassign, watch SLA, record disposition with required fields.

### Header area

| Zone | Content |
|------|---------|
| Left | `Manual Review Queue` |
| Center | `[ Status ]` `[ Assignee / pool ]` `[ SLA state ]` `[ Campaign ]` `[ Risk tier ]` |
| Right | `( Stale data banner if feed late )` `>> New assignment` |

### KPI cards

| New | In review | SLA breach | Avg age (open) |
|-----|------------|------------|----------------|
| `__` | `__` | `__` | `__ h` |

### Main chart areas (optional for Ops lead)

| Small chart | |
|-------------|--|
| **Cases opened vs closed** (last 14 days) | **Breach rate** (line) |

### Detail table area (primary work surface)

| Case / order queue | |
|--------------------|--|
| Columns: Case id, Order id, Campaign, Flags, Risk tier, Age, Due, Assignee, Status | |
| Row select: `>> Open case` | |

### Case drawer (same page, right rail)

| Section | Fields |
|---------|--------|
| Summary | Order id, account id (masked per role), campaign, flags |
| SLA | Due time, breach indicator (FR-010) |
| Assignment | `[ Assignee ]` `[ Pool ]` `>> Save` (FR-009) |
| Disposition | `[ Outcome ]` required fields, notes (FR-011) |
| Audit | `( Last config or status changes )` link to audit view (FR-012) |

### Notes on expected user action

- Investigator assigns on intake, updates disposition once facts are known, never closes high-risk without required fields.
- Lead sorts by SLA breach and reassigns for PTO (FR-009).

**Related IDs:** FR-008, FR-009, FR-010, FR-011, FR-012, FR-015, BR-011, NFR-003.

---

## Changelog

| Version | Note |
|---------|------|
| 0.2 | Added four recruiter-friendly wireframes aligned to dashboard requirements |
| 0.1 | Earlier ASCII sketch (retired; see git history if needed) |
