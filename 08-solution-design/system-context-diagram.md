# System Context Diagram (Text / C4 Level 1)

**Note:** Box names are generic; swap in whatever we actually run internally.

```mermaid
flowchart LR
  subgraph actors [People]
    Cust[Customer]
    Inv[Investigator]
    Fin[Finance analyst]
    Gro[Growth marketer]
  end

  subgraph northline [Northline Commerce]
    Web[Web / App Storefront]
    Cart[Cart and Checkout]
    Promo[Promotion Engine]
    Pay[Payments]
    OMS[Order Management]
    Ref[Referral Service]
    IdP[Customer Identity]
    CRM[CRM / CS Platform]
    DW[Data Warehouse / Lake]
    Dash[PromoLeak Dashboard]
    Case[Case / Queue Tool]
  end

  Cust --> Web --> Cart
  Cart --> Promo
  Cart --> Pay
  Cart --> OMS
  Web --> Ref
  Web --> IdP
  Cust --> CRM

  Promo --> DW
  OMS --> DW
  Pay --> DW
  Ref --> DW
  IdP --> DW
  CRM --> DW

  DW --> Dash
  Fin --> Dash
  Inv --> Dash
  Inv --> Case
  Case --> CRM
  Gro --> Promo
```

## Boundaries

- **In scope for this analysis:** feeds and flows we need to flag orders and feed dashboard + case tool.
- **Out for now:** WMS, physical returns handling — except where refunds change net promo dollars.

- PII minimized on Dash by role.
- Any new SaaS goes through normal vendor security — list TBD.

## Follow-up

Drop a PNG export here when arch review produces something prettier than my mermaid.
