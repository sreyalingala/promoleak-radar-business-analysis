# UAT Plan — PromoLeak Radar

**Version:** Draft 0.1  
**Scope:** Business acceptance of monitoring, workflow, and rule changes delivered for MVP (exact build scope TBD).

## Objectives

- Confirm that agreed requirements work for real analyst and investigator tasks.
- Validate that metrics definitions match Finance expectations within agreed tolerance.
- Verify role-based access and audit behavior with Security sample checks.

## Entry criteria

- Test environments provisioned; masked or synthetic data approved.
- Test cases authored and traceable (see `test-cases.md`).
- Known defects classified; **no Sev-1 open** for core happy paths (define Sev-1 with team).

## Participants & roles

| Role | Responsibility |
|------|----------------|
| UAT Lead | Schedule, sign-off pack, defect triage cadence |
| Business SMEs | Finance, Growth delegate, CS delegate |
| QA | Supports reproduction, logs environment details |
| Product Owner | Accepts scope changes during UAT only through change control |

## Schedule (placeholder)

| Phase | Duration | Notes |
|-------|----------|-------|
| UAT prep walkthrough | 1 session | Show dashboards + sample cases |
| Cycle 1 execution | TBD | Core reporting + queue |
| Cycle 2 | TBD | Rule changes + edge cases |
| Sign-off window | 3 business days | For formal approval doc |

## Environment

- URL(s): TBD  
- Test accounts: TBD (role matrix)

## Exit criteria

- All **Must** test cases executed; pass or accepted waiver with sponsor approval.
- Critical defects resolved or explicitly deferred with documented business risk.
- Sign-off sheet captured (store per org policy; not necessarily in this repo).

## Communication

- Daily stand-down during active UAT (15 min): blockers, new defects.
- Defect log uses `defect-log-template.md` or Jira — pick one source of truth.

## Post-UAT

- Hypercare week: watch pipeline latency and CS ticket tags.
