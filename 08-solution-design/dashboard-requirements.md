# Dashboard Requirements — PromoLeak Radar

**Audience:** Data/BI builders, Product, Finance consumers  
**Status:** First draft; wireframe companion in `dashboard-wireframe.md`

## Personas & primary questions

| Persona | Primary questions | Typical depth |
|---------|-------------------|---------------|
| Finance analyst | How much discount exposure on flagged orders this week vs. last? Which campaigns? | Aggregate → campaign |
| Ops / investigation lead | What’s new in the queue, who is working it, any SLA risk? | Queue metrics |
| Growth owner | Is a specific code “too hot” on margin? | Campaign slice |
| Exec (occasional) | Directionally better or worse after rule change? | Single headline tile |

## Global filters (MVP)

- Date (default: yesterday + rolling 7 days)
- Channel (web, app, marketplace — as available)
- Category / department
- Campaign or coupon code (typeahead)

## Core views

### 1. Executive pulse (optional one screen)

- Headline: flagged order count, estimated margin at risk (method footnoted).
- Sparkline 30-day trend.
- Annotation area for known events (e.g., “Black Friday”, “config bug #123”).

### 2. Operations dashboard

- Table: top campaigns by flagged discount dollars.
- Histogram: distribution of effective discount % on flagged orders.
- Queue: new / in review / closed counts by investigator.

### 3. Investigator drill-down

- Order-level table with reason codes, link to detail pane (see FR-03).
- Ability to export **within policy** (column list approved by Legal).

## Data freshness & quality

- Show “last successful pipeline run” timestamp on every view.
- If referral data lags cart data, show separate freshness chips.

## Non-goals for MVP dashboard

- Fancy customer network graphs — nice later; not required to start.

## Open decisions

- Single BI tool vs. embedded app — org standard wins.
- Currency handling for cross-border if applicable.
