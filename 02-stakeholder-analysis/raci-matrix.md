# RACI Matrix — PromoLeak Radar (MVP phase)

**Legend:** R = Responsible, A = Accountable, C = Consulted, I = Informed  
**Note:** This is a first cut for analysis and delivery coordination. Engineering may split R further by system.

| Activity / deliverable | Finance | Growth / Promos | Product | Engineering | Data/BI | CS | Legal | Fraud |
|------------------------|---------|------------------|---------|-------------|---------|----|----|-------|
| Problem statement sign-off | A | C | C | I | I | I | I | C |
| Business case numbers | R | C | I | I | C | I | I | C |
| Elicitation workshops | C | R | R | C | R | R | I | R |
| BRD / FRD inputs | C | A | R | C | C | C | C | C |
| Business rules (promo eligibility) | C | A | R | C | I | C | C | C |
| As-is / To-be process | I | R | R | C | I | R | I | R |
| Dashboard requirements | C | C | R | I | R | C | I | C |
| Data definitions / lineage | C | I | C | C | A | I | I | C |
| UAT plan | C | C | A | C | I | R | C | C |
| UAT execution | I | C | C | R | I | R | I | R |
| Go-live comms to customers | I | C | C | I | I | R | A | I |
| Post-go KPI review | A | R | I | I | R | I | I | C |

## Gaps

- Single **Accountable** owner for end-to-end “PromoLeak” product might be missing — recommend naming one PO after charter approval.
- If Engineering is outsourced, RACI columns need vendor PM added.
