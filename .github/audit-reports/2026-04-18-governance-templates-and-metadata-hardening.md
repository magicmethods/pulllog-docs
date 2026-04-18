---
record-id: 2026-04-18-governance-templates-and-metadata-hardening
record-type: maintenance-run
date: 2026-04-18
trigger: approved follow-up to add operational prompt templates and tighten audit-record metadata for future aggregation
acting-agent: GitHub Copilot
status: applied
scope: add copy-paste operational prompt templates to the governance docs, harden the YAML front matter schema for audit records, and normalize existing April 18 audit records to the stricter schema
exclusions: direct product-document changes outside governance and audit-record policy, frontend, backend, contract, and any new CHANGELOG or ROADMAP planning beyond existing approved records work
source-records:
  - .github/audit-reports/2026-04-18-agent-driven-docs-maintenance-review.md
  - .github/audit-reports/2026-04-18-project-records-planning.md
  - .github/audit-reports/2026-04-18-project-records-maintenance.md
target-files:
  - docs/document-governance.md
  - docs/document-governance-ja.md
  - .github/audit-reports/README.md
  - .github/audit-reports/2026-04-18-agent-driven-docs-maintenance-review.md
  - .github/audit-reports/2026-04-18-project-records-planning.md
  - .github/audit-reports/2026-04-18-project-records-maintenance.md
  - .github/audit-reports/2026-04-18-governance-templates-and-metadata-hardening.md
---

# Governance Templates And Metadata Hardening

## Confirmed maintenance basis
- The governance docs already defined the relevant agents and workflows, but did not yet provide copy-paste operational prompt templates.
- The audit-record policy already used YAML front matter, but the schema was still too loose for future aggregation.
- Existing April 18 records needed to match the stricter schema once it was defined.

## Approved maintenance actions
- Add operational prompt templates for changelog planning, roadmap planning, and project-record maintenance execution.
- Add stricter YAML front matter requirements, including `record-id`, `source-records`, `target-files`, and controlled `status` values.
- Normalize the existing April 18 evidence records to the stricter schema.

## Validation
- verify that the governance docs mention the same prompt-template and metadata rules in English and Japanese
- verify that the normalized April 18 records include the stricter required front matter keys

## Residual follow-up
- If future aggregation becomes necessary, the current schema should be sufficient for a first pass without reformatting the April 18 records again.