# Project Charter — PromoLeak Radar

**Document status:** Draft v0.1 — not yet signed off by sponsor  
**Last updated:** [Date TBD]

## Purpose

This charter frames the analysis work for promotion abuse and revenue leakage at a mid-sized e-commerce retailer (working name: **Northline Commerce**). It is meant to align the sponsor, product, finance, and operations on scope and authority—not to lock technical design.

## Background

Finance flagged a widening gap between expected gross margin after promotions and actual margin on certain categories. Customer service and fraud teams also report repeat patterns: duplicate accounts, stacked codes, and referral payouts that do not match genuine acquisition. This project documents the business problem, requirements, and a path to better detection and controls.

## Objectives

1. Quantify where leakage occurs (coupons, referrals, first-time buyer offers) and which product lines are most exposed.
2. Produce business and functional requirements for monitoring, alerting, and process changes.
3. Define dashboard and reporting needs so operations and finance can act on signals without waiting for ad hoc extracts.
4. Prepare UAT-ready artifacts for whatever solution the organization selects (build vs. buy still open).

## Scope (in)

- Business analysis, process modeling, requirements, traceability, UAT planning, and impact/KPI framing.
- Assumptions and risks documented explicitly; dependencies on data quality and legacy promo engine called out.

## Scope (out)

- Implementation of production software (handled by engineering/vendor after handoff).
- Legal determination of “fraud” vs. “policy abuse” — we document business rules; legal reviews separately.

## Sponsor & decision rights

| Role | Name / area | Notes |
|------|-------------|--------|
| Executive sponsor | TBD — VP Finance or CFO delegate | Budget and policy trade-offs |
| Product owner | TBD — Promotions / Growth | Rule changes and customer-facing impact |
| BA lead | TBD | This documentation set |

## Success criteria (for this BA phase)

- Stakeholders agree on problem statement and priority use cases.
- BRD and supporting packs are reviewable by engineering for sizing.
- Traceability from high-level needs to test themes exists (gaps marked TBD).

## Open items

- Exact sponsor names and sign-off date.
- Whether “referral” scope includes partner/channel programs or DTC only.
