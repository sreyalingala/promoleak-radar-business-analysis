# Business Rules: PromoLeak Radar (Northline Market)

> **Note:** Rules below are **draft** for the case study. They assume early discovery input. **Marketing / Growth**, **Finance**, **Legal**, and **Fraud or Risk** must validate before Northline Market treats them as binding policy or customer-facing commitment.

**Project:** PromoLeak Radar  
**Version:** 0.2 draft

---

## Business rules catalog

| Rule ID | Business rule | Applies to | Rule owner | Exception allowed | Notes |
|---------|----------------|------------|------------|-------------------|-------|
| BR-001 | First-time buyer coupon: **one redemption per eligible customer** per Northline Market definition (account-based at minimum; enriched match if Legal approves signals). | First-time and new-customer codes | Marketing / Growth Manager | Goodwill credit with **single** approver and cap, logged in CRM | Definition of “customer” must match what checkout enforces or exceptions are documented. |
| BR-002 | First-time codes **cannot** be reused on a second account that shares a **blocked linkage** (see BR-006 through BR-008) within the lookback window **TBD** days. | First-time promos | Fraud / Risk Analyst | Legal-approved manual override with ticket id | Lookback and signal list need Data and Legal sign-off. |
| BR-003 | Referral reward pays only when the referee meets **milestone TBD** (example: first paid order shipped) and passes fraud checks in referral service rules. | Referral program | Marketing / Growth Manager | Manual payout correction with dual approval per Finance table | Milestone must match customer-facing terms. |
| BR-004 | Self-referral and **closed-loop** referral among linked accounts (per BR-006 to BR-008) are **ineligible** for payout; accrued credit may be voided per Legal template. | Referral | Compliance / Legal Representative | None without Legal and Growth exec written approval | Wording of “void” needs Legal exact language. |
| BR-005 | **Stacking:** unless a campaign is marked “stackable with list X,” a customer may apply **at most TBD** promotional discounts on the same order, in the published application order. | Cart coupons, auto-promos | Marketing / Growth Manager | Emergency campaign flag with owner and expiry | Engineering must enforce same order Growth publishes. |
| BR-006 | **Discount depth:** if effective line discount pushes **margin below floor TBD%** for a category on the exclusion list, order is **flagged** (not auto-cancelled in v1 unless Legal agrees). | Low-margin SKUs and categories | Finance Manager | Merchandising seasonal exclusion list update | COGS source must be trusted or rule falls back to “flag only.” |
| BR-007 | **Duplicate account signal (payment):** two or more accounts with same **stored payment token or card hash** within **TBD** days using first-time or high-value codes → flag for review. | Checkout accounts | Fraud / Risk Analyst | False positive disposition in queue | PCI and Legal govern what can be stored or compared. |
| BR-008 | **Duplicate account signal (device):** **TBD** or more new accounts per device id in rolling **TBD** days → flag. | Account creation, logins | Fraud / Risk Analyst | Known family or business shared device list (small allowlist) | Device graph quality limits confidence; tune thresholds. |
| BR-009 | **Duplicate account signal (address):** shipping address hash match across accounts with **TBD** pattern (new account + high promo same week) → flag. | Orders | Fraud / Risk Analyst | Gift send, dorms, corporate ship-to allowlist process | High false positive risk; start conservative. |
| BR-010 | **Campaign approval:** codes with **discount depth > TBD%** OR **audience = sitewide** OR **stackable = yes** require **second approver** (Growth peer or Ops lead per RACI). | New campaigns | Marketing / Growth Manager | Executive Sponsor pre-approved seasonal list | Prevents single-person publish mistakes. |
| BR-011 | **Manual review trigger:** any order scoring above **TBD** risk tier, or breaching BR-005 or BR-006, opens or updates a **queue** item (no silent drop). | Flagged orders | Operations Manager | Auto-close only for defined benign tests in non-prod | SLA in Ops runbook. |
| BR-012 | **Refunds and returns:** if an order that triggered referral payout is **fully refunded** within **TBD** days, referral credit is **reversed or netted** per Finance policy and Legal template. | Referral payouts | Finance Manager | Partial refund proration rule documented by Finance | Engineering must emit events Finance can reconcile. |
| BR-013 | **Reward reversal** for confirmed abuse follows **Legal-approved** script; partial reversal amounts rounded per Finance policy. | Accounts, wallet, or points | Compliance / Legal Representative | None without Legal ticket | CS uses only approved templates. |
| BR-014 | **Campaign pause:** if **TBD** orders flagged in **TBD** hours for same code, or Finance breach signal, Growth must **pause or cap** within **TBD** hours or escalate to Executive Sponsor. | Live campaigns | Marketing / Growth Manager | Sponsor waiver with written risk accept | Kill-switch FR must support audit. |
| BR-015 | **Legal and privacy checks** before turning on new signals that use **sensitive** attributes; Legal maintains approved attribute list. | Detection models | Compliance / Legal Representative | None | Fair lending and marketing law context for Northline Market regions. |
| BR-016 | **Audit logging:** any change to BR thresholds, stack policy flags, kill-switch, or manual payout override writes an **append-only** audit record with user, time, old and new values. | Admin and config tools | Engineering Lead | Break-glass account per Security policy | Retention per NFR. |
| BR-017 | **Role-based override:** policy exceptions (credits, manual completion) require **requester + approver** roles, reason code, and optional expiry; approver cannot be the same person as requester. | CS and Growth tools | Customer Support Manager | None for same-person approval | Mapped to FR-016. |
| BR-018 | **Reporting definitions:** “suspected leakage $” equals **sum of promo discount dollars** on orders meeting **flag set vTBD** minus orders marked false positive in period; Finance publishes denominator exclusions (cancelled, test). | Dashboards and exports | Finance Manager | Board pack may use alternate view if footnoted | Version flag definitions when they change. |

---

## Open items (fill in workshop, not in table)

- Replace every **TBD** (percent, day count, velocity threshold, risk tier) with numbers Northline Market sponsors agree.
- Confirm whether **void** language for referral is allowed in all regions Northline Market sells into.
- Add **marketplace** orders to BR scope or explicitly exclude in BR-018 footnotes.
