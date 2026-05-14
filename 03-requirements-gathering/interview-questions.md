# Interview Questions: PromoLeak Radar (Northline Market)

**Use:** Pick **8–10** questions per session; send the shortlist 24 hours ahead so people can pull examples. Not every question every time.

**Context to state at the start:** PromoLeak Radar is about **promotion-related revenue leakage**, duplicate accounts, first-time coupon reuse, referral misuse, stacking, and **high discounts on low-margin SKUs**, plus bad config where the system doesn’t match what Growth thought they published.

---

## Marketing / Growth Manager

1. Walk me through the last coupon campaign you launched from idea to live: who typed the rules, who clicked “go,” and in which tool(s)?
2. For Northline Market today, who is allowed to create a **stackable** code vs. non-stackable, and is that enforced in the tool or only in a runbook?
3. What’s your **written rule** for first-time buyer discounts (one per person, one per household, one per device, whatever you have) vs. what checkout actually enforces?
4. Have you ever **killed or capped** a code mid-flight? What broke (CS volume, social, tech), and how long did it take to stop new uses?
5. Which **categories or SKUs** are you explicitly not supposed to deep-discount, and do exclusions always make it into the promo config, or do they sometimes slip?
6. What **referral** milestones pay out today, and have you seen payouts you’d call “wrong” even if the system allowed them?
7. When Finance says a campaign “ran hot,” what **number** would you need to see to agree, gross discount dollars, margin after promo, something else?
8. What customer segments or campaigns are you **not willing** to tighten with stricter rules in v1, even if there’s some abuse?
9. What reports or exports do **you** use weekly to sanity-check promos, or do you rely on Finance to tell you something’s wrong?
10. If Northline Market added a **pre-flight checklist** before high-risk codes go live, what three checks would you insist stay short enough that people actually use them?

---

## Finance Manager

1. How do you build **margin after promotions** by category today, which systems, which pulls, and where do numbers **fight** with Growth’s view?
2. When the plan misses on promo-heavy categories, how much of that do you attribute to **volume mix** vs. **discount depth** vs. “something’s off”, gut split is fine.
3. What would convince you a **leakage estimate** is directionally right even if it’s not penny-perfect?
4. Which promo mechanics worry you most for Northline Market right now: **first-time**, **referral**, **sitewide %**, **BOGO**, **shipping**, **loyalty**, rank if you can.
5. Do you have a **threshold** (margin % or discount %) where you’d want an automatic **review flag** on an order or campaign, or is that still undefined?
6. Who at Northline **signs off** when Finance asks Growth to cap or kill a code, and how often did that actually happen last year?
7. What’s missing from **current dashboards** that forces you into ad hoc Excel work during close?
8. How do you want **referral cost** shown, separate from cart coupons, blended, or you don’t care as long as total promo $ reconciles?
9. What **audit trail** do you need if Northline Market clawed back or adjusted a reward, order id, rule version, who approved?
10. For board or exec readouts, what **one headline metric** would you want PromoLeak to feed first (knowing v2 can add more)?

---

## Fraud / Risk Analyst

1. What **repeat patterns** do you already see on duplicate accounts, referral loops, or first-time code farming, even if informal notes only?
2. When you say an order “looks abusive,” what **signals** do you actually look at today (device, payment hash, velocity, address, something else)?
3. What’s the **manual review** path now, ticket from CS, export from Finance, your own query, and where does it break?
4. What evidence would you need to **restrict an account** or **reverse a referral credit** without Legal pushing back?
5. What **false positive rate** (rough) would make the queue unusable for your team size?
6. Are there referral or promo cases you **do not investigate** because tooling doesn’t support them, name them.
7. What would a **reason code** list need to include so you’re not typing the same paragraph on every case?
8. How do you want **handoff to CS** documented when you close a case, what does the agent need to see?
9. External data (device intel, consortium, etc.): **in or out** of scope for Northline Market politically and contractually?
10. What’s the **worst incident** Northline Market had in the last 12 months on promos, anonymized, and what would have prevented it or caught it faster?

---

## Product Manager (e-commerce)

1. Map the **happy path** for applying a coupon and a referral credit on the same order, where does each discount get calculated and stored?
2. Where do **stacking** and **order of application** get decided in the product today, and where do CS agents *think* it happens?
3. What **guardrails** exist in the admin UI so Growth can’t accidentally publish a stackable + category-wide combo without a warning?
4. What promo-related **bugs or “known quirks”** are in the backlog right now, even if deprioritized?
5. Who gets paged when checkout **mis-applies** a promo at peak, and what’s the rollback playbook?
6. What would you need in-product (banner, message, disabled code) when Northline Market **turns off** a campaign for abuse vs. for a mistake?
7. How does **guest checkout** interact with first-time and referral rules, edge cases you already know hurt CS?
8. What **identity** does the product use for “one per customer”, account only, or something richer planned?
9. What’s **out of scope** for your team this quarter that still blocks a clean promo-leak fix (platform upgrade, vendor dependency)?
10. If we proposed a **case queue** for flagged orders in v1, is that net-new product work or something an existing tool should own?

---

## Engineering Lead

1. At what point in the **order lifecycle** is promotional discount considered final for reporting, authorized, captured, shipped, something else?
2. Where do promo rules **execute** today (cart service, promo microservice, OMS, batch repricing), list as built, not as designed on a slide.
3. What’s **cheap** to change in the next release train: a new cap, a new eligibility check, an event to the warehouse, a kill flag?
4. What’s **expensive or risky** (refunds, split shipments, partial captures, marketplace orders)?
5. How does Northline Market technically represent **customer identity** for promos, account id, email hash, payment token, device id, and what’s missing?
6. What **logging** exists today for “which rules fired in what order” on an order, suitable for Fraud or not?
7. Referral service: **webhooks**, batch files, latency, what breaks BI when it’s slow or wrong?
8. **Freeze windows** near peak: when can we not touch promo logic, and when is there a carve-out for revenue leaks?
9. What **debt** in the promo stack worries you if we add detection rules without paying it down first?
10. If Finance asked for “**every** promo line with rule version id,” is that data available end-to-end today, yes/no/partially where?

---

## Data Analyst (or BI lead)

1. What are the **canonical tables** (or reports) for order lines, promo applications, referral events, and payments, and where do they **disagree**?
2. What’s the **freshness** of each feed, hourly, daily, T+1, and who owns fixing upstream delays?
3. Can you produce a **sample** of “orders with >X% effective discount on category Y” without a week of SQL, or is that always a custom job?
4. What **join keys** are reliable between referral, identity, and order facts?
5. What **PII** restrictions apply to extracts for Fraud vs. for Finance aggregates?
6. What would a **minimum** Northline Market v1 dashboard need, three metrics, your pick, to be worth maintaining?
7. Where does **COGS or margin** live for SKU-level “low margin” flags, trusted or not?
8. What’s been tried before on **“promo abuse”** reporting that got abandoned, and why?
9. **Marketplace** orders: do we get enough promo detail in the warehouse to include them in v1 or should we exclude explicitly?
10. What would you need from Engineering in writing to add **new event fields** for detection without breaking existing marts?

---

## Customer Support Manager

1. Top **ticket reasons** tied to discounts, codes, referrals, rough volume or rank order if you don’t have %.
2. What can agents **do** today (goodwill credit, manual discount, escalate to Fraud), and is every action logged the same way?
3. When Finance or Fraud **changes** an account’s rewards, what do agents see in the CRM, anything, or do they get blindsided?
4. What phrases do customers use when they’re **pushing policy** vs. genuinely confused?
5. What **SLA** pressure hits when a bad promo runs over a weekend, staffing reality?
6. What **scripts or macros** are outdated the minute Growth changes a rule?
7. If flagged orders got a **disposition** field visible to CS, what would you want it to say in plain English?
8. What **training** lead time do you need before customer-visible enforcement changes?
9. Which **escalations** to Fraud or Legal today take longest, and why?
10. What would **reduce repeat contacts** on the same promo dispute, one thing, even small?

---

## Compliance / Legal Representative

1. What does Northline Market’s **customer-facing language** say today about changing, revoking, or clawing back promotions and referral rewards?
2. What can we **say in email or in-app** when we adjust rewards, any mandatory disclosures or tone constraints?
3. What **investigation data** can we retain, for how long, and who may access it, especially payment-adjacent fields?
4. Are there **referral** terms that conflict with how Engineering actually pays out (timing, eligibility)?
5. What words should we **avoid** in internal dashboards that might leak into screenshots (e.g., loaded labels)?
6. When CS or Fraud **restricts an account** for promo abuse, what approvals or notices are required before the customer is told?
7. Any **jurisdictional** wrinkles for Northline Market’s customer base (state/country) that change promo enforcement?
8. What review **SLA** can Legal commit to for PromoLeak-related comms templates during UAT prep?
9. **Profiling** risk: if detection uses certain attributes, what does Legal need to review before go-live?
10. What **policy documents** should the BA read end-to-end before the requirements workshop, links or owners?

---

## Capture format (for the BA)

- Date, interviewer, interviewee name + role.  
- Label lines as **decision**, **hypothesis**, or **follow-up** (owner + due date).  
- Attach screenshots or ticket IDs per Northline Market data policy, not in this public portfolio repo if PII.
