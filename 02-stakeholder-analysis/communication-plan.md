# Communication Plan: PromoLeak Radar

**Organization:** Northline Market  
**Project:** PromoLeak Radar (promotion leakage, duplicate accounts, first-time coupon reuse, referral misuse, stacking, low-margin discount issues)  
**Audience:** Internal stakeholders only unless Legal clears external messaging.

## What we’re trying to avoid

- Finance and Growth circulating **different spreadsheets** with the same campaign names and different totals.
- Customer Support hearing about a rule change from angry customers first.
- Engineering getting verbal decisions from a workshop with **nothing written** in Confluence / email / ticket.

---

## Cadence table

| Meeting or communication type | Audience | Frequency | Purpose | Format / channel | Owner | Notes |
|-------------------------------|-----------|-----------|---------|------------------|-------|-------|
| **Discovery interviews** | Rotating SMEs (Finance, Growth, Fraud, CS, Data, Eng) | 2–3 per week during discovery burst | Pull facts on how promos break, who fixes what, what data exists | 45–60 min video or room; BA sends questions 24h ahead | BA (facilitate); PM looped on scheduling | Record only if policy allows; otherwise two note-takers on hot topics |
| **Steering / sponsor check-in** | Exec Sponsor, Finance Mgr, Growth Mgr, PM | Biweekly while active | Scope, decisions, risks, date pressure | 30 min live; pre-read 1-pager | PM or BA | Keep to decisions; park deep policy debates for working session |
| **Weekly working session** | PM, Eng Lead, Data Analyst, Fraud Analyst, Growth delegate | Weekly | Policy vs. system gaps, rule drafts, dashboard MVP scope | Whiteboard or Miro + actions list | PM chairs; BA captures | Rotate Growth vs. Finance “voice” so both show up over a month |
| **Requirements review** | PM, Eng Lead, Finance, Growth, Data | Weekly or biweekly as docs stabilize | Walk BRD/FR slices; flag feasibility and dependencies | Screen share + annotated doc | PM | Send diff or “what changed” section so people don’t reread everything |
| **KPI review** | Finance Mgr, Data Analyst, Growth Mgr, Fraud Analyst, Ops Mgr | After first dashboard draft; then as needed | Agree headline metrics, footnotes, and “good enough” definitions | Working meeting + follow-up in writing | Finance Mgr owns metric sign-off; Data runs numbers live if possible | If Growth disputes a definition, escalate to Sponsor same week |
| **Risk / Legal check-in** | Legal, Growth Mgr, Fraud Analyst, PM, CS Manager | Biweekly during rules work; ad hoc if customer-visible change | Referral clawback language, “abuse” vs policy wording, fair treatment | 30 min + email summary | Legal rep schedules | Don’t skip before stacking or referral payout changes hit UAT |
| **Data deep-dive** | Data Analyst, Eng Lead, Fraud Analyst, Finance analyst (optional) | One or two half-days early | Order/promo/referral feeds, join keys, latency | Screen share + notes to `08-solution-design/data-requirements.md` | Data Analyst leads | Bring anonymized examples only |
| **UAT planning session** | PM, CS Manager, Finance delegate, Fraud Analyst, QA (if any) | Once before UAT cycle | Scope of UAT, environments, roles, exit criteria | Workshop + written UAT plan update | PM | CS must see disposition scenarios, not only happy path |
| **Final recommendation review** | Exec Sponsor, Finance Mgr, Growth Mgr, Legal, PM | Once at analysis close | Sponsor decision on next investment phase (build/buy, pilot scope) | 45 min + written recommendation | Exec Sponsor chairs; Finance presents economics | Growth gets pre-read 48h ahead to reduce surprises |

## Async / written

| Type | Audience | Frequency | Purpose | Format | Owner |
|------|-----------|-----------|---------|--------|-------|
| **Written status (short)** | Sponsor + PM + Finance lead | Weekly during heavy discovery | What moved, what’s blocked, decisions needed | Email or wiki | BA or PM |
| **Teams / Slack channel** | Core working group | Ongoing | Quick clarifications | Chat; **decisions** copied to email or ticket same day | PM or BA |

## Escalation (comms)

- **Stacking or policy interpretation deadlocked** (Growth vs. Finance): joint 60 min; if still stuck in 5 business days → Executive Sponsor picks a pilot path or defers change with written rationale.
- **Customer-visible incident during pilot** (e.g., mass reward clawback): CS Manager notifies Legal + Growth same day; PM pulls Eng/Data into a bridge if tooling failed.

## Open points

- Where Northline Market stores the **master copy** of these docs (Confluence vs. internal wiki vs. this portfolio repo for interviews only).
