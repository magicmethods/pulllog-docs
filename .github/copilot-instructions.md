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

## Review & Validation Rules

- Verify links and file paths after edits.
- If no build/test tooling exists for the changed scope, do not invent heavy validation steps.
- Do not claim a check was performed unless command output confirms it.

## Workspace Root Policy Summary

- This workspace follows the shared root policy in `pulllog/AGENTS.md`.
- On Windows, prefer PowerShell-first workflows.
- Do not assume Python is installed. Avoid Python-based helpers unless availability is confirmed.
- For command selection, prioritize existing repository scripts first.
- Keep edits scoped and validate with the smallest relevant check first.
