# Problem Statement — Promotion Abuse & Revenue Leakage

## Summary

Discounts and referral credits are walking out the door in ways Growth didn’t intend—sometimes individual customers gaming the rules, sometimes bulkier patterns. Nobody has one report everyone trusts for how much money that is, which campaigns or SKUs it clusters on, or what rule changes would hurt real acquisition least. That’s the gap this analysis is trying to close.

## What we observe

- **Duplicate and synthetic accounts** used to harvest first-time buyer codes or referral bonuses.
- **Coupon stacking** or application order issues leading to effective discounts above policy caps on low-margin SKUs.
- **Referral abuse** — self-referrals, closed loops among related accounts, or payouts before real purchase behavior.
- **Operational blind spots** — promo rules live in multiple places; when something changes, finance often finds out late.

## Impact (qualitative for now)

- Margin erosion on categories where list margin was already thin.
- Time lost in disputes between Growth (“we need promos to convert”) and Finance (“this is out of policy”).
- Inconsistent customer experience when accounts are restricted without clear internal criteria.

## Scope (this document)

**In:** fuzzy abuse definitions, rules that don’t match checkout behavior, nobody owning escalation when a code runs hot.

**Out:** picking a vendor or “we need AI” before we know what we’re measuring.

## Done when (roughly)

1. Abuse categories and rule ownership written down and argued through once, not infinite relitigation.
2. Baseline + trend for whatever leakage proxy Finance signs off on (even if v1 is ugly).
3. Written path for detect → review → customer comms (Legal in the loop where needed).
4. Requirements pack good enough to compare build vs. buy without starting from a blank page.

## Out of scope (for this problem statement)

- Criminal prosecution / law-enforcement track (separate workstream if ever).
- Replacing the whole fraud stack or identity platform in one go.
- Campaign creative and marketing calendar — only touched where economics force it.
