# User Stories & Acceptance Criteria

**Format:** As a … I want … So that … + Given/When/Then where useful.

---

## US-01 — Finance analyst views daily leakage summary

**As a** finance analyst,  
**I want** a daily summary of orders flagged for suspected promotion abuse,  
**So that** Growth and I aren’t comparing two different exports in a conference room.

**Acceptance criteria**

- Given yesterday’s data has loaded, when I open the summary view, then I see total flagged orders, estimated discount exposure, and comparison to prior day (or last same weekday).
- Given a date I select within allowed retention, when I apply it, then metrics refresh for that date.
- Given data is incomplete, when the dashboard loads, then a visible banner states which feeds are delayed.

---

## US-02 — Investigator drills into order detail

**As an** investigator,  
**I want** to open an order from the flagged list and see applied promos, line categories, and reason codes,  
**So that** I can confirm or clear the flag with notes.

**Acceptance criteria**

- Given I have investigation role, when I click an order ID, then I see promo codes, discount amounts, and stacked sequence if available.
- Given I change case status, when I save, then the system records user, timestamp, and prior status.
- Given I lack role permission, when I attempt access, then access is denied and the attempt is logged.

---

## US-03 — Growth owner caps a runaway campaign

**As a** promotions owner,  
**I want** to reduce or disable a coupon that is exceeding safe margin,  
**So that** we stop additional loss without waiting for a dev emergency every time.

**Acceptance criteria**

- Given I have authorized role, when I set a new cap or disable flag, then new checkouts obey the change within **TBD minutes**.
- Given the change, when it applies, then an audit entry records old and new values.
- Given I am not authorized, when I try the action, then I see a denial and suggested contact.

---

## US-04 — CS agent sees disposition

**As a** customer service agent,  
**I want** to see whether an account’s discount issue was investigated and closed,  
**So that** I do not contradict the investigation team or repeat manual credits.

**Acceptance criteria**

- Given a linked CRM or case ID exists, when I open the customer record, then I see latest disposition summary (not full investigator notes if restricted).
- Given no case exists, when I search, then I see “no investigation on file” rather than an error.

---

## US-05 — Data engineer monitors pipeline health

**As a** data engineer,  
**I want** job failures for promo fact pipelines to alert the on-call channel,  
**So that** dashboards are not silently stale.

**Acceptance criteria**

- Given a job failure, when it occurs, then an alert fires to **TBD channel** with job name and last success time.
- Given partial load, when rules define “do not publish,” then dashboard shows maintenance state.

---

## Backlog / future

- US-06: Self-service threshold simulation (finance sandbox) — **Could**, legal/complexity review first.
