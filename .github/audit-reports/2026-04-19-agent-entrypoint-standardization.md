---
record-id: 2026-04-19-agent-entrypoint-standardization
record-type: maintenance-run
date: 2026-04-19
trigger: approved PullLog agent entrypoint standardization, naming unification, and agent catalog rollout
acting-agent: docs-impl-maintainer
status: applied
scope: standardize custom agent names across frontend, contract, and pulllog-docs; add an E2E orchestrator for frontend; add orchestrator prompts; document orchestrator-first usage; add an internal agent catalog
exclusions: backend custom agent implementation, workspace-router introduction, VS Code task scaffolding, and unrelated documentation changes
source-records: []
target-files:
    - ../frontend/.github/agents/frontend-orch-feature.agent.md
    - ../frontend/.github/agents/frontend-arch-system.agent.md
    - ../frontend/.github/agents/frontend-design-uiux.agent.md
    - ../frontend/.github/agents/frontend-impl-feature.agent.md
    - ../frontend/.github/agents/frontend-review-feature.agent.md
    - ../frontend/.github/agents/frontend-design-e2e-scenario.agent.md
    - ../frontend/.github/agents/frontend-impl-e2e-playwright.agent.md
    - ../frontend/.github/agents/frontend-debug-e2e.agent.md
    - ../frontend/.github/agents/frontend-review-e2e.agent.md
    - ../frontend/.github/agents/frontend-orch-e2e.agent.md
    - ../frontend/.github/prompts/start-feature-workflow.prompt.md
    - ../frontend/.github/prompts/start-e2e-workflow.prompt.md
    - ../frontend/docs/architecture/feature-development-workflow.md
    - ../frontend/docs/architecture/e2e-test.md
    - ../frontend/docs/architecture/e2e-test-ja.md
    - ../frontend/README.md
    - ../contract/.github/agents/contract-orch-audit.agent.md
    - ../contract/.github/agents/contract-audit-frontend.agent.md
    - ../contract/.github/agents/contract-audit-backend.agent.md
    - ../contract/.github/agents/contract-review-gap.agent.md
    - ../contract/.github/agents/contract-impl-spec.agent.md
    - ../contract/.github/prompts/run-api-contract-audit.prompt.md
    - ../contract/.github/instructions/api-contract-sync.instructions.md
    - ../contract/docs/api-contract-sync-workflow.md
    - ../contract/README.md
    - .github/agents/docs-orch-maintenance.agent.md
    - .github/agents/docs-audit-governance.agent.md
    - .github/agents/docs-audit-public.agent.md
    - .github/agents/docs-plan-changelog.agent.md
    - .github/agents/docs-plan-roadmap.agent.md
    - .github/agents/docs-impl-maintainer.agent.md
    - .github/prompts/start-docs-maintenance-workflow.prompt.md
    - .github/agent-catalog.md
    - .github/audit-reports/2026-04-19-agent-entrypoint-standardization.md
    - docs/document-governance.md
    - docs/document-governance-ja.md
---

# Agent Entrypoint Standardization

## Confirmed decisions
- Use orchestrators as the default user-facing entrypoints.
- Reduce normal entrypoint count by keeping specialist agents behind orchestrators.
- Standardize agent names to kebab-case with the pattern `<subproject>-<group>-<role>`.
- Add one prompt per orchestrator.
- Add a shared internal catalog so agent ownership and entrypoints stay discoverable.

## Implemented changes
- Renamed frontend feature workflow agents to the standardized naming scheme.
- Added `frontend-orch-e2e` so frontend E2E now has an orchestrator entrypoint.
- Renamed contract and pulllog-docs agents to the same naming scheme.
- Updated prompts so each orchestrator has a clear startup entry.
- Updated workflow documentation and README content to recommend orchestrator-first usage.
- Added `.github/agent-catalog.md` as the internal quick index for agent ownership and prompts.

## Residual follow-up
- Decide later whether VS Code task scaffolding should be added for orchestrator prompts.
- Add backend orchestrator workflows only when backend-specific specialist agents are introduced.