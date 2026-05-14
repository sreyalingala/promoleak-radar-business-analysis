# Requirements Traceability Matrix (RTM)

**Project:** PromoLeak Radar  
**How to use:** Fill Solution/Component and Test Case IDs as the project matures. “TBD” means not yet mapped.

## Business needs → requirements → tests (skeleton)

| Business need | BRD ref | FR / NFR / BR | User story | Solution component | Test case |
|---------------|---------|---------------|------------|---------------------|-----------|
| See leakage trends | BRD §6 capability table | FR-01, FR-02 | US-01 | Dashboard / mart | TC-REPORT-01 |
| Investigate orders | BRD §6 | FR-03, FR-11, FR-21 | US-02 | Case UI or module | TC-WF-01 |
| Stop runaway campaign | BRD §6 | FR-30, BR-02 | US-03 | Promo admin / engine | TC-RULE-01 |
| CS alignment | BRD stakeholder needs | FR-41 (optional), NFR-10 | US-04 | CRM integration | TC-INT-01 |
| Reliable data | BRD dependencies | NFR-01, NFR-60, FR-40 | US-05 | Pipeline / monitoring | TC-NFR-PIPE-01 |
| Stacking policy | Business rules | FR-31, BR-02 | PB-06 | Checkout service | TBD |
| Referral separation | Business rules | FR-04, BR-04 | PB-08 | Referral subsystem | TBD |

## Coverage checklist (for UAT prep)

- [ ] Every **Must** FR has ≥1 test theme.
- [ ] Every business rule marked “in scope for MVP” has expected pass/fail example orders.
- [ ] Security roles have negative tests (deny paths).

## Change log

| Date | Author | Change |
|------|--------|--------|
| | | Initial matrix scaffold |
