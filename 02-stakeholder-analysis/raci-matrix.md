# RACI Matrix: PromoLeak Radar

**Organization:** Northline Market  
**Legend:** **R** = Responsible (does the work) · **A** = Accountable (approves / owns outcome) · **C** = Consulted (input required) · **I** = Informed (kept in the loop)

One **A** per row where possible. Adjust if Northline Market splits accountability (e.g., co-sponsors).

| Activity | Executive Sponsor | Marketing / Growth Manager | Finance Manager | Fraud / Risk Analyst | Product Manager | Engineering Lead | Data Analyst | Customer Support Manager | Compliance / Legal | Operations Manager |
|----------|-------------------|---------------------------|-----------------|----------------------|-----------------|------------------|--------------|-------------------------|-------------------|---------------------|
| Confirm business problem | A | C | R | C | C | I | C | I | I | C |
| Review promotion policy gaps | I | A | C | C | C | I | I | I | R | C |
| Gather stakeholder requirements | I | C | C | C | A | C | C | C | I | C |
| Define abuse detection rules | I | C | A | R | C | C | C | I | C | C |
| Review data availability | I | I | C | C | C | C | A | R | I | I |
| Approve dashboard KPIs | C | C | A | C | C | I | R | I | I | C |
| Validate future-state workflow | I | C | C | C | R | C | I | C | I | A |
| Review UAT test cases | I | C | C | C | A | C | I | R | C | C |
| Approve final recommendation | A | C | R | C | C | I | I | I | C | C |

### How to read a few rows

- **Confirm business problem:** Finance pulls together the margin and promo-variance story; Sponsor signs off that the problem is worth a structured program.
- **Review promotion policy gaps:** Growth owns what was *intended* to be published; Legal helps where terms and enforcement overlap; others comment so Finance and Fraud aren’t guessing.
- **Gather stakeholder requirements:** Product Manager is accountable for a coherent backlog-facing set of inputs; the BA (not on this matrix) usually facilitates, here PM holds the **A** so one neck is visible for delivery handoff.
- **Define abuse detection rules:** Finance **A** on economic thresholds and what “material” means; Fraud **R** to draft rule themes with Eng/Data support; Growth consulted so legitimate campaigns don’t get accidentally classified as abuse.
- **Review data availability:** Data **A** on whether the warehouse can support definitions; Data **R** to document gaps; Eng consulted for source systems.
- **Approve dashboard KPIs:** Finance **A** on headline metrics that go to leadership; Data **R** on definitions and feasibility.
- **Validate future-state workflow:** Ops **A** on how monitoring and escalation will actually run day to day; Product **R** to integrate UX and tool touchpoints.
- **Review UAT test cases:** Product **A**; CS consulted because agents live the customer-facing edge cases.
- **Approve final recommendation:** Sponsor **A**; Finance **R** to co-own the economic write-up; others consulted as needed.

## Gaps / follow-ups

- If Northline Market assigns a **dedicated BA**, add a column or note “BA facilitates all rows where PM is A.”
- If Engineering is outsourced, add **vendor PM** as C or R on data and workflow rows.
