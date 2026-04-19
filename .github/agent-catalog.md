# PullLog Agent Catalog

## Purpose

This catalog is the quick index for PullLog custom agents.

Use it when you need to know:
- which agent is the entry point for a workflow
- which specialists sit under an orchestrator
- which prompt to start from
- whether a specialist should normally be called directly

## Entry policy

- Default rule: start from an orchestrator.
- Default user-facing entrypoints are orchestrators and their prompts.
- Specialist agents exist for delegated work and narrow follow-up, not as the normal first stop.

## Naming rule

Use this pattern for new agents:

`<subproject>-<group>-<role>`

Examples:
- `frontend-orch-feature`
- `frontend-impl-e2e-playwright`
- `contract-review-gap`
- `docs-plan-changelog`

Preferred group tokens:
- `orch`: workflow entrypoint and delegation
- `arch`: architecture design
- `design`: scenario or UI design
- `audit`: evidence gathering and drift review
- `plan`: read-only planning
- `impl`: editing or execution
- `debug`: failure reproduction and repair
- `review`: quality review and verdict

## Catalog

### frontend

#### Feature workflow

| Role | Agent | Normal entry? | Prompt |
|---|---|---|---|
| Orchestrator | `frontend-orch-feature` | Yes | `Start Frontend Feature Workflow` |
| Architecture | `frontend-arch-system` | No | - |
| UI/UX | `frontend-design-uiux` | No | - |
| Implementation | `frontend-impl-feature` | No | - |
| Review | `frontend-review-feature` | No | - |

#### E2E workflow

| Role | Agent | Normal entry? | Prompt |
|---|---|---|---|
| Orchestrator | `frontend-orch-e2e` | Yes | `Start Frontend E2E Workflow` |
| Scenario design | `frontend-design-e2e-scenario` | No | - |
| Implementation | `frontend-impl-e2e-playwright` | No | - |
| Debug | `frontend-debug-e2e` | No | - |
| Review | `frontend-review-e2e` | No | - |

### contract

| Role | Agent | Normal entry? | Prompt |
|---|---|---|---|
| Orchestrator | `contract-orch-audit` | Yes | `Start Contract Audit Workflow` |
| Frontend audit | `contract-audit-frontend` | No | - |
| Backend audit | `contract-audit-backend` | No | - |
| Integrated review | `contract-review-gap` | No | - |
| Contract update | `contract-impl-spec` | No | - |

### pulllog-docs

| Role | Agent | Normal entry? | Prompt |
|---|---|---|---|
| Orchestrator | `docs-orch-maintenance` | Yes | `Start Docs Maintenance Workflow` |
| Governance audit | `docs-audit-governance` | No | - |
| Public-doc audit | `docs-audit-public` | No | - |
| Changelog planning | `docs-plan-changelog` | No | - |
| Roadmap planning | `docs-plan-roadmap` | No | - |
| Maintenance execution | `docs-impl-maintainer` | No | - |

### backend

#### Feature workflow

| Role | Agent | Normal entry? | Prompt |
|---|---|---|---|
| Orchestrator | backend-orch-feature | Yes | Start Backend Feature Workflow |
| Architecture | backend-arch-api | No | - |
| Contract alignment | backend-design-contract | No | - |
| Implementation | backend-impl-feature | No | - |
| Review | backend-review-feature | No | - |

## Maintenance rule

When adding a new workflow:
1. Add the orchestrator first.
2. Keep specialist agents behind the orchestrator by default.
3. Add one prompt per orchestrator.
4. Update this catalog in the same change.