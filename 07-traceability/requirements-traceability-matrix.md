# Requirements Traceability Matrix (RTM)

**Project:** PromoLeak Radar  
Fill in solution/test IDs as build firms up. **TBD** = not mapped yet, not “forgotten.”

## Business needs → requirements → tests (skeleton)

| Business need | BRD ref | FR / NFR / BR | User story | Solution component | Test case |
|---------------|---------|---------------|------------|---------------------|-----------|
| See leakage trends | BRD business requirements | FR-006, FR-013, FR-018 | US-01 | Dashboard / mart | TC-REPORT-01 |
| Investigate orders | BRD business requirements | FR-008, FR-009, FR-011, FR-012 | US-02 | Case UI or module | TC-WF-01 |
| Stop runaway campaign | BRD business requirements | FR-017, BR-014 | US-03 | Promo admin / engine | TC-RULE-01 |
| CS sees case outcome | BRD stakeholder needs | FR-011 (optional CRM), NFR-003, NFR-011 | US-04 | CRM integration | TC-INT-01 |
| Reliable data | BRD dependencies | NFR-001, NFR-010, FR-006 feeds | US-05 | Pipeline / monitoring | TC-NFR-PIPE-01 |
| Stacking policy | Business rules | FR-003, BR-005 | PB-06 | Checkout service | TBD |
| Referral separation | Business rules | FR-004, BR-003, BR-004 | PB-08 | Referral subsystem | TBD |

## Coverage checklist (for UAT prep)

- [ ] Every **Must** FR has ≥1 test theme.
- [ ] Every business rule marked “in scope for MVP” has expected pass/fail example orders.
- [ ] Security roles have negative tests (deny paths).

## Change log

| Date | Author | Change |
|------|--------|--------|
| | | Initial matrix scaffold |
