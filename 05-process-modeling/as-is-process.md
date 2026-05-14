# As-Is Process — Promotions & Leakage (Current State)

How things run today, warts included — not what we want next quarter.

## High-level flow (narrative)

1. **Campaign ideation** — Growth or category marketing proposes discounts; finance may review large spends inconsistently.
2. **Configuration** — Codes entered in promo tool and/or commerce platform; sometimes duplicated fields between systems.
3. **Customer shop** — Customer applies codes at checkout; stacking behavior depends on order of application and legacy quirks.
4. **Fulfillment & settlement** — Order completes; referral credits may trigger on capture event that does not match finance’s mental model of “real” purchase.
5. **Detection (weak)** — Finance spots margin dips during month-end close; fraud may run occasional queries; CS handles complaints ad hoc.
6. **Response** — Manual account notes, one-off credits or reversals; limited consistency; hard to audit six months later.

## Swimlane sketch (text)

```
[Customer] → browse → cart → checkout (promo engine) → payment → OMS
                ↑                                      ↓
[Growth] ---- config codes                          [Finance] month-end review
                ↑                                      ↑
[Engineering] fixes urgent bugs only                [CS] tickets / goodwill
```

## Pain points (observed / hypothesized)

- **Late signal:** Problems found weeks after campaign peak.
- **Unclear ownership:** Is bad stacking a bug, a config error, or accepted risk?
- **Tool fragmentation:** BI export doesn’t match the promo admin export; people fight over which file is “right.”
- **Customer friction:** Agents lack single case view linking orders, devices, and credits.

## What exists on paper today

Mostly email threads, one-off spreadsheets, and the monthly margin pack. CS ticket categories exist but I haven’t mapped which codes map to which tags yet (TBD).

## Known gaps in this description

- Exact systems names redacted in portfolio version; replace with real system map in internal copy.
- Timing of referral payout vs. return window — confirm with Engineering.
