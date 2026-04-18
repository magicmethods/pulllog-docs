# PullLog Workspace Terminology

This document is the canonical source for workspace and subproject terminology used across PullLog repositories.

## Standard Terms

- Workspace: the entire PullLog development unit composed of multiple top-level directories such as `frontend/`, `backend/`, `contract/`, and `pulllog-docs/`.
- Subproject: each top-level directory that participates in the PullLog workspace.

## Usage Policy

- In everyday PullLog documentation and development discussions, use `workspace` to mean the whole PullLog development unit.
- Use `subproject` to mean one of the top-level directories inside the workspace.
- Keep this terminology consistent across README files, agent guidance, and internal design notes.

## Exceptions

- When referring to Visual Studio Code features or configuration, use the official VS Code terms `workspace` and `workspace folder` as needed.
- When referring to pnpm behavior or configuration, use the official term `pnpm workspace`.
- When quoting external tools, commands, or documentation, preserve the original terminology even if it differs from PullLog's internal wording.

## Scope

This terminology policy is intended for PullLog repository operations and documentation. It does not replace official terms used by external tools.