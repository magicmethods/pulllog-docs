---
record-id: 2026-04-18-agent-driven-docs-maintenance-review
record-type: maintenance-run
date: 2026-04-18
trigger: approved pulllog-docs documentation maintenance for audit-evidence metadata and records-maintenance flow
acting-agent: docs-maintainer
status: applied
scope: standardize audit evidence metadata, normalize this evidence record, add read-only planners for CHANGELOG and ROADMAP preparation, and update governance plus orchestrator flow in pulllog-docs
exclusions: frontend, backend, contract, direct content updates to CHANGELOG.md or ROADMAP.md, and unrelated public-documentation changes
source-records: []
target-files:
	- .github/agents/docs-orch-maintenance.agent.md
	- .github/agents/docs-plan-changelog.agent.md
	- .github/agents/docs-plan-roadmap.agent.md
	- docs/document-governance.md
	- docs/document-governance-ja.md
	- .github/audit-reports/README.md
	- .github/audit-reports/2026-04-18-agent-driven-docs-maintenance-review.md
---

# Agent-Driven Documentation Maintenance Review

## Confirmed findings
- The current `docs-maintenance-orchestrator` definition includes `edit` and `execute`, which blurs planning and execution responsibilities.
- Existing specialist auditors are read-only, so approved findings cannot be handed to a dedicated execution agent.
- The current governance workflow documents audit planning, but not a durable evidence path for approved findings.
- The current governance workflow does not distinguish audit remediation from maintenance of shared project records such as `CHANGELOG.md` and `ROADMAP.md`.
- Audit evidence guidance under `.github/audit-reports/` does not yet define a required metadata set for maintenance records.

## Approved maintenance design captured here
- Keep `docs-maintenance-orchestrator` as the planning and delegation entry point only.
- Add `docs-maintainer` as the execution role for approved edits.
- Store audit evidence under `.github/audit-reports/`.
- Treat `CHANGELOG.md` and `ROADMAP.md` upkeep as a separate maintenance mode with explicit evidence and approval requirements.
- Add planner-only agents for `CHANGELOG.md` and `ROADMAP.md` preparation, with `docs-maintainer` remaining the only editing agent.
- Standardize required audit-evidence metadata for records stored under `.github/audit-reports/`.

## Changed files
- `.github/agents/docs-orch-maintenance.agent.md`
- `.github/agents/docs-plan-changelog.agent.md`
- `.github/agents/docs-plan-roadmap.agent.md`
- `docs/document-governance.md`
- `docs/document-governance-ja.md`
- `.github/audit-reports/README.md`
- `.github/audit-reports/2026-04-18-agent-driven-docs-maintenance-review.md`

## Validation
- confirmed that `docs-maintainer` is the only pulllog-docs agent with `edit` and `execute`
- confirmed that `docs-maintenance-orchestrator` references the new planner agents in records-maintenance flow
- confirmed that the standardized audit-evidence metadata fields are present in this record and documented in `.github/audit-reports/README.md`

## Residual follow-up
- Decide whether future audit evidence should also include a machine-readable companion format.
- Reuse the standardized metadata block for future audit and maintenance evidence records.