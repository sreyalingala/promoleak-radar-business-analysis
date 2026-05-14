# Interview Questions (Bank)

Pick a subset per interview; you’ll bore people if you run the whole list. Wording is generic — swap in your company’s system names.

## Finance / FP&A

1. How do you currently estimate “margin after promotions” by category? What breaks when a code is mis-configured?
2. What would convince you a leakage number is directionally correct even if not perfect?
3. Which promo types worry you most: % off, fixed amount, BOGO, referral credit, shipping?
4. Who signs off when a campaign runs hotter than forecast?

## Growth / Promotions

1. Walk me through creating a typical coupon campaign from idea to live — who touches it, what systems?
2. Where do rules live for: stacking, one-per-customer, first purchase, category exclusions?
3. Have you ever had to kill a code mid-flight? What happened?
4. What customer segments are you unwilling to restrict even if abuse exists?

## Engineering

1. At which point in the order lifecycle is discount final? Refunds, partial captures, split shipments?
2. How do we identify a “customer” technically — account ID, email, device, payment hash?
3. What change would be cheap vs. expensive: new cap, new eligibility check, new event stream for BI?
4. Known bugs or “we’ve always lived with it” behaviors affecting promos?

## Customer Service

1. Top five reasons customers contact us about discounts or referrals (rough % if known).
2. What do agents have permission to do today (credits, manual discounts)? Audit trail?
3. Phrases customers use when they’re pushing policy vs. genuinely confused?

## Fraud / Risk (if applicable)

1. What patterns you’ve already seen — velocity, linked accounts, mule behavior?
2. What evidence do you need to freeze or claw back value without creating PR risk?
3. External signals we could use later (device intel, consortium) — in or out of scope politically?

## Legal / Compliance

1. What can we say in-app or email when we adjust or remove rewards?
2. Constraints on data retention for investigation queues?

## Data / BI

1. Canonical sources for orders, payments, promo applications, referrals — and where they disagree.
2. Latency acceptable for an operations dashboard (near real-time vs. daily).

## Capture format

- Date, interviewer, interviewee names/roles.
- Decisions vs. hypotheses labeled clearly.
- Follow-ups with owner and due date.
