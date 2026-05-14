# Business Rules — Promotions & Referrals (Draft)

**Status:** Placeholder for workshop consolidation. **Do not treat as legally binding** until Legal and Growth sign.

## Rule catalog (initial stubs)

| Rule ID | Name | Rule (draft wording) | Owner | Exceptions |
|---------|------|---------------------|-------|---------------------|
| BR-01 | One first-time discount per person | First-time buyer promotion may be used once per verified customer identity | Growth | Manual goodwill via CS with cap |
| BR-02 | Stacking policy | Unless campaign explicitly allows stack, customer may not combine more than **TBD** promotions on same order | Growth | Emergency campaign flag |
| BR-03 | Category floor margin | Orders where promo discount drives **margin below X%** on excluded categories require review flag | Finance + Merch | Seasonal list updates |
| BR-04 | Referral genuine purchase | Referral credit pays out only after referee order **ships** or passes **TBD** fraud checks | Growth | Fraud lead approval |
| BR-05 | Self-referral prohibition | Accounts with shared payment instrument, address hash, or **TBD** link cannot refer each other | Fraud / Legal | Documented investigation |
| BR-06 | Velocity | More than **TBD** new accounts per device per rolling 30 days → review flag | Fraud | False positive workflow |

## Definitions (to refine)

- **Customer identity:** business definition tying accounts together — pending technical mapping.
- **Suspected abuse:** policy deviation or statistical anomaly pending human confirmation.
- **Confirmed abuse:** investigator marks case with evidence per internal standard.

## When two rules disagree

Published customer terms win on anything customer-facing. Internal-only conflicts go to the sponsor; log what changed and who approved it.

## Traceability

Each BR-* should map to FRs and test themes in the RTM when populated.

## Open items

- Exact margin floor X% by category.
- Whether employee and B2B accounts follow separate BR set.
