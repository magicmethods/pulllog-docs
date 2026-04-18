# Document Governance

This document defines the PullLog documentation governance model centered on the `pulllog-docs/` subproject.

## Purpose

`pulllog-docs/` is the governance hub for PullLog-wide documentation policy, terminology, and public-documentation review.

This does not make `pulllog-docs/` the source of truth for every technical detail. Each subproject remains responsible for its own implementation-specific documentation.

## Governance model

- `pulllog-docs/` owns shared terminology, public-documentation policy, and cross-subproject documentation audit workflow.
- `frontend/`, `backend/`, and `contract/` own their implementation details, build instructions, and technical source-of-truth documents.
- Cross-subproject fixes should prefer small, reviewable changes and explicit source-of-truth references.

## Agent roster

### `docs-maintenance-orchestrator`
- Entry point for PullLog-wide documentation audit and maintenance planning.
- Delegates specialist reviews and consolidates findings into an approval-ready plan.
- Stops at planning unless the user explicitly asks for edits.
- Does not edit files directly; approved changes are delegated to `docs-maintainer`.

### `docs-governance-auditor`
- Reviews terminology consistency, canonical-reference usage, README and AGENTS drift, and documentation-map freshness.
- Reviews documentation filename consistency, including snake_case versus kebab-case drift when naming should be unified.
- Covers `frontend/`, `backend/`, `contract/`, and `pulllog-docs/`.

### `public-docs-sanitizer`
- Reviews `pulllog-docs/` for publication-risk content, private implementation leakage, and public navigation issues.

### `docs-maintainer`
- Applies approved documentation fixes with minimal diffs after orchestrator approval.
- Archives audit evidence under `.github/audit-reports/` so the review trail remains inspectable.
- Maintains `CHANGELOG.md` and `ROADMAP.md` when project-record upkeep is explicitly requested and the source information is confirmed.

### `docs-changelog-planner`
- Prepares evidence-backed `CHANGELOG.md` maintenance instructions.
- Uses read and search only.
- Does not edit files; `docs-maintainer` remains the only editing agent for project-record updates.

### `docs-roadmap-planner`
- Prepares confirmed `ROADMAP.md` maintenance instructions.
- Uses read and search only.
- Does not edit files; `docs-maintainer` remains the only editing agent for project-record updates.

## Operating workflow

1. Start with `docs-maintenance-orchestrator` when the request spans more than one subproject or needs a maintenance plan.
2. Use `docs-governance-auditor` for terminology, README, AGENTS, index, and canonical-reference checks.
3. Use `public-docs-sanitizer` when the scope includes `pulllog-docs/` public content.
4. Classify outcomes into:
   - safe maintenance candidates
   - human review required
   - out-of-scope items owned by another subproject
5. Store audit evidence in `.github/audit-reports/` when the result needs to remain reviewable, and use the standardized YAML front matter metadata defined in `.github/audit-reports/README.md`.
   The minimum front matter should include a stable `record-id`, controlled `status`, and YAML lists for `source-records` and `target-files`.
6. Only apply edits after explicit user approval or an explicit edit request, and route execution through `docs-maintainer`.

## Maintenance modes

### Audit remediation mode
- Start with `docs-maintenance-orchestrator`.
- Use specialist auditors to gather findings.
- Archive the approved finding set as evidence.
- Delegate the approved edits to `docs-maintainer`.

### Project records maintenance mode
- Use this when the goal is to maintain shared project records such as `CHANGELOG.md` and `ROADMAP.md`, even if no audit is running.
- Start with `docs-maintenance-orchestrator` when prioritization or scope review is needed.
- Use `docs-changelog-planner` to prepare evidence-backed `CHANGELOG.md` instructions.
- Use `docs-roadmap-planner` to prepare confirmed `ROADMAP.md` instructions.
- Use `docs-maintainer` directly only when the update source is already approved and the file targets are clear.
- Keep `docs-maintainer` as the only agent that applies project-record edits.
- Keep roadmap entries forward-looking and confirmed. Keep changelog entries limited to completed, evidence-backed changes.

## Prompt examples

### Orchestrator entry point
Use `docs-maintenance-orchestrator` as the default entry point for workspace-wide reviews.

Example prompts:
- `PullLog workspace 全体の文書監査を開始してください。今回は監査のみで、編集はしないでください。`
- `README と AGENTS に限定して文書監査を開始してください。ファイル名規約の揺れも確認してください。`
- `public docs only の範囲で監査を開始してください。公開リスクの確認を優先してください。`
- `文書監査の結果を整理し、承認後に maintainer へ渡す編集指示まで作ってください。`

### Focused governance audit
Use `docs-governance-auditor` directly when you want a focused cross-subproject audit without orchestration overhead.

Example prompts:
- `workspace / subproject 用語の統一状況と正本参照の抜けを監査してください。編集はまだ不要です。`
- `docs 配下のファイル名がスネークケースとケバブケースで混在していないか確認してください。`
- `README、AGENTS、docs の索引にドリフトがないか確認してください。`

### Public documentation safety review
Use `public-docs-sanitizer` directly when the concern is publication safety within `pulllog-docs/`.

Example prompts:
- `pulllog-docs の公開文書に内部情報や公開不適切な表現がないか確認してください。`
- `README と docs の公開向けナビゲーションに古いリンクがないか確認してください。`
- `public docs が他 subproject の技術正本を不適切に上書きしていないか確認してください。`

### Approved maintenance execution
Use `docs-maintainer` when the approved change set is already clear and you want the edits and evidence retention to be executed.

Example prompts:
- `承認済みの README と document-governance の修正を適用し、証跡も残してください。`
- `監査結果に基づいて CHANGELOG.md と ROADMAP.md を更新してください。根拠のある内容だけ反映してください。`

### Project records planning
Use the planner agents when the records update needs instructions before editing.

Example prompts:
- `CHANGELOG.md に載せるべき完了済み変更を監査証跡から整理してください。編集はまだしないでください。`
- `ROADMAP.md に反映できる確定事項だけを整理し、maintainer 向け指示にしてください。`

## Operational prompt templates

### Changelog planning template
```text
Prepare evidence-backed CHANGELOG maintenance instructions without editing files.
Scope: pulllog-docs only.
Inputs:
- CHANGELOG.md
- relevant approved evidence under .github/audit-reports/
Requirements:
- include completed items only
- exclude roadmap intent, pending plans, and unresolved follow-up
- return maintainer-ready instructions only
```

### Roadmap planning template
```text
Prepare confirmed ROADMAP maintenance instructions without editing files.
Scope: pulllog-docs only.
Inputs:
- ROADMAP.md
- relevant approved evidence under .github/audit-reports/
Requirements:
- include confirmed forward-looking public items only
- exclude completed changes, internal workflow notes, and speculative ideas
- return maintainer-ready instructions only
```

### Records maintenance template
```text
Apply the approved project-record maintenance in pulllog-docs only.
Scope:
- apply only the approved instructions preserved in the named audit report
Requirements:
- edit only approved target files
- preserve source-of-truth boundaries
- create or update an audit evidence record under .github/audit-reports/
- validate the changed files with the smallest relevant check
```

## Expected operator behavior

As a rule, instructing `docs-maintenance-orchestrator` to start a documentation audit is enough for a normal workspace-wide review. The orchestrator should choose the relevant specialist agents, gather their findings, and return a consolidated report. Use the specialist agents directly only when you want to narrow the scope yourself.

When edits are approved, the orchestrator should hand the work to `docs-maintainer` instead of editing directly. This keeps audit, approval, execution, and evidence retention separate.

## Source-of-truth rules

- Workspace terminology: `docs/workspace-terminology.md`
- Public documentation policy: this file and `AGENTS.md`
- Frontend technical implementation: `../frontend/`
- Backend technical implementation: `../backend/`
- API contract: `../contract/api-schema.yaml`

## Boundaries

- Do not let public docs redefine backend, frontend, or contract behavior without evidence from those subprojects.
- Do not expose secrets, internal endpoints, credentials, or private operations in public docs.
- Do not use documentation cleanup as a reason to rewrite unrelated technical content.
- Do not treat roadmap intent as changelog evidence, and do not treat audit suspicion as an approved maintenance instruction.

## Recommended usage

- Use the orchestrator for workspace-wide reviews.
- Use the governance auditor directly for focused drift checks.
- Use the sanitizer directly for publication-readiness reviews.
- Use the changelog planner and roadmap planner for records-maintenance instructions.
- Use the maintainer for approved edits, evidence retention, and confirmed changelog or roadmap upkeep.