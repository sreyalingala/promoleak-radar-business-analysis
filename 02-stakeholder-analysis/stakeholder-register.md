# Stakeholder Register: PromoLeak Radar

**Organization:** Northline Market (fictional mid-sized e-commerce)  
**Project:** PromoLeak Radar, promotion abuse & revenue leakage analysis  
**Maintained by:** BA  
**Review cadence:** After major workshops, org changes, or if someone's role on promos shifts.

Names below are **role titles**; swap in real Northline Market names when you formalize the project.

| ID | Stakeholder (role) | Main interest in the project | Influence | Current pain points | Information they can provide | Engagement approach | Likely concerns |
|----|--------------------|------------------------------|-----------|---------------------|------------------------------|---------------------|-----------------|
| S01 | **Executive Sponsor** | Credible story for leadership: leakage is real, bounded, and fixable without blowing up growth | High | Board asks on margin after promos; doesn't want a science project that never lands | Priorities, what "good enough" looks like for v1, who can break ties between Finance and Growth | Short pre-reads; 30-minute decision meetings; one-page summaries with explicit asks | Scope creep; dates slipping with no visible output |
| S02 | **Marketing / Growth Manager** | Hit acquisition and promo targets; keep codes simple for customers | High | Finance challenging campaigns without numbers Growth trusts; fire drills when a code misbehaves | How campaigns are built, who publishes codes, stacking intent, historical "we meant X" stories | Joint working sessions; show category-level pain before asking for broad caps | Conversion hit if rules get blunt; promo calendar pressure during peaks |
| S03 | **Finance Manager** | Margin after promotions ties to forecast; defensible leakage view | High | Month-end variance packs full of "promo mix"; hard to tie dollars to specific codes or abuse types | Category margin targets, finance definitions of revenue at risk, what would make numbers credible | Early interview + weekly check on metric definitions; review draft KPIs before wider socialization | Numbers challenged by Growth; data gaps that make any headline metric look shaky |
| S04 | **Fraud / Risk Analyst** | Repeat abuse patterns stopped or contained; audit trail when accounts are actioned | Med-High | Investigations start from CS tickets or one-off exports; no standard queue or reason codes | Examples of duplicate-account and referral loops (anonymized), velocity signals, what evidence they need | Walkthrough real cases; keep Legal in same room for enforcement language | False positives creating PR or CS blowback; tooling not keeping up with volume |
| S05 | **Product Manager** (e-commerce) | Shippable scope; checkout and promo UX stay coherent | High | Reactive fixes when promos break; unclear priority vs. feature roadmap | User journeys, backlog reality, what can ship in which release window | Story workshops; single backlog view for PromoLeak-related items | Being asked to "just add a flag" without data or policy backing |
| S06 | **Engineering Lead** | Stable systems; promo engine behavior matches written rules | High | Stacking bugs, identity edge cases, integration debt; hears conflicting asks from Growth vs. Finance | Where rules execute (cart vs. OMS vs. batch), known limitations, rough effort bands | Technical walkthrough early; written decisions after rule workshops | Hidden dependencies; freeze windows near peak season |
| S07 | **Data Analyst** (or BI lead) | Trusted extracts; fewer one-off fire drills | Medium | Everyone wants a different cut of "flagged" orders; source tables don't always agree | What exists in the warehouse, join keys, latency, known data quality holes | Data availability workshop; small MVP metric set first | Being blamed when upstream feeds are wrong or late |
| S08 | **Customer Support Manager** | Fair treatment of customers; predictable scripts when discounts change | Medium | Agents improvising credits; spikes when rewards blocked or removed | Top ticket themes, handle times, what agents wish they could see on an account | CS preview before customer-visible rule changes; sample macros for UAT | Agent morale if policy keeps shifting without training lead time |
| S09 | **Compliance / Legal Representative** | Terms and outbound comms match what Northline Market actually does | Medium | Brought in late on clawbacks or account restrictions | Review of T&Cs, referral rules, what can/can't be said to customers | Short legal checkpoint before UAT on customer-facing flows | Over-broad detection rules that look like profiling or unfair practice |
| S10 | **Operations Manager** | Day-to-day monitoring and escalation when a campaign runs hot | Medium-High | No single runbook; ops hears about problems from Finance or CS late | Who gets paged today, what manual mitigations exist, handoffs to Growth/Eng | Process mapping session; validate to-be workflow draft | Extra workload if dashboards/alerts aren't tuned and queue explodes |

## Notes

- **"Fraud" vs. "abuse":** run customer-facing wording past Legal before using "fraud" in emails or in-app copy.
- **Merchandising / category** is not in this first cut of the register; add if margin floors need a named SKU owner outside Finance.
- Update this table when Northline Market assigns **named individuals** and backup delegates.

## Change log

| Date | Change |
|------|--------|
| | Expanded register for PromoLeak Radar discovery |
