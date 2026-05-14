# Final Recommendation: PromoLeak Radar (Northline Market)

**Project:** PromoLeak Radar  
**Prepared for:** Executive Sponsor, Finance, Marketing / Growth, Operations, Compliance / Legal, Product  
**Document type:** Business Analyst recommendation after discovery, requirements, process modeling, solution design, traceability, and UAT planning work in this repository.

This is a **balanced** view. PromoLeak Radar is worth doing in phases because Northline Market already loses money and credibility on promotion leakage, but the numbers are sensitive to execution and data quality. The cost-benefit paper in `cost-benefit-analysis.md` uses **fictional** mid-sized figures and shows that a narrow ROI-only read can look weak unless benefits land in the upper band or costs stay tight.

---

## Executive summary

Northline Market mixes real abuse with **config mistakes and unclear ownership** when promos go live. Finance cannot defend margin questions from one agreed definition. Growth and Fraud work from different exports. Customer Support patches goodwill cases when enforcement is inconsistent.

The work in **01** through **09** of this case study supports a **PromoLeak Radar** program: shared definitions (BR-018, FR-006, US-012, US-022), detection and stacking controls (FR-001 through FR-005), referral and refund awareness (FR-004, BR-012), a **manual review queue** with disposition and audit (FR-008 through FR-012), role-based access and exports (FR-014, FR-015, NFR-003, NFR-011), and operational response tools such as **kill-switch and alerts** (FR-017, FR-018, BR-014).

**Recommendation:** Approve a **four-phase** implementation with a **12-month benefits checkpoint**. Do not treat PromoLeak as a finished product until Finance tie-out (NFR-010) passes on a locked definition version and the business accepts the false positive cost of running the queue.

---

## What was found

From `01-project-overview/business-case.md` and `02-stakeholder-analysis/`, the same themes repeat:

- **Duplicate accounts** and **first-time coupon reuse** harvest welcome economics.  
- **Referral misuse** ( self-referral, closed loops, refunds after payout ) drains acquisition budget.  
- **Coupon stacking** and **high discounts on low-margin SKUs** show up in margin variance and incident reviews, not only in "bad actor" narratives.

From `05-process-modeling/`, the **as-is** path leaves escalation and containment uneven when a code runs hot. The **to-be** path depends on one queue, structured outcomes, and audit so CS and Finance see the same story.

From `04-business-requirements/` and `06-user-stories/`, requirements are documented to **FR-018**, **NFR-012**, and **BR-018**, with gaps called out ( example: **BR-010** second approver on publish is not yet backed by a user story in `06-user-stories/` ).

From `09-testing-uat/`, UAT is definable with **TC-001 through TC-032**, but success still needs synthetic data, Legal template readiness, and sponsor patience during threshold tuning.

---

## Recommended solution

Implement **PromoLeak Radar** as a Northline-owned layer on the existing stack ( see `08-solution-design/system-context-diagram.md` ): warehouse-fed reporting, a rules and risk scoring pass aligned to FR-001 through FR-007, a **manual review queue** for triage and disposition (FR-008 through FR-011), dashboards described in `08-solution-design/dashboard-requirements.md`, and governance hooks ( audit FR-012, exceptions FR-016, kill-switch FR-017, alerts FR-018).

This is **practical** because it reuses systems Northline already pays for ( e-commerce, OMS, promo engine, referral, payments, catalog, warehouse, SSO ) instead of leading with a heavy vendor fraud suite before Northline knows which signals pay off locally.

---

## Why this approach is practical

- **One definition** under BR-018 stops the monthly argument about what "leakage" means.  
- **Queue plus disposition** ( FR-011 ) gives Finance and CS a defensible record without every case living in a side channel.  
- **Kill-switch and spike alerts** ( FR-017, FR-018 ) address the real pain of weekend bleed called out in BR-014.  
- **UAT pack** ( `09-testing-uat/` ) gives a path to prove usability ( NFR-006 ) and access denial ( NFR-011 ) before wide rollout.

Tradeoffs are explicit: device and address signals need tuning and Legal sign-off on sensitive attributes ( BR-015, NFR-012 ). Marketplace data may stay out of headline KPIs until feeds improve.

---

## Suggested implementation phases

### Phase 1: Reporting and definitions

**Goal:** Finance and Growth read the same campaign and leakage numbers with a versioned footnote ( BR-018, US-022, FR-006, FR-013 ).

**Deliverables:** Mart design aligned to `08-solution-design/data-requirements.md`, executive and campaign views per dashboard requirements, initial KPI catalog in `kpi-framework.md`, BR-018 sign-off workshop output.

**Exit check:** NFR-010 tie-out on a small sample passes or variance is documented with an owner.

---

### Phase 2: Rules and review queue pilot

**Goal:** Run detection and stacking paths on a **limited** code set or category slice with a live queue ( FR-001 through FR-005, FR-008, FR-009, FR-011, FR-012 ).

**Deliverables:** Pilot ruleset, investigator training, disposition codes, audit export smoke, referral and refund scenarios where data exists ( FR-004, BR-012 ).

**Exit check:** False positive rate and SLA breach count inside a band agreed by Ops and Fraud, or a written decision to retune before scaling.

---

### Phase 3: Dashboard and governance rollout

**Goal:** Roll dashboards to the wider Finance and Growth audience, turn on role-based exports with Legal column matrix ( FR-014, NFR-003 ), policy exception workflow if approved ( FR-016 ), kill-switch and alerts for production codes ( FR-017, FR-018 ).

**Deliverables:** Full dashboard set from `08-solution-design/dashboard-requirements.md`, exception reporting in KPI framework, campaign pause count visible to Growth leadership.

**Exit check:** NFR-012 checklist complete for any customer-visible enforcement tied to dispositions or reversals.

---

### Phase 4: Measurement and tuning

**Goal:** Operate PromoLeak as a normal control with weekly Ops and Fraud review of KPIs in `kpi-framework.md`, monthly exec readout, and threshold changes through config paths where possible ( NFR-009 ).

**Deliverables:** Threshold ownership runbook, quarterly review of BR-010 tooling gap ( second approver on publish ), refresh of cost-benefit assumptions with real Northline numbers.

**Exit check:** 12-month benefits checkpoint against the cost-benefit expected band; sponsor decides scale-up, pause, or add scope.

---

## Risks and mitigations

| Risk | Mitigation |
|------|------------|
| KPI distrust if BR-018 drifts | Single owner in Finance for definition versions; US-022 style UI footnote |
| Alert fatigue ( FR-018 ) | Start with conservative thresholds; pair alerts with BR-014 human response targets |
| Legal exposure on new signals | BR-015 gate before production; NFR-012 on any customer comms |
| Queue overload | Phase pilot scope; staffing line in operating cost; SLA realism ( FR-010 ) |
| BR-010 still missing | Track campaign pause count and publish mistakes separately; add backlog item or accept risk |

---

## Decisions needed from stakeholders

1. **Approve phased funding** with the 12-month benefits checkpoint and pre-agreed minimum benefit or pause trigger.  
2. **Name owners** for BR-018 definitions, queue SLA parameters, and kill-switch authority ( Growth plus backup on-call ).  
3. **Confirm Legal path** for referral reversal and restriction language before production tie to customer comms.  
4. **Resolve BR-010** either as in-scope with a backlog item and build, or as accepted risk with sponsor sign-off.  
5. **Marketplace** inclusion or exclusion in headline leakage for v1.

---

## Expected business impact

If Northline executes near the **expected** band in `cost-benefit-analysis.md`, mature run rate benefit on the order of **$145k per year** ( fictional ) is plausible against **$74k** annual operating cost, after the program reaches steady state. Year one stays cash negative on paper because of implementation cost and ramp.

Non-dollar impact matters for this recommendation: **faster containment** when codes misbehave, **fewer board surprises**, and **less ad hoc SQL** from Data ( see business case impact on teams ).

---

## Final recommendation

**Proceed with PromoLeak Radar in the four phases above**, funded as a **gated program**, not a silent IT project. Start with definitions and reporting so Finance and Growth stop arguing from different spreadsheets. Add the queue and rules pilot only after Phase 1 tie-out is credible. Scale dashboards, governance, and kill-switch once Legal and Ops exit criteria are met. Revisit costs and benefits at **12 months** with real Northline data and decide whether to deepen signals, add BR-010 style publish controls, or narrow scope.

If the Executive Sponsor cannot commit to **named owners** and the **BR-018** workshop, pause rather than ship tooling that will not be trusted.

---

## References in this repo ( for traceability )

- Requirements: `04-business-requirements/` ( FR-001 to FR-018, NFR-001 to NFR-012, BR-001 to BR-018 )  
- User stories: `06-user-stories/` ( US-001 to US-022 )  
- RTM and test IDs: `07-traceability/requirements-traceability-matrix.md`, `09-testing-uat/test-cases.md`  
- Solution design: `08-solution-design/`  
- UAT plan: `09-testing-uat/uat-plan.md`

---

## Change log

| Date | Author | Note |
|------|--------|------|
| 2026-05-14 | BA case study | Final balanced recommendation with phased rollout and explicit checkpoint |
