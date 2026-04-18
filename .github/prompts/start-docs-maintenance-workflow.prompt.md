---
description: Start the PullLog documentation maintenance workflow from one prompt and route work through the documentation orchestrator
name: Start Docs Maintenance Workflow
argument-hint: Scope or maintenance request, e.g. all docs, README and AGENTS only, public docs only, or records maintenance
agent: docs-orch-maintenance
---

Start the PullLog documentation maintenance workflow for the provided request.

Use `docs-orch-maintenance` as the single entry point and let it delegate governance audit, public-doc review, records planning, and approved maintenance execution as needed.

Required references:
- [Documentation governance](../../docs/document-governance.md)
- [docs-orch-maintenance](../agents/docs-orch-maintenance.agent.md)
- [docs-audit-governance](../agents/docs-audit-governance.agent.md)
- [docs-audit-public](../agents/docs-audit-public.agent.md)
- [docs-plan-changelog](../agents/docs-plan-changelog.agent.md)
- [docs-plan-roadmap](../agents/docs-plan-roadmap.agent.md)
- [docs-impl-maintainer](../agents/docs-impl-maintainer.agent.md)

Instructions:
- Treat the user input as the primary request source unless it explicitly references a stricter source of truth
- Restate the requested scope and explicit exclusions first
- Start with audit and planning unless the user clearly provides an already approved edit scope
- Keep specialist work behind the orchestrator unless a narrower, expert-only follow-up is explicitly needed
- Preserve source-of-truth boundaries between frontend, backend, contract, and pulllog-docs

Return the result using this structure:

```text
Overall status
-

Governance findings
-

Public docs findings
-

Maintenance plan
-

Evidence / records plan
-

User approval / next step
-
```

User input:

{{input}}