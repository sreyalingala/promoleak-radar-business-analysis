# Business Requirements Document (BRD)

**Project:** PromoLeak Radar — Promotion abuse & revenue leakage detection  
**Version:** 0.1 draft  
**Audience:** Product, Engineering, Finance, Operations

## 1. Document control

| Field | Value |
|-------|--------|
| Author | BA (portfolio) |
| Reviewers | TBD |
| Related docs | FRD slice in `functional-requirements.md`, NFRs, business rules |

## 2. Business context

Coupons, first-time offers, and referrals are core to how Northline acquires and retains customers. Finance and ops are convinced a real chunk of promo value is going to people breaking policy or hitting holes in how checkout applies rules (dup accounts, stacking weirdness, wrong categories). Growth still has to run campaigns. The ask for this BRD slice is: enough definition and monitoring intent that we can tighten things without flying blind or surprising CS.

## 3. Business objectives

1. Agree what counts as leakage / abuse for this program (written down, not hallway).
2. See volume, trend, and where it clusters — customer, SKU, campaign, channel — within whatever the data can support.
3. Give ops a way to respond (queue, alerts, rule tweaks) with an audit trail when someone asks “why did we flag this?”
4. Cut repeat abuse where we can; be explicit where we’re accepting conversion risk.

## 4. In scope

- BA pack: detection signals, dashboards, workflows, rule-change needs, traceability, UAT themes.
- Enough acceptance language that QA/UAT isn’t inventing success criteria from screenshots.

## 5. Out of scope

- Writing production code or picking a vendor here (assumptions only).
- Replacing the whole identity platform unless that gets its own initiative later.

## 6. Business capabilities required (summary)

| Capability | Description | Priority |
|------------|-------------|----------|
| Leakage visibility | Reports/dashboards on suspected abuse and margin impact | Must |
| Case handling | Queue or integration path for human review | Must |
| Rule governance | Who can publish/change codes; approval checkpoints | Should |
| Alerting | Threshold-based notifications to defined roles | Should |
| Historical audit | Explain why an order was flagged | Must |

## 7. Stakeholder needs (condensed)

- **Finance:** numbers they’ll defend in a meeting, MoM trend, drill to campaign/SKU where possible.
- **Growth:** room to tune or exempt by segment — but not without someone writing down who approved it.
- **CS:** scripts and a view of what happened when a customer pushes back on a discount or referral.
- **Engineering:** prioritized signal list and stable-ish interfaces; they’ll tell us what’s unrealistic.

## 8. When this BRD is “good enough” for sizing

Sponsor signed scope + objectives, capability table has real priorities (not everything “Must”), and open questions each have a name attached — even if the answer is still “TBD until spike.”

## 9. Open questions

- Single owner for post-live rule changes?
- Geographic or legal differences for referral clawback?
