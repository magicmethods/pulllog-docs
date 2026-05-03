# Copilot Instructions — Pulllog Docs

## Scope
These instructions apply to the `pulllog-docs/` workspace.
This repository primarily contains public documentation assets.

## Environment Policy

- Primary local environment: Windows
- Preferred shell on Windows: PowerShell
- Do not assume Python is installed or available.
- Do not default to Python for routine file editing or text processing.

## Command Selection Priority

1. Existing repository scripts (if present)
2. PowerShell commands
3. Node.js one-off scripts
4. Bash only when explicitly required and available
5. Python only if availability is confirmed and clearly justified

## Documentation Editing Rules

- Keep edits scoped to the requested document or section.
- Preserve existing style, heading hierarchy, and terminology.
- Do not publish secrets, internal endpoints, credentials, or private architecture details.
- Keep image/video references relative and valid.
- Prefer small factual fixes over broad rewrites unless explicitly requested.
- For PullLog-wide documentation governance or audit work, consult `docs/document-governance.md` and the custom agents under `.github/agents/` when they exist.

## Review & Validation Rules

- Verify links and file paths after edits.
- If no build/test tooling exists for the changed scope, do not invent heavy validation steps.
- Do not claim a check was performed unless command output confirms it.

## Repository-wide instructions for Playwright E2E operations

### Purpose
This repository uses GitHub Copilot custom agents to design, implement, run, debug, and review Playwright E2E tests.
Always follow the repository E2E architecture and case manifest definitions before making changes.

### Required references
Before working on any E2E task, read these files when they exist:

- `docs/architecture.md` for the public architecture overview
- `../frontend/docs/architecture/e2e-test.md` when the workspace is available and internal architecture alignment is relevant
- `../frontend/e2e/cases/case.schema.json` when the workspace is available and manifest structure details are needed
- public-facing docs under `docs/` that mention frontend architecture, QA, or testing behavior

### General rules
- Use the existing project structure and naming conventions.
- Prefer minimal diffs.
- Do not rewrite unrelated docs.
- Do not publish secrets, passwords, tokens, internal endpoints, or private operational details.
- Keep the public docs high-level, factual, and safe for publication.
- When describing E2E behavior, explain the architecture and public-facing workflow without exposing sensitive implementation detail.

### E2E execution policy
- PullLog E2E tests are manifest-driven.
- The standard default project matrix is PC `chromium`, tablet `ipad-pro-11`, and smartphone `iphone-14`.
- Public docs may mention that shared repository scripts and template-based reporting exist, but should not expose credentials or internal-only setup values.
- If the requested behavior should not be covered by E2E, say so clearly and explain whether it belongs in unit or integration tests.

### Reporting and evidence policy
- Public docs may describe that every E2E execution produces a Markdown report and that successful runs may be archived as PDF evidence.
- Public descriptions may mention the shared template approach and the PullLog-branded default set, but should stay at an architectural level.
- When multiple projects run for the same case, public docs may note that the case report is aggregated across all executed projects and that PDF evidence can include a fixed PC / Tablet / SP comparison table.

### Manifest policy
- Public docs may describe that case manifests are JSON-based and support environment, target, coverage, report, execution, and tag metadata.
- Do not publish sensitive account references or internal-only configuration values.

### Expected workflow
1. Read the relevant public documentation pages.
2. Confirm whether the requested E2E/testing statement belongs in public docs.
3. Update the public-facing explanation with minimal, accurate wording.
4. Verify links and paths after edits.

### Output expectations
- Be explicit about assumptions.
- Distinguish facts from guesses.
- When blocked, report the exact blocker.
- When changing docs, explain what public-facing E2E architecture information was updated and why.

## Terminal & Process Management
- After completing any task in a terminal, always run the `exit` command to close the session.
- Do not leave background processes running after your work is done.
- On Windows, when using Git Bash (bash.exe), be aware that orphaned child processes may remain; always include a cleanup step for lingering processes at the end of a work sequence.

## Cleanup Rules
- After running multiple Git operations or build tasks in succession, consider cleaning up idle Git processes by running:
  `powershell.exe -Command "Get-Process | Where-Object { $_.Name -match 'git-remote-https|ssh-agent' } | Stop-Process -Force"`

## Workspace Root Policy Summary

- This workspace follows the shared root policy in `pulllog/AGENTS.md`.
- On Windows, prefer PowerShell-first workflows.
- Do not assume Python is installed. Avoid Python-based helpers unless availability is confirmed.
- For command selection, prioritize existing repository scripts first.
- Keep edits scoped and validate with the smallest relevant check first.
