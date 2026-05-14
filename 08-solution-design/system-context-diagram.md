# System Context Diagram (Text / C4 Level 1)

**Note:** Names are generic placeholders. Swap for Northline’s actual systems when doing internal documentation.

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

- **In scope for analysis:** data flows needed to compute flags and feed dashboard/case tools.
- **Out of scope (for now):** warehouse management, physical return logistics (except refund events that affect net promo impact).

## Trust boundaries

- PII minimized in Dash per role.
- External SaaS (if any) must meet vendor security review — table TBD.

## Follow-up

- Replace mermaid with official architecture diagram in `assets/diagrams/` when available.
