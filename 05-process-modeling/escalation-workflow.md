# Escalation Workflow — Suspected Promotion Abuse

**Use when:** Automated flag or manual referral exceeds investigator authority, legal sensitivity spikes, or technical incident affects promo application broadly.

## Levels

| Level | Trigger examples | Who | Time expectation |
|-------|------------------|-----|------------------|
| L1 | Single order flag, routine review | Investigator on duty | Same business day |
| L2 | Pattern affecting **TBD+** orders or high-value accounts | Investigation lead + Growth delegate | Within 4 business hours |
| L3 | Possible widespread misconfiguration (double discount) | Engineering on-call + Product + Finance | Immediate page during business hours; TBD off-hours |
| L4 | Legal/reputational risk (influencer, VIP, press) | Legal + Executive sponsor | As fast as counsel available |

## Actions by level (illustrative)

- **L1:** Confirm/deny, document, close or route.
- **L2:** Pause the specific campaign if there’s a kill-switch; keep blast radius small (don’t turn off unrelated codes by accident).
- **L3:** Consider temporary hold on new referrals or global cap — **sponsor approval** if customer-visible.
- **L4:** External comms only through Legal-approved channels.

## Information to attach on escalation

- Order IDs / cohort definition  
- Screenshots or exports per data policy  
- Rule version in effect  
- Customer tenure and lifetime value (if policy allows)  

## RACI reminder

Finance owns dollar impact narrative; Growth owns campaign intent; Legal owns wording; Engineering owns technical rollback feasibility.

## Post-incident

Short write-up within ~10 business days: what broke, why we missed it, what req/test we’re adding. Doesn’t need to be a 40-slide RCA unless L3/L4.

## Open

- Exact thresholds for L2/L3.
- After-hours coverage model.
