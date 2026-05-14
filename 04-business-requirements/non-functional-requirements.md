# Non-Functional Requirements: PromoLeak Radar

> **Note:** NFRs below apply to the **Northline Market** case study. Targets use **TBD** where a real program would plug SLAs from Engineering, Security, and Legal. Stakeholders must validate before contract or release sign-off.

**Project:** PromoLeak Radar

---

## Non-functional requirements

| Requirement ID | Category | Requirement | Rationale | Priority | Validation method |
|----------------|----------|-------------|-----------|----------|---------------------|
| NFR-001 | Performance | Primary dashboard views for default filters load within **TBD** seconds on a standard office connection. Nightly or agreed batch jobs that feed leakage metrics complete before **TBD** local time for morning review. | Slow UI and stale numbers kill adoption and incident response. | Must | Load or timing test in UAT; job monitoring with alert on SLA breach |
| NFR-002 | Security | Authentication uses Northline Market **corporate IdP** (SSO) or agreed standard; no standalone prod passwords for admin paths; session timeout per security policy. | Central identity and MFA reduce account takeover risk. | Must | Security checklist in UAT |
| NFR-003 | Privacy | PII in investigation views is **masked or role-gated** per Legal table; exports require role, are logged, and use approved column sets. | Investigators need enough context without over-sharing PII. | Must | Role matrix test; Legal spot check on sample export |
| NFR-004 | Availability | PromoLeak monitoring UI target uptime **TBD** excluding published maintenance; graceful message if partial data load fails. | If the tool is down during an incident, teams revert to spreadsheets. | Should | Uptime report from hosting or SRE; UAT failure-path test |
| NFR-005 | Auditability | Audit events for configuration, kill-switch, case status, and exports are **append-only** in production configuration; retention meets Legal schedule. | Disputes and internal investigations need a defensible trail. | Must | Config review; sample audit export |
| NFR-006 | Usability | A trained Finance or Fraud user completes primary dashboard tasks in the **guided UAT script** without writing SQL. | Self-serve cuts load on Data for routine questions. | Must | UAT pass or fail with timing notes |
| NFR-007 | Scalability | Design supports **TBD** peak daily order volume and **TBD** concurrent investigators without redesign of core fact tables (headroom documented by Engineering). | Peak promos and queue spikes stress the system. | Should | Written capacity statement; optional load test |
| NFR-008 | Data retention | Investigation artifacts and exports follow **retention schedule TBD**; purge or legal hold path documented and owned. | Retention mistakes create Legal and privacy exposure. | Must | Legal sign-off on retention; job owner in runbook |
| NFR-009 | Maintainability | Threshold and scoring changes use **configuration or admin paths** where design allows, so Finance and Fraud are not blocked on every software release. | Tuning is frequent early in a pilot. | Should | UAT demo of config change without code deploy |
| NFR-010 | Reporting accuracy | Headline leakage metrics reconcile to a **Finance tie-out sample** within **TBD** tolerance, or variance is documented with cause. | Wrong numbers waste executive trust and drive bad caps. | Must | Reconciliation test case in UAT (see test pack) |
| NFR-011 | Access control | **Least privilege**: aggregate-only roles cannot open full investigation panes; admin actions limited to named roles; deny attempts logged. | Stops casual spread of sensitive data. | Must | Negative permission tests in UAT |
| NFR-012 | Compliance review | Customer-facing templates for enforcement, clawback, or restriction carry **Legal approval** and version id before production enablement. | Copy drift creates enforceability and brand risk. | Must | Legal sign-off item on release checklist |
