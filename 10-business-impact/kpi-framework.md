# KPI Framework: PromoLeak Radar (Northline Market)

**Project:** PromoLeak Radar  
**Audience:** Finance, Marketing / Growth, Fraud / Risk, Operations, Product, Data  
**Status:** Draft for sponsor review. Ties to **BR-018** (reporting definitions), **FR-006** and **FR-013** (dashboards and filters), and **NFR-010** (Finance tie-out).

This framework is what Northline would use after PromoLeak reporting and the review queue exist. It is not a substitute for signed Finance definitions. Until those sign, every KPI below carries a **definition version** footnote in the dashboard (see `08-solution-design/dashboard-requirements.md` and **US-022**).

---

## Reporting definition rules (apply to all KPIs)

1. **Numerator and denominator** for any rate are published by Finance and versioned (BR-018). Cancelled orders, test orders, and known bad feeds follow the exclusion table Finance owns.  
2. **False positive** and **confirmed abuse** use disposition codes from the manual review process (FR-011), not informal email.  
3. **Margin unknown** lines (FR-005) are excluded from gross margin impact unless Finance turns on an explicit include flag for a pilot read.  
4. **Policy exceptions** (FR-016, BR-017) are tagged so Finance can run reports with include or exclude, and the active choice is named on the slide footnote.  
5. Any KPI that uses referral or payment signals documents **data lag** next to the number when feeds are out of sync (see stakeholder pain in `01-project-overview/business-case.md`).

---

## KPI catalog

| KPI name | Definition | Formula | Data source | Owner | Reporting frequency | Target or threshold | Business decision supported | Notes or caveats |
|----------|------------|---------|-------------|-------|---------------------|----------------------|-----------------------------|------------------|
| Estimated revenue leakage | Finance-approved sum of promo discount dollars on orders in the flagged set for the period, minus orders marked false positive (BR-018) | Sum(promo discount $ on flagged orders in scope) minus Sum(promo discount $ on false positive dispositions in period) | Data Warehouse mart fed from OMS, Promotion Engine, PromoLeak rules output | Finance Manager | Weekly for ops; monthly for exec | Baseline TBD after 4-week stable run; then month-over-month direction and band vs plan | Board and monthly close narrative; where to fund investigation vs new promos | Definition version must print on every view; marketplace orders may be excluded until feed quality is known |
| Coupon abuse rate | Share of orders (or promo dollars) in scope that hit coupon-related abuse flags (stacking, first-time reuse, depth on excluded categories as Finance defines "abuse family") | Numerator: orders or dollars with coupon-abuse flag family; Denominator: Finance-published eligible orders or dollars | Warehouse + PromoLeak reason codes | Fraud / Risk Analyst | Weekly | Threshold TBD; first goal is stable measurement, not a random % | Whether to tighten stack policy, cap codes, or retrain CS scripts | Do not mix referral-only flags into this rate without relabeling |
| Duplicate account rate | Orders or accounts with duplicate linkage signals (payment, device, address per BR-007 to BR-009) divided by Finance denominator | Count(flagged duplicate signal) / denominator definition vX | Account service, payments hash, device and address features in warehouse | Fraud / Risk Analyst | Weekly | TBD; watch week-over-week spikes after rule changes | Allowlist tuning, device graph investment, or pausing aggressive address match | High false positive risk on address; publish confidence band in analyst notes |
| Referral abuse rate | Referral-tagged abuse flags divided by eligible referral orders or dollars | Count(referral abuse flags) / eligible referral denominator vX | Referral Service + warehouse | Marketing / Growth Manager | Weekly | TBD; pair with Legal on any public wording before hard enforcement | Referral structure changes, milestone edits, payout holds | Refund timing (BR-012) must be in the same story as the rate or Finance will not trust it |
| Campaign ROI | Promo-attributed revenue and margin vs promo cost for a campaign (Growth and Finance use one mart with footnoted deltas if needed) | (Attributed margin dollars minus promo cost) / promo cost, or agreed alternate per Finance | Campaign tables, order facts, promo applications | Marketing / Growth Manager | Weekly during live promos; monthly otherwise | Campaign plan targets set by Growth; Finance flags outliers | Continue, cap, or kill a campaign; budget reallocation | US-013 style footnote if Growth still uses a secondary view |
| Gross margin impact | Estimated margin dollars lost or at risk on flagged orders where COGS is trusted; excludes margin unknown unless Finance opts in | Sum( (list or sell basis per Finance) minus COGS minus net promo ) on flagged trusted-COGS lines, scoped to definition vX | OMS lines, Product Catalog COGS, promo allocation | Finance Manager | Monthly for exec; weekly for Finance deep dive | Compare to FP&A promo margin bridge | Category exclusions, merch actions, vendor renegotiation where promo depth was the trigger | FR-005 unknown COGS path must be visible as a separate line, not buried |
| Average discount per order | Mean effective promo discount dollars per order in the selected slice | Sum(promo discount $) / Count(orders) for filter context | OMS + promo facts | Data Analyst | Weekly | Track vs plan by campaign; no universal magic number | Depth checks on sitewide events; sense-check after rule changes | Include shipping and fees per Finance exclusion table |
| Manual review volume | Count of cases or distinct orders in New, In review, waiting on Growth or Legal, plus closed in period | Count by status bucket per day or week | Manual Review Queue (FR-008) | Operations Manager | Daily during incidents; weekly in steady state | Staffing plan vs agreed band; spike triggers escalation (BR-014) | Hiring, shift coverage, pause requests to Growth | Pipeline failure is not zero volume; use banner logic from UAT TC-009 |
| SLA breach count | Cases past due time per SLA class (FR-010) | Count(cases where now greater than due time) | Queue + SLA config | Operations Manager | Daily when SLA live; weekly summary | Target near zero for P1 campaigns after kill-switch discipline | Process fix, tooling fix, or temporary cap on new flags | SLA parameters owned by Ops with sponsor visibility |
| False positive review rate | Share of closed cases marked false positive over closed cases in period | Count(disposition = false positive) / Count(closed cases) | Queue dispositions (FR-011) | Fraud / Risk Analyst | Weekly | Band TBD; rising rate after a rule push means tune before Ops loses trust | Threshold tuning, signal retirement, training | Low rate is not always good if team is afraid to use the code; spot check samples |
| Redemption spike count | Count of alert events when redemption or flag volume crosses threshold in window (FR-018) | Count(alert events) from alert log by campaign or global | Rules layer + alert channel | Operations Manager | Per incident plus weekly rollup | Thresholds set with Growth so alerts are not muted | Early cap or kill-switch; weekend coverage | Dedup rules per US-020; tie to BR-014 human response time in ops runbook |
| Policy exception rate | Count or dollars of active policy exceptions (FR-016, BR-017) over eligible orders or accounts | Count(active exceptions) / denominator per Finance, or Sum(exception benefit $) / promo $ | Exception workflow + orders | Customer Support Manager | Monthly | Growth and Finance set acceptable band; spikes trigger policy review | Goodwill policy, VIP handling, audit readiness | Same-person approval must stay zero in production metrics |
| Reward reversal amount | Dollars reversed or netted for confirmed abuse or refund rules (BR-012, BR-013) | Sum(reversal $) in period per Finance sign convention | Referral wallet or finance adjustment feed | Finance Manager | Monthly | Track vs referral budget and Legal template usage | Budget true-up; Legal review of high-volume reversal reasons | Only Legal-approved scripts count as production-ready for customer-facing totals |
| Campaign pause count | Count of pauses or kill-switch actions on campaigns or codes (FR-017, BR-014) | Count(audit events of type pause, cap, disable) | Audit log + promo admin | Marketing / Growth Manager | Weekly | No fixed "lower is better"; context in incident log | Post-mortem on publish process, approver discipline, BR-010 coverage | Pauses without audit row are a defect, not a KPI success |

---

## KPI ownership notes

- **Finance** owns numerator and denominator for money and margin KPIs. If Finance and Growth disagree, the dashboard shows Finance vX on the headline tile and may show a secondary Growth field only with a footnote (per **US-012** / **US-013**).  
- **Fraud / Risk** owns interpretation of abuse and duplicate rates and partners with Data on signal quality.  
- **Operations** owns SLA and queue volume staffing narrative.  
- **Marketing / Growth** owns campaign ROI targets and pause count context (why we stopped a code).  
- **Compliance / Legal** does not own the rate math; they own **template and attribute** gates (NFR-012, BR-015) that decide whether a KPI is allowed to drive customer-facing action.

---

## Known measurement gaps

- **Marketplace** orders may lack full promo detail; Finance should exclude or footnote until parity is documented (BRD parking lot).  
- **Device and address** signals carry higher false positive rates; publish alongside duplicate account rate, not as a single "truth."  
- **Lag** between cart, OMS, referral payout, and refund events can distort referral abuse rate and reversal amount for a few days after month-end.  
- **BR-010** second approver is not in the current user story set; **campaign pause count** should not be interpreted as proof that publish-time governance is fixed.

---

## Weekly vs monthly review cadence

| Cadence | KPIs (typical set) | Who leads |
|---------|-------------------|-----------|
| **Weekly** (30 to 45 min ops and fraud) | Manual review volume, SLA breach count, false positive review rate, redemption spike count, coupon abuse rate, duplicate account rate, estimated revenue leakage (directional), average discount per order on hot campaigns | Operations Manager with Fraud / Risk Analyst |
| **Weekly** (Growth and Finance optional slice) | Campaign ROI, campaign pause count, referral abuse rate on live referral pushes | Marketing / Growth Manager with Finance Manager |
| **Monthly** (exec and board prep) | Estimated revenue leakage (vX locked for the month), gross margin impact, reward reversal amount, policy exception rate, year-to-date trend of abuse rates | Finance Manager with Executive Sponsor |

---

## Change log

| Date | Author | Note |
|------|--------|------|
| 2026-05-14 | BA case study | Expanded KPI catalog with formulas, owners, and governance notes |
