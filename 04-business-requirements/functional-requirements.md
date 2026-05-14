# Functional Requirements

**Project:** PromoLeak Radar  
**Format:** Each item has a stable ID for traceability (prefix FR).

## Reporting & analytics

| ID | Requirement | Rationale | Priority |
|----|---------------|-----------|----------|
| FR-01 | System shall calculate and display daily and weekly totals of **suspected abusive orders** using agreed definitions (see business rules). | Operations needs a pulse, not only month-end | Must |
| FR-02 | User shall filter dashboard views by **campaign**, **coupon code**, **category**, and **channel** (as data allows). | Leakage is not uniform | Must |
| FR-03 | User shall drill from aggregate metrics to **order-level list** for investigation (subject to permissions). | Analysts verify before action | Must |
| FR-04 | System shall show **referral** metrics separately from cart coupons (payout vs. discount). | Different economics and rules | Should |

## Detection & scoring (business-facing)

| ID | Requirement | Rationale | Priority |
|----|-------------|-----------|----------|
| FR-10 | System shall support configurable **thresholds** (e.g., discount % on order, count of accounts per device fingerprint if available) with owner and effective date. | Tuning without redeploy | Should |
| FR-11 | System shall attach **reason codes** to flagged orders (multi-select allowed). | CS and audit explainability | Must |
| FR-12 | System shall allow **false positive** marking and capture short reason. | Model/process improvement | Should |

## Workflow

| ID | Requirement | Rationale | Priority |
|----|-------------|-----------|----------|
| FR-20 | Investigator role shall change case status: New → In review → Confirmed abuse / False positive → Closed. | Clear pipeline | Must |
| FR-21 | System shall log status changes with user ID and timestamp. | Audit | Must |
| FR-22 | System shall support **assignment** of cases to a named investigator (or pool). | Workload management | Should |

## Rules & configuration (read from business rules doc)

| ID | Requirement | Rationale | Priority |
|----|-------------|-----------|----------|
| FR-30 | Authorized role shall **disable** or **cap** a coupon campaign with immediate effect where technically supported, with rollback note. | Stop bleeding | Must |
| FR-31 | System shall prevent or warn on **stacking** combinations that violate published policy (exact behavior TBD with engineering). | Close known gap | Must |

## Integrations (functional expectation level)

| ID | Requirement | Rationale | Priority |
|----|-------------|-----------|----------|
| FR-40 | Solution shall ingest **order**, **line item**, **payment**, and **promo application** facts from source systems per data map. | Single picture | Must |
| FR-41 | Optional: push **case outcome** back to CRM or CS tool for agent visibility. | Fewer repeat contacts | Could |

## Defer / parking lot

- Real-time scoring at click-time vs. batch — decision pending architecture.
- Partner marketplace orders if different contract terms.
