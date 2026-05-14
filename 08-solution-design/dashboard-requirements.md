# Dashboard Requirements — PromoLeak Radar

**Audience:** Data/BI builders, Product, Finance consumers  
**Status:** First draft; wireframe companion in `dashboard-wireframe.md`

## Who looks at which screen (rough)

| Role | What they’re trying to answer | How deep they go |
|------|-------------------------------|-------------------|
| Finance analyst | How bad was this week vs last; which campaigns drove it? | Summary → campaign |
| Ops / investigation lead | What landed in the queue; who’s stuck; anything aging out? | Queue view |
| Growth owner | Is this one code cooking margin? | Single campaign slice |
| Exec (drops in occasionally) | After last week’s rule change, better or worse? | One headline tile is enough |

## Global filters (MVP)

- Date (default: yesterday + rolling 7 days)
- Channel (web, app, marketplace — as available)
- Category / department
- Campaign or coupon code (typeahead)

## Core views

### 1. Exec pulse (optional)

- Big numbers: flagged orders, rough $ at risk — with the same footnote Finance approved.
- 30-day trend line; scribble space (or annotations) for “we changed rule X on this date.”

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
