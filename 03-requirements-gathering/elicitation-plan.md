# Elicitation Plan: PromoLeak Radar

**Organization:** Northline Market  
**Project:** PromoLeak Radar (promotion abuse & revenue leakage)  
**Owner:** BA  
**Status:** Working plan, update when sessions are scheduled and after each wave of discovery.

---

## Purpose of elicitation

Northline Market is losing money through **duplicate accounts**, **first-time coupon reuse**, **referral misuse**, **stacking**, and **deep discounts on low-margin SKUs**, mixed with plain **config mistakes** and **unclear policy ownership**. Elicitation exists so we stop guessing: we need enough fact and opinion on record to write requirements, process, and dashboard asks that Finance, Growth, Engineering, and CS can all recognize.

This phase is **not** to pick a vendor or final architecture. It is to learn how promos and referrals actually behave end-to-end, what data exists, who decides what, and what "fixed" would look like in operations.

---

## What the BA needs to learn

| Topic | Why it matters |
|-------|----------------|
| **Current promotion setup** | Where codes are created, who approves, what systems apply discounts, where rules disagree. |
| **Coupon / campaign approval** | Who can publish, who can override, what checks happen before go-live. |
| **Known abuse patterns** | What Fraud and CS already see; what Finance sees in margin variance. |
| **How leakage is measured today** | Spreadsheets, BI views, or "we don't", so we know the gap. |
| **Dashboard and reporting holes** | What's missing for daily/weekly ops vs. month-end only. |
| **Data availability & quality** | Order line, promo application, referral events, identity keys, latency. |
| **Manual review today** | Who gets a list, from where, how cases close, what gets escalated. |
| **Policy and legal constraints** | Terms, referral clawback, what we can say to customers, retention limits. |
| **Future-state detection & review** | Who flags, who triages, who can cap/kill a code, how CS learns outcome. |

---

## Stakeholder groups

| Group | Typical roles | What we need from them |
|-------|---------------|------------------------|
| **Commercial** | Marketing / Growth Manager | Campaign intent, stacking rules, approval path, pain on Finance pushback |
| **Finance** | Finance Manager, FP&A delegate | Margin definitions, variance drivers, what numbers they'll defend |
| **Risk** | Fraud / Risk Analyst | Patterns, evidence needs, false positive tolerance |
| **Product & delivery** | Product Manager, Engineering Lead | Checkout flow, promo engine limits, change windows |
| **Data** | Data Analyst / BI | Sources, joins, freshness, what's expensive to build |
| **Customer-facing** | Customer Support Manager | Tickets, credits, scripts, what agents can't see today |
| **Governance** | Compliance / Legal Representative | Terms, comms, investigation data retention |

Executive Sponsor gets **summary readouts** and decision sessions, not every interview.

---

## Elicitation methods

| Method | When we use it | Typical output |
|--------|----------------|----------------|
| **1:1 stakeholder interviews** | Early; deep dives per role | Notes, quotes, follow-up data requests |
| **Requirements workshop** | Mid-discovery; cross-functional | Decision list, future-state process sketch |
| **Promotion policy review** | With Growth + Legal | Marked-up policy doc, list of "published vs. actual" gaps |
| **Data review** | With Data + Eng + Fraud | Source map, known gaps, sample anonymized pulls |
| **Process walkthrough** | With PM + CS + Ops | As-is swimlane, exception paths |
| **Dashboard / report review** | With Finance + Data | What exists today, what's wrong with it, MVP widget list |

---

## Planned sessions (indicative)

Order shifts if calendars force it; keep **Finance + Data** early so we don't write fiction.

| # | Session | Participants | Method |
|---|---------|--------------|--------|
| 1 | Finance deep-dive | Finance Manager, FP&A optional | 1:1 interview |
| 2 | Growth / promos | Marketing / Growth Manager | 1:1 interview |
| 3 | Fraud patterns | Fraud / Risk Analyst | 1:1 interview |
| 4 | Product & checkout | Product Manager | 1:1 + short process walkthrough |
| 5 | Engineering constraints | Engineering Lead | 1:1 interview |
| 6 | Data & BI | Data Analyst | Data review |
| 7 | CS reality | Customer Support Manager | 1:1 interview |
| 8 | Legal / compliance | Compliance / Legal Representative | 1:1 + policy review slot |
| 9 | **Requirements workshop** (90 min) | Growth, Finance, Fraud, PM, Eng, Data, CS, Ops optional | Workshop |
| 10 | Promo policy read-through | Growth + Legal (+ Finance listen) | Promotion policy review |
| 11 | Existing reporting | Finance + Data | Dashboard / report review |

Ops Manager joins workshop and reporting review if Northline Market has a central ops function for campaign monitoring.

---

## Inputs needed before sessions

- One-page **problem statement** and list of **promo types in scope** (first-time, referral, sitewide %, category-specific, etc.).
- **Sample artifacts** (redacted): example order where stacking went wrong; CS ticket export summary if allowed.
- **Org chart snippet** for who approves campaigns today.
- **Interview questions** sent ~24h ahead (`interview-questions.md`) so people can pull screenshots or run a quick query.
- **Recording policy** confirmed with Legal/HR before hitting record on any call.

---

## Outputs expected after sessions

- Updated **assumptions / constraints / risks** log after each wave.
- **Interview notes** with decisions vs. open questions labeled; owners and due dates on follow-ups.
- **Workshop outputs:** future-state detection & review process (draft), parking lot list, action items.
- **Data findings** folded into `08-solution-design/data-requirements.md` (or a short addendum).
- **Policy gap list** for Legal/Growth follow-up.
- **Candidate dashboard KPIs** for Finance sign-off track.

---

## Open questions to resolve during elicitation

- Does **"one customer"** for promo limits mean account ID only, or email/device/payment linkage, and who owns that definition?
- **Referral payout trigger:** ship, deliver, first payment capture, or other, and does Finance match that timing in models?
- **Marketplace / third-party channel** orders: in scope for v1 analysis or explicitly out?
- **Kill-switch** for a code: who has authority, how fast can it propagate, and is there audit?
- **False positive cost:** how many bad flags per week can CS and Fraud absorb before the process collapses?
- **Single headline metric** Finance will stand behind for steering (even if footnoted).

---

## Risks to elicitation itself

- People downplay leakage until **anonymized examples** or Finance variance memos are in the room.
- The engineer who knows promo edge cases is **booked solid** before peak, schedule early or document "unknown until spike."
- Growth and Finance schedule separate one-on-ones and never **jointly** agree on definitions, the workshop is mandatory for that.
