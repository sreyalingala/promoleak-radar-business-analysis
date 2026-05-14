# PromoLeak Radar: Business Analysis for Promotion Abuse & Revenue Leakage Detection

Documentation-only portfolio case study for a mid-sized e-commerce retailer (**Northline Market**, fictional name). The scenario is promotion abuse and revenue leakage: stacked coupons, duplicate accounts, referral gaming, and discounts applied where margin cannot support them. The repo is written the way a BA would hand off early discovery: clear structure, real artifact types, and honest TBDs where workshops or FP&A would still supply names, dates, and numbers.

---

## 1. Short project summary

PromoLeak Radar is a full BA documentation set for scoping how the business would **detect**, **measure**, and **respond** to promotional leakage before committing to a specific product build or vendor. It covers stakeholders, elicitation, a BRD slice, functional and non-functional requirements, business rules, as-is/to-be process and escalation, user stories, traceability to tests, dashboard and data needs, UAT planning, and a KPI / cost–benefit frame for the sponsor.

---

## 2. Business problem

- **Leakage:** Customers (and sometimes coordinated groups) exploit first-time offers, referral credits, and stackable codes beyond what policy intended.
- **Margin:** High effective discounts land on low-margin SKUs or categories merchandising never meant to deep-discount.
- **Operations:** Finance often sees the pain at month-end; Growth and customer service end up in reactive disputes without agreed metrics or escalation when a campaign misbehaves.

---

## 3. Why this project matters

Promotion economics sit between **Growth** (conversion, acquisition) and **Finance** (margin, forecast). Without shared definitions, reporting, and rules of engagement, teams debate different spreadsheets while leakage continues. This work matters because it shows how a BA **narrows the problem**, **documents requirements and rules**, **models handoffs and escalation**, and **connects delivery to acceptance and KPIs**, so engineering and leadership can decide what to build with less rework and fewer “we didn’t know that was in scope” moments.

---

## 4. Project objectives

1. **Scope and sponsor alignment**, Charter-level in/out scope and who decides policy vs. technical trade-offs.
2. **Requirements fit for sizing**, BRD, FRs, NFRs, and draft business rules written so delivery can estimate effort and dependencies.
3. **Process clarity**, As-is pain points, to-be operating model, and escalation when abuse or misconfiguration spikes.
4. **Solution-facing specs (BA-owned)**, Dashboard requirements, data entity view, system context; no production code in this repo.
5. **Quality path**, UAT plan, sample test cases, defect fields; traceability from needs to test themes.
6. **Impact framing**, KPI set, cost–benefit skeleton, and a short sponsor recommendation tied to those metrics.

---

## 5. Business Analyst skills demonstrated

This project is intentionally documentation-heavy. It demonstrates:

| Skill area | Where it shows up in the repo |
|------------|-------------------------------|
| **Stakeholder analysis** | `02-stakeholder-analysis/`, register, RACI, communication plan |
| **Requirements gathering** | `03-requirements-gathering/`, elicitation plan, interview questions, workshop agenda, assumptions / constraints / risks |
| **BRD creation** | `04-business-requirements/business-requirements-document.md` |
| **Functional and non-functional requirements** | `04-business-requirements/functional-requirements.md`, `non-functional-requirements.md` |
| **Business rules** | `04-business-requirements/business-rules.md` |
| **Process modeling** | `05-process-modeling/`, as-is, to-be, escalation workflow |
| **User stories and acceptance criteria** | `06-user-stories/`, backlog themes, stories with Given/When/Then style acceptance |
| **Requirements traceability** | `07-traceability/requirements-traceability-matrix.md` |
| **Dashboard requirements** | `08-solution-design/dashboard-requirements.md`, `dashboard-wireframe.md` |
| **UAT planning** | `09-testing-uat/`, UAT plan, test cases, defect log template |
| **KPI framework** | `10-business-impact/kpi-framework.md` |
| **Business impact analysis** | `10-business-impact/cost-benefit-analysis.md`, `final-recommendation.md` |

Supporting context: project charter, business case, and problem statement in `01-project-overview/`; data requirements and system context in `08-solution-design/`.

---

## 6. Key deliverables

- **Overview:** Project charter, business case, problem statement  
- **People & governance:** Stakeholder register, RACI matrix, communication plan  
- **Discovery:** Elicitation plan, interview bank, workshop agenda, logged assumptions/constraints/risks  
- **Requirements:** BRD, FR/NFR catalogs, draft business rules with open items called out  
- **Process:** Current-state narrative, target operating model, escalation levels  
- **Agile-facing inputs:** Product backlog themes, user stories with acceptance criteria  
- **Traceability:** RTM linking business needs to requirements and sample test IDs  
- **Solution design (BA view):** Dashboard specs, text wireframe, data requirements, system context diagram (Mermaid in markdown)  
- **Testing:** UAT plan, representative test cases, defect log field template  
- **Impact:** KPI framework, CBA working paper, draft final recommendation for sponsor review  

---

## 7. Repository structure

| Folder | Contents |
|--------|----------|
| `01-project-overview/` | Charter, business case, problem statement |
| `02-stakeholder-analysis/` | Stakeholder register, RACI, communication plan |
| `03-requirements-gathering/` | Elicitation plan, interview questions, workshop agenda, assumptions-constraints-risks |
| `04-business-requirements/` | BRD, functional requirements, non-functional requirements, business rules |
| `05-process-modeling/` | As-is process, to-be process, escalation workflow |
| `06-user-stories/` | Product backlog, user stories and acceptance criteria |
| `07-traceability/` | Requirements traceability matrix |
| `08-solution-design/` | Dashboard requirements, dashboard wireframe, data requirements, system context diagram |
| `09-testing-uat/` | UAT plan, test cases, defect log template |
| `10-business-impact/` | KPI framework, cost–benefit analysis, final recommendation |
| `assets/diagrams/` | Placeholder for exported diagrams (PNG/SVG) if you add them later |

---

## 8. Project workflow

A sensible read order if you want to follow how the analysis would unfold on the job:

1. **Charter & problem**, `01-project-overview/`  
2. **Who is involved and how decisions travel**, `02-stakeholder-analysis/`  
3. **How discovery would run**, `03-requirements-gathering/`  
4. **What the business asks for**, `04-business-requirements/`  
5. **How work happens today vs. target**, `05-process-modeling/`  
6. **Backlog and stories for delivery discussion**, `06-user-stories/`  
7. **Traceability for test planning**, `07-traceability/`  
8. **What reporting and data need**, `08-solution-design/`  
9. **How we’d prove it in UAT**, `09-testing-uat/`  
10. **How we’d judge success and cost**, `10-business-impact/`  

That order mirrors a common path: **frame → people → elicit → specify → process → backlog → trace → solution notes → test → impact**.

---

## 9. Expected business impact

If implemented against these requirements, the business would expect:

- **Earlier detection** of runaway campaigns and abusive patterns instead of discovering them mainly at close.  
- **Fewer cross-team arguments** over “the real number” when Finance, Growth, and ops share the same definitions and feeds.  
- **Faster containment** when stacking, eligibility, or referral rules need a cap, kill-switch, or investigation queue.  
- **Clearer customer handling** when CS has disposition context and Legal-approved language where enforcement applies.  
- **Measurable trade-offs** via the KPI framework and CBA, so margin moves can be weighed against conversion and CS load instead of one-off opinions.  

Figures in the CBA are placeholders until a real FP&A model and implementation costs are attached; the structure shows how a BA supports that conversation.

---

## 10. How to review this project

**If you have 15 minutes:** Read `01-project-overview/problem-statement.md`, skim `04-business-requirements/business-requirements-document.md`, and open `07-traceability/requirements-traceability-matrix.md` to see how needs link to tests.

**If you have 45 minutes:** Add `02-stakeholder-analysis/stakeholder-register.md`, `05-process-modeling/as-is-process.md` → `to-be-process.md`, `06-user-stories/user-stories-acceptance-criteria.md`, and `08-solution-design/dashboard-requirements.md`.

**If you want depth:** Walk `03-requirements-gathering/` → full `04-business-requirements/` → `09-testing-uat/test-cases.md` → `10-business-impact/final-recommendation.md` to see discovery through recommendation in one pass.

**What this repo is not:** Production code, a live data pipeline, or signed legal/finance approvals. It is a **portfolio-grade BA artifact set** you can discuss in interviews: trade-offs you called out, open questions you left visible, and how you’d hand off to engineering and QA.

---

## License

See `LICENSE`. Fictional company and system labels are used where a real engagement would name actual tools and individuals.
