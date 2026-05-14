# Data Requirements: PromoLeak Radar (Northline Market)

**Project:** PromoLeak Radar  
**Audience:** Business Analysts, Product, Finance, Fraud / Risk, Data owners, Compliance / Legal  
**Intent:** Describe entities the business needs to measure, flag, review, and audit. Physical models and pipelines sit with Data Engineering; this is the agreement layer for what exists, who owns it, and what can go wrong.

---

## Entity catalog

### Customer

| Field | Detail |
|-------|--------|
| **Entity name** | Customer |
| **Purpose** | Stable commercial identity for loyalty, marketing consent, and Finance rollups (may differ from login account). |
| **Key fields** | Customer id, created date, region or market, status, segment tags (if used), link to primary account id. |
| **Source system** | Customer Account Service or CRM master (Northline standard). |
| **Data owner** | Marketing / Growth Manager (segment definitions), Finance Manager (reporting rollups). |
| **Refresh need** | Near daily for dashboards; near real-time only if checkout enforcement reads this entity (often owned by another service in early pilots). |
| **Notes / quality** | The word "customer" must match BR-001 language or exceptions are documented. Household vs account splits cause false positives if not defined. |

### Account

| Field | Detail |
|-------|--------|
| **Entity name** | Account |
| **Purpose** | Login and order identity used for duplicate signals, referral roles, and queue assignment. |
| **Key fields** | Account id, created date, status, email hash or token (policy), phone token, last login, device id last seen (if allowed). |
| **Source system** | Customer Account Service. |
| **Data owner** | Engineering Lead (technical integrity), Fraud / Risk Analyst (signal use). |
| **Refresh need** | Near real-time for fraud signals; daily snapshot acceptable for historical dashboards if documented. |
| **Notes / quality** | Guest checkout and merged accounts need explicit rules. Shared devices (dorms, families) drive false positives (BR-008). |

### Order

| Field | Detail |
|-------|--------|
| **Entity name** | Order |
| **Purpose** | Header for promo applications, payments, margin checks, referral milestones, and queue facts. |
| **Key fields** | Order id, timestamps, channel, currency, customer id, account id, status (placed, paid, shipped, cancelled, refunded), policy version ids for stack and promos. |
| **Source system** | Northline Market E-commerce Platform and Order Management System. |
| **Data owner** | Operations Manager (status truth), Finance Manager (revenue recognition alignment). |
| **Refresh need** | Near real-time for kill-switch and alerts; nightly acceptable for historical leakage if Finance agrees lag. |
| **Notes / quality** | Partial refunds and split shipments complicate promo and referral allocation (BR-012). Test orders must be tagged and excluded per BR-018. |

### Order Item

| Field | Detail |
|-------|--------|
| **Entity name** | Order Item |
| **Purpose** | Line-level economics for margin floor checks and category rollups. |
| **Key fields** | Order line id, order id, sku, qty, list price, sell price, discount allocated, category id, COGS or margin flag (trusted or unknown). |
| **Source system** | Order Management System plus pricing snapshot from Product Catalog. |
| **Data owner** | Finance Manager (COGS trust), Merchandising (category mapping). |
| **Refresh need** | Same as order header for v1 reporting. |
| **Notes / quality** | If COGS missing, FR-005 path is "margin unknown," not silent zero (FR-005, BR-006). |

### Product

| Field | Detail |
|-------|--------|
| **Entity name** | Product |
| **Purpose** | SKU attributes, category, and exclusion lists for low-margin logic. |
| **Key fields** | Sku, title, category hierarchy, margin class, active flag, replacement sku if superseded. |
| **Source system** | Product Catalog. |
| **Data owner** | Merchandising lead (business), Engineering Lead (feed). |
| **Refresh need** | Daily minimum; faster if promos target new SKUs mid-week. |
| **Notes / quality** | Category drift breaks historical comparisons unless versioned. |

### Coupon

| Field | Detail |
|-------|--------|
| **Entity name** | Coupon |
| **Purpose** | Code-level configuration for stack groups, caps, audience, dates, and kill-switch state. |
| **Key fields** | Coupon or code id, human code string, campaign id, stack policy id, discount type, max redemptions, effective window, disabled flag, approver ids (BR-010 linkage if captured). |
| **Source system** | Promotion Engine (authoring), mirrored to Data Warehouse. |
| **Data owner** | Marketing / Growth Manager. |
| **Refresh need** | Near real-time for enforcement and FR-017; warehouse may lag with visible freshness chip. |
| **Notes / quality** | Manual hotfixes in spreadsheets do not belong in metrics; Growth must publish in the engine or metrics lie. |

### Campaign

| Field | Detail |
|-------|--------|
| **Entity name** | Campaign |
| **Purpose** | Parent object for Finance and Growth to align spend, leakage, and ROI. |
| **Key fields** | Campaign id, name, owner, budget, start and end, channel targets, referral flag yes or no. |
| **Source system** | Promotion Engine or marketing planning tool (Northline standard). |
| **Data owner** | Marketing / Growth Manager. |
| **Refresh need** | Daily for reporting; near real-time for alerts tied to campaign id (FR-018). |
| **Notes / quality** | Orphan codes without a campaign break executive rollups unless Finance assigns a default bucket. |

### Referral

| Field | Detail |
|-------|--------|
| **Entity name** | Referral |
| **Purpose** | Events for invite, acceptance, milestone, payout, hold, void, and refund netting. |
| **Key fields** | Referral id, referrer account id, referee account id, timestamps, milestone status, payout amount, hold reason, reversal id. |
| **Source system** | Referral Service. |
| **Data owner** | Marketing / Growth Manager (program rules), Finance Manager (payout truth). |
| **Refresh need** | Hourly or better if referral jobs are async; show separate freshness if lagging cart data. |
| **Notes / quality** | Closed-loop and self-referral detection spans services; reconcile ids with Account (BR-003, BR-004, BR-012). |

### Payment

| Field | Detail |
|-------|--------|
| **Entity name** | Payment |
| **Purpose** | Duplicate account signal via token or hash (BR-007) and tender context for investigations. |
| **Key fields** | Payment id, order id, method family, token or hash surrogate, auth and capture timestamps, outcome. |
| **Source system** | Payment System. |
| **Data owner** | Engineering Lead (PCI scope), Fraud / Risk Analyst (use policy). |
| **Refresh need** | Near real-time for duplicate checks at order capture; masked fields only in investigator UI (NFR-003). |
| **Notes / quality** | If hash is unavailable, UI must say so (US-002), not imply "all clear." |

### Device

| Field | Detail |
|-------|--------|
| **Entity name** | Device |
| **Purpose** | Velocity and duplicate graph edges (BR-008). |
| **Key fields** | Device id surrogate, first seen, last seen, account ids observed (aggregated), confidence score if modeled. |
| **Source system** | E-commerce Platform session telemetry (subject to Legal approval, BR-015). |
| **Data owner** | Fraud / Risk Analyst (thresholds), Compliance / Legal Representative (attribute approval). |
| **Refresh need** | Near real-time for creation bursts; daily for dashboards. |
| **Notes / quality** | Shared devices cause false positives; allowlist process must exist before hard actions. |

### Shipping Address

| Field | Detail |
|-------|--------|
| **Entity name** | Shipping Address |
| **Purpose** | Hash-based duplicate detection (BR-009) and CS context for investigations. |
| **Key fields** | Address hash, normalized components (policy), order id link, gift flag if captured. |
| **Source system** | Order Management System or checkout address capture. |
| **Data owner** | Fraud / Risk Analyst (matching rules), Compliance / Legal Representative (retention and display). |
| **Refresh need** | Same as order. |
| **Notes / quality** | Gift sends and corporate ship-tos need allowlist handling; high false positive risk if thresholds are aggressive. |

### Return

| Field | Detail |
|-------|--------|
| **Entity name** | Return |
| **Purpose** | Refund timing for referral netting and leakage adjustments (BR-012). |
| **Key fields** | Return id, order id, line ids, refund amount, refund timestamp, reason code. |
| **Source system** | Order Management System or returns portal. |
| **Data owner** | Finance Manager. |
| **Refresh need** | Daily minimum; faster if referral reversals are near real-time. |
| **Notes / quality** | Partial returns need a clear allocation rule to promo dollars or Finance will not sign NFR-010. |

### Manual Review Case

| Field | Detail |
|-------|--------|
| **Entity name** | Manual Review Case |
| **Purpose** | Workflow object for queue, assignment, SLA, and disposition (FR-008 to FR-011). |
| **Key fields** | Case id, order id(s), status, assignee, pool, opened time, due time, breach flag, disposition code, notes, links to exception id if any. |
| **Source system** | Manual Review Queue (PromoLeak module or Northline case tool). |
| **Data owner** | Operations Manager (SLA), Fraud / Risk Analyst (outcomes). |
| **Refresh need** | Near real-time for operations; audit export on demand (FR-012, FR-014). |
| **Notes / quality** | Pipeline failures must not silently drop cases (FR-008); stale banner on read models. |

### Promotion Decision

| Field | Detail |
|-------|--------|
| **Entity name** | Promotion Decision |
| **Purpose** | Captures allow, warn, or block outcomes at capture plus stack evaluation detail (FR-003). |
| **Key fields** | Decision id, order id, timestamp, policy version id, outcome, reason codes, applied codes in sequence. |
| **Source system** | Promotion Engine at checkout, persisted on order in OMS. |
| **Data owner** | Marketing / Growth Manager (policy), Engineering Lead (persistence). |
| **Refresh need** | Same as order. |
| **Notes / quality** | Without policy version id, audits and disputes are weak (FR-003 acceptance notes). |

### Audit Log

| Field | Detail |
|-------|--------|
| **Entity name** | Audit Log |
| **Purpose** | Append-style history for thresholds, kill-switch, case changes, exports (FR-012, BR-016, NFR-005). |
| **Key fields** | Event id, actor, timestamp, object type, old value, new value, correlation id. |
| **Source system** | PromoLeak Radar Rules and Risk Scoring Layer and Manual Review Queue. |
| **Data owner** | Compliance / Legal Representative (retention), Engineering Lead (implementation). |
| **Refresh need** | Real-time append; reporting near real-time. |
| **Notes / quality** | Retention and legal hold path per NFR-008; export of audit itself must be logged. |

---

## Data quality checks (business-facing)

| Check | Why it matters |
|-------|----------------|
| Order status and refund state align before leakage close | Stops overstating leakage on cancelled or refunded orders (BR-018). |
| Policy version id present on orders with promos | Supports FR-003 and audit story. |
| COGS coverage report by category | Explains "margin unknown" volume (FR-005). |
| Referral milestone completeness | Missing milestones inflate false referral abuse (BR-003). |
| Duplicate signal null rate | PCI or feed gaps must surface in UI, not as zeros (US-002). |
| Queue case orphan rate | Detects silent pipeline drops (FR-008). |

---

## Data privacy considerations

- Investigator views use masking and least privilege (NFR-003, NFR-011, FR-015). Legal publishes which columns appear in exports (FR-014).
- New signals on device or address need Legal sign-off before production enablement (BR-015).
- Retention and purge for cases and exports follow NFR-008; legal hold stops purge without a ticket owner.

---

## Reporting definition notes

- **Suspected leakage dollars** and exclusions follow BR-018; Finance publishes denominator rules for cancelled, test, and marketplace (if excluded).
- When definitions change, dashboards show version id and effective time (US-022, NFR-010).
- Marketing-facing ROI must footnote any delta from Finance leakage proxy (US-013).

---

## Open data questions

- Marketplace partner promo detail: full feed or explicit exclusion (BRD parking lot).
- Backfill depth for referral and payment hashes for trend charts.
- Single customer id across brands if Northline adds brands later.
