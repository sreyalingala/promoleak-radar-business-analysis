# Dashboard Wireframe (Text-First)

Rough ASCII so BI / UX have something to react to before anyone opens Figma.

## Screen: Daily Leakage Overview

```
┌─────────────────────────────────────────────────────────────────┐
│ PromoLeak Radar                    [Date ▼] [Channel ▼] [Cat ▼]│
│ Last refresh: 2026-__-__ 06:12 UTC   (sources: orders ✓ ref △) │
├─────────────────────────────────────────────────────────────────┤
│ [ Tile: Flagged orders ] [ Tile: $ at risk* ] [ Tile: vs prior ]│
│   1,204                    $87.4k est              +12%           │
├───────────────────────────────┬─────────────────────────────────┤
│ TOP CAMPAIGNS (flagged $)     │ FLAG REASON MIX (bar)            │
│ 1. SUMMER20 ........ $22k     │ duplicate_acct ████████          │
│ 2. WELCOME10 ....... $18k     │ stack_violation ████             │
│ 3. REFERRAL2X ...... $15k     │ low_margin ███                   │
│ (table continues)             │                                  │
├───────────────────────────────┴─────────────────────────────────┤
│ INVESTIGATION QUEUE        New: 42   In review: 17   SLA risk: 3 │
│ [Open queue view]                                                │
└─────────────────────────────────────────────────────────────────┘
* Footnote defining “at risk” calculation — Finance-approved text.
```

## Screen: Order Detail (Investigator)

```
┌─────────────────────────────────────────────────────────────────┐
│ Order #12345678    Status: [ In review ▼ ]   Assignee: [ ____ ] │
├─────────────────────────────────────────────────────────────────┤
│ Customer: ****1234 (masked)    Tenure: 14 days   Orders: 3      │
│ Device / geo: [masked tokens]                Referral: Yes      │
├───────────────────────────────┬─────────────────────────────────┤
│ LINE ITEMS                    │ PROMO TIMELINE                   │
│ SKU   Cat   List  Discount    │ 10:01 coupon applied SUMMER20   │
│ ...                            │ 10:02 stack attempt WELCOME10   │
│                                │ ...                              │
├───────────────────────────────┴─────────────────────────────────┤
│ REASON CODES: [x] stack_violation [x] new_acct_high_discount    │
│ Notes: [ free text ]                         [ Save ] [ Close ] │
└─────────────────────────────────────────────────────────────────┘
```

## Notes for implementation

- Masking rules per NFR-10.
- Print/export layout can be simpler; do not ship export before Legal review.

## Changelog

- v0.1 text wireframe only.
