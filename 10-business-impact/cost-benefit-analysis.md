# Cost-Benefit Analysis: PromoLeak Radar (Northline Market)

**Project:** PromoLeak Radar  
**Document type:** Working estimate for portfolio and sponsor workshop  
**Disclaimer:** All figures are **fictional, rounded assumptions** for a mid-sized e-commerce profile. They are not audited Northline Market financials. Replace with FP&A models, vendor quotes, and loaded labor rates before any budget commit.

---

## 1. Purpose

Summarize what Finance thinks is walking out the door on promos today, what PromoLeak-style visibility, rules, and queue work might recover, and what it costs to build and run. The numbers support a **phased** decision, not a big-bang bet.

---

## 2. Current leakage estimate ( fictional, Finance-style )

| Item | Amount | How to read it |
|------|--------|----------------|
| Annual promo-related leakage ( duplicate accounts, first-time reuse, referral abuse, stacking, low-margin depth, net of known noise ) | **$680,000** | Aligns with the problem scale described in `01-project-overview/business-case.md`; exact split by lever is still workshop work |
| Share Finance calls **addressable** with better definitions, rules, and containment in a 24-month horizon | **40%** of $680k = **$272,000 / year** at run rate | Honest haircut: not every dollar is recoverable without hurting conversion or Legal comfort |

---

## 3. Expected leakage reduction ( fictional )

| Scenario | Year 1 realized benefit ( ramping delivery ) | Mature annual run rate ( steady state after tuning ) |
|----------|-----------------------------------------------|--------------------------------------------------------|
| Conservative | $58,000 | $95,000 |
| **Expected** | **$95,000** | **$145,000** |
| Optimistic | $125,000 | $175,000 |

**Expected case logic ( simple, not a Monte Carlo )**

- Year 1 only reaches part of the addressable pool because definitions, queue staffing, and rules need tuning (see **Phase 4** in `final-recommendation.md`).  
- Mature run rate assumes PromoLeak KPIs are trusted, kill-switch discipline exists (FR-017, BR-014), and Finance keeps BR-018 definitions stable enough to act.

---

## 4. Estimated implementation cost ( one-time, fictional )

| Cost bucket | Conservative | **Expected** | Optimistic |
|-------------|--------------|--------------|------------|
| Engineering ( integrations, rules layer, queue, warehouse marts ) | $165,000 | **$95,000** | $72,000 |
| Data / BI modeling and pipelines | $62,000 | **$48,000** | $35,000 |
| Product, BA, UAT coordination ( internal hours loaded ) | $48,000 | **$32,000** | $24,000 |
| Legal / Compliance review and template work ( incremental ) | $28,000 | **$18,000** | $12,000 |
| **Total one-time** | **$303,000** | **$193,000** | **$143,000** |

Expected **$193,000** assumes Northline already has a warehouse and SSO patterns (NFR-002) and is **extending** rather than buying a full external fraud suite.

---

## 5. Ongoing operating cost ( annual, fictional )

| Cost bucket | Expected annual |
|-------------|-----------------|
| Blended investigation and queue lead time ( partial FTE ) | $38,000 |
| Finance and Data touch for definitions, tie-outs, mart changes | $14,000 |
| Cloud, BI increment, log retention | $12,000 |
| Small enhancements and vendor ticky-tack | $10,000 |
| **Total annual operating** | **$74,000** |

Round to **$74k** in tables below.

---

## 6. Expected monthly savings and annualized savings ( expected case )

| Period | Gross benefit | One-time cost | Operating cost | Net |
|--------|---------------|---------------|------------------|-----|
| **Year 1** | $95,000 | $193,000 | $74,000 | **negative $172,000** |
| **Year 2** | $145,000 | $0 | $74,000 | **positive $71,000** |
| **Year 3** | $152,000 ( small uplift from tuning ) | $0 | $76,000 | **positive $76,000** |

**Annualized savings ( mature steady state, expected ):** about **$145,000 / year** gross margin or cost avoidance before operating cost.

**Simple cumulative three-year view ( expected, not discounted )**

- Benefits: $95k + $145k + $152k = **$392k**  
- Costs: $193k + $74k + $74k + $76k = **$417k**  
- **Cumulative net ( rough ): negative $25k over three years** before discounting

That honest outcome is why the written recommendation is **phased with a hard 12-month benefits review**, not "this pays back in six months" hype. If Northline executes closer to the **optimistic** benefit row and holds **optimistic** one-time costs, the picture flips sooner ( see sensitivity ).

---

## 7. ROI estimate and payback period

Using **undiscounted** expected numbers:

- **Simple ROI after year 2:** cumulative benefit $95k + $145k = $240k vs cumulative cost $193k + $74k + $74k = $341k, still underwater.  
- **After year 3:** cumulative benefit about $392k vs cost about $417k, still slightly underwater in this cut.

**Payback:** Under the **expected** central case above, **simple payback extends past three years** unless benefits run closer to **optimistic** or one-time costs land closer to **optimistic**.

**Optimistic quick check ( illustrative flip )**

- One-time **$143k**, operating **$70k / year**, mature benefit **$175k / year**, year 1 benefit **$125k**  
- Three-year benefit: $125 + $175 + $180 = $480k  
- Three-year cost: $143 + $70 + $70 + $72 = $355k  
- Cumulative: about **+$125k** over three years

So the business case is **sensitive**. The recommendation is still to proceed in phases because some costs ( firefighting, exec time, goodwill credits ) are not fully in the table ( see section 9 ).

---

## 8. Sensitivity analysis ( summary )

| Case | Year 1 benefit | Mature annual benefit | One-time cost | Annual operating | Comment |
|------|----------------|----------------------|---------------|------------------|---------|
| **Conservative** | $58,000 | $95,000 | $303,000 | $82,000 | High build, slower capture, heavier ops |
| **Expected** | $95,000 | $145,000 | $193,000 | $74,000 | Base plan in this doc |
| **Optimistic** | $125,000 | $175,000 | $143,000 | $70,000 | Tight scope, good data, Growth and Finance stay aligned |

---

## 9. Costs not included ( read before approving budget )

- **Opportunity cost** of Engineering and Data not shipping other roadmap items.  
- **Conversion or revenue** hit if caps are too blunt ( model with Growth, not only Finance ).  
- **Customer churn or complaint** handling spikes if comms are mishandled ( Legal gate, NFR-012 ).  
- **External counsel** for a serious dispute beyond the small Legal line item.  
- **Major package** fraud vendor purchase ( intentionally out of scope for this CBA ).

---

## 10. Risks that could reduce benefits

| Risk | Effect on benefit |
|------|-------------------|
| Weak or late feeds ( referral, payment hash, marketplace gap ) | Lower measured and actual recovery; more manual work |
| High false positive rate without tuning | Investigators throttle rules; savings stall |
| Growth and Finance never agree on BR-018 | KPI fights; delayed decisions on caps |
| BR-010 style publish governance still missing | Repeat "code went hot" incidents even with dashboards |

---

## 11. Recommendation based on these numbers

Do **not** approve PromoLeak on a pure three-year ROI from the table above in the **expected** column alone, because the strict cumulative math is flat to slightly negative.

Do **approve a gated phased program** because:

1. The **$680k** leakage estimate is large enough that even the **conservative** mature capture ( $95k / year ) pays variable operating cost if one-time spend is controlled.  
2. **Optimistic** execution clears costs in a reasonable window, and many controls ( definitions, queue, kill-switch ) have value **beyond** the dollars in the model ( fewer board surprises, faster containment ).  
3. A **12-month benefits checkpoint** with a pre-agreed minimum realized benefit or a pause decision keeps the portfolio honest.

---

## Change log

| Date | Author | Note |
|------|--------|------|
| 2026-05-14 | BA case study | Fictional mid-market numbers with explicit sensitivity and cost exclusions |
