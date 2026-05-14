# PromoLeak Radar: Business Analysis for Promotion Abuse & Revenue Leakage Detection

Documentation-first BA portfolio work. Scenario: a mid-sized e-commerce company (“Northline Commerce” as a working label) is losing margin through coupon stacking, duplicate accounts, referral gaming, and promos applied to categories that cannot carry the discount. This repo holds the artifacts you would produce while the real build is still being sized—charter, requirements, process views, dashboard needs, UAT pack, and impact framing.

## Short summary

The business needs a shared picture of *where* promotional value leaks, *what* rules and processes should change, and *what* monitoring and UAT will look like before anyone commits to a vendor or a big internal build. The materials here read like an early project folder: placeholders (TBD names, dates, thresholds) left on purpose where a real team would fill them after workshops and finance modeling.

## Business problem

- Customers and organized groups exploit first-time offers, referral credits, and stackable codes.
- Low-margin SKUs end up sold at effective discounts the category teams never approved.
- Finance sees the margin hit late; Growth and CS get pulled into reactive firefights without a single set of numbers or escalation rules.

## Project objectives

1. Frame the problem and sponsor scope so engineering is not guessing from hallway conversations.
2. Capture requirements (business, functional, non-functional, rules) with enough detail to support estimation.
3. Model as-is vs. to-be operating patterns, including escalation when a campaign or code runs out of control.
4. Define what a first dashboard and data slice must contain, plus UAT entry/exit and test themes.
5. Tie needs to KPIs and a cost–benefit view so trade-offs on conversion vs. control are explicit.

## Repository structure

| Folder | What’s inside |
|--------|----------------|
| `01-project-overview/` | Charter, business case, problem statement |
| `02-stakeholder-analysis/` | Stakeholder register, RACI, communication plan |
| `03-requirements-gathering/` | Elicitation plan, interview bank, workshop agenda, assumptions/constraints/risks |
| `04-business-requirements/` | BRD slice, functional & non-functional requirements, draft business rules |
| `05-process-modeling/` | As-is and to-be narratives, escalation workflow |
| `06-user-stories/` | Product backlog themes, user stories with acceptance criteria |
| `07-traceability/` | Requirements traceability matrix scaffold |
| `08-solution-design/` | Dashboard requirements, text wireframe, data requirements, system context (incl. mermaid) |
| `09-testing-uat/` | UAT plan, sample test cases, defect log template |
| `10-business-impact/` | KPI framework, CBA working paper, draft final recommendation |
| `assets/diagrams/` | Placeholder for exported architecture or UI diagrams |

## Business Analyst skills demonstrated

- Problem framing and charter-style scope boundaries  
- Stakeholder identification, RACI, and communication planning  
- Elicitation planning (interviews, workshops, document review)  
- BRD / FR / NFR authoring and draft business rules  
- As-is / to-be process description and escalation paths  
- User stories, backlog themes, acceptance criteria  
- Traceability from needs to tests (matrix starter)  
- Solution-oriented outputs without pretending to be a finished product: dashboard specs, data needs, context diagram  
- UAT planning, test case design, defect management structure  
- KPI and cost–benefit thinking tied back to operational reality  

## Key deliverables

- Signed-off-ready **templates** for charter, business case, and problem statement (names/dates still TBD).  
- **Stakeholder** register, RACI, and comms plan tuned to Finance vs. Growth tension.  
- **Requirements** pack: BRD, FR/NFR, business rules with explicit open items.  
- **Process** material: as-is pain points, to-be operating model, escalation levels.  
- **Backlog and stories** with Given/When/Then style acceptance where it helps.  
- **RTM** skeleton linking needs to future test IDs.  
- **Solution design** inputs: dashboard requirements, ASCII-style wireframe, data entity list, system context.  
- **UAT** plan, starter test cases, defect log field list.  
- **Impact**: KPI set with guardrails, CBA structure, sponsor-facing recommendation draft.

---

*License: see `LICENSE`. This scenario uses fictional company naming in places; swap in real system names and numbers when adapting for an employer or client.*
