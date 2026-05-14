# Data Requirements

**Project:** PromoLeak Radar  
**Goal:** List entities and fields we need for the FRs and dashboards. Real DDL lives with Data Eng; this is the “what matters to the business” view.

## Core entities

| Entity | Description | Key attributes (non-exhaustive) | Source system (placeholder) |
|--------|-------------|----------------------------------|-----------------------------|
| Order | Customer basket converted to purchase | order_id, timestamps, channel, status, customer_id | OMS / e-com |
| Order line | SKU-level economics | sku, qty, list price, net price, category, COGS if available | OMS |
| Payment | Tender and outcome | payment_id, method type (masked), auth/capture times | Payments |
| Promo application | Each discount line | code_id, type, amount, sequence, stack group | Promo engine / cart |
| Campaign / code master | Human-readable promo config | code, start/end, caps, owner, stack policy | Promo tool |
| Referral event | Invite / accept / payout | referrer_id, referee_id, milestones, payout amount | Referral service |
| Customer account | Login identity | account_id, created_at, status | Identity |
| Investigation case | Workflow object | case_id, order_ids[], status, assignee, timestamps | New or existing tool |

## Derived fields (examples)

- **Effective discount %** = total promo $ / pre-discount subtotal (define exclusions for shipping).
- **Margin after promo**, only if COGS trusted at line level; else flag “margin unknown.”
- **Linked account score**, definition owned by Fraud/Data; document assumptions.

## Data quality rules (business)

- Orders with **cancelled** or **fully refunded** state excluded from “leakage $” or counted separately, **decision TBD with Finance**.
- Partial refunds: allocate promo impact pro-rata unless finance specifies otherwise.

## Privacy

- Portfolio repo uses fictional field names; internal version links to classification (PII, sensitive).

## Open questions

- Marketplace orders: do we get full promo detail from partner feeds?
- Historical backfill depth for referral events.
