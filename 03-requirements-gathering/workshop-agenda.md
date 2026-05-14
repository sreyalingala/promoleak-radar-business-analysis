# Workshop Agenda: Future-State Promotion Abuse Detection & Review (90 minutes)

**Organization:** Northline Market  
**Project:** PromoLeak Radar  
**Workshop type:** Requirements workshop (cross-functional)  
**Duration:** 90 minutes, **hard stop** at 90 unless sponsor extends same day.

---

## Workshop objective

Draft a **shared future-state** for how Northline Market will **detect** suspected promotion abuse (duplicate accounts, first-time coupon reuse, referral misuse, stacking, low-margin discount issues), **triage** it, **decide** (false positive vs. action), and **communicate** internally so CS and Growth aren't working from different playbooks. Leave with **owners**, **top gaps**, and **decisions** (or explicit escalations) documented, not a finished BRD.

---

## Participants (target)

| Role | Count | Notes |
|------|-------|--------|
| Marketing / Growth Manager | 1 | Policy and campaign intent |
| Finance Manager | 1 | Margin / metric ownership |
| Fraud / Risk Analyst | 1 | Detection and evidence |
| Product Manager | 1 | Product and workflow touchpoints |
| Engineering Lead | 1 | Feasibility, events, timing |
| Data Analyst | 1 | Reporting and definitions |
| Customer Support Manager | 1 | Agent reality |
| Compliance / Legal Representative | 1 optional | If referral clawback or customer messaging on the table |
| Operations Manager | 1 optional | If Northline runs central campaign monitoring |
| **Facilitator** | BA | Timeboxing, parking lot |
| **Executive Sponsor** | 0 in room | Send outcomes same day; pull in if deadlock |

If Legal cannot attend, **park** customer-facing enforcement topics and schedule a 30-minute legal follow-up.

---

## Pre-work (send 48 hours ahead)

- Latest **problem statement** (1-2 pages) for PromoLeak Radar.  
- **Draft as-is** pain bullets from interviews (Finance, Growth, CS, Fraud).  
- One **anonymized** example each (if allowed): bad stacking outcome; referral loop; duplicate first-time use, or clear "we can't share examples yet" from Legal.  
- Blank **future-state swimlane** template (Miro / slide) for live fill-in.  
- Ask Growth to bring **current stacking / first-time / referral policy** links or PDFs.

---

## Time-boxed agenda

| Time | Length | Topic | Discussion focus | Expected output |
|------|--------|-------|------------------|-----------------|
| 0:00 | 5 min | Welcome & objective | Why this workshop; rules of engagement | Aligned expectations |
| 0:05 | 10 min | **As-is recap**, detection & review today | Where signals come from today; who acts; where it breaks | Agreed "current pain" list on the board |
| 0:15 | 15 min | **Triggering detection** | What should create a flag or case (rules, thresholds, data feeds) | Draft list of trigger types + "needs data" tags |
| 0:30 | 15 min | **Triage & ownership** | Who owns queue, assignment, SLA, weekend coverage | Named role owners (or "TBD + deadline") |
| 0:45 | 10 min | **Decision outcomes** | False positive, warn customer, cap code, restrict account, escalate Legal | Draft outcome types + who approves each |
| 0:55 | 10 min | **Handoffs** | CS visibility; Growth notification when code capped; Finance sign-off on metrics | Handoff arrows on swimlane |
| 1:05 | 10 min | **Dashboard / ops cadence** | What Finance and Ops need daily/weekly vs. ad hoc | MVP dashboard themes (not pixel design) |
| 1:15 | 10 min | **Decisions, parking lot, actions** | Confirm decisions; park out-of-time items | Action list with owner + due date |
| 1:25 | 5 min | **Close** | Next meeting(s); doc updates | Photo / export of board + note to sponsor |

---

## Discussion topics (prompts for the facilitator)

- Should **first-time abuse** and **referral abuse** live in **one queue** or two at Northline Market?  
- Who can **kill or cap** a code without a dev emergency, and within what time target?  
- What is **explicitly manual** in v1 (e.g., all investigations human) vs. aspirational later?  
- What do we **not** try to detect in v1 to avoid alert fatigue?

---

## Decisions expected (minimum)

By end of session, the group should either **decide** or **escalate with owner**:

1. **Primary owner** of the investigation queue (role name).  
2. **Whether** Finance, Fraud, or joint sign-off approves economic thresholds for auto-flagging (if any).  
3. **Whether** v1 is **batch/daily** detection only vs. any near-real-time requirement, Engineering to confirm feasibility after workshop.  
4. **CS visibility** minimum: what disposition fields agents must see in a first release.  
5. **Top 3** trigger themes for MVP (e.g., stacking over cap on excluded categories, referral payout anomaly, duplicate first-time pattern).

---

## Parking lot (capture, don't derail)

- Vendor fraud tools, ML scoring, identity vendor upgrades.  
- Full **marketplace** channel scope if data isn't ready.  
- Exact **legal wording** for clawbacks, Legal follow-up if not in room.  
- International **policy** differences if Northline Market sells cross-border.

---

## Follow-up actions (template)

Capture in the meeting notes:

| Action | Owner | Due |
|--------|-------|-----|
| *Example:* Draft future-state swimlane into `05-process-modeling/to-be-process.md` | BA | +3 business days |
| *Example:* Data feasibility note on referral + order join | Data Analyst + Eng Lead | +1 week |

Send **same-day summary** to participants and sponsor: decisions, parking lot, actions.
