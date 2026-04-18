# PullLog API - Overview

This document provides a high-level overview of the PullLog backend API.  
It explains versioning, authentication, major resource groups, and the relationship to the canonical contract.

> Note  
> The canonical machine-readable specification is maintained in the contract subproject at `contract/api-schema.yaml`.  
> This page intentionally stays high-level and does not restate the full contract.

---

## Public Summary

- PullLog API is versioned and contract-driven.
- Major resource groups include auth, apps, logs, stats, user, and gallery.
- The official frontend mediates normal browser access through a server-side proxy.

This public page intentionally remains concise. Human-readable route summaries and contract maintenance guidance are maintained in the contract subproject.

## Canonical References

- Human-readable API overview: `contract/docs/api-overview.md`
- Machine-readable source of truth: `contract/api-schema.yaml`
- Contract maintenance workflow: `contract/docs/api-contract-sync-workflow.md`

## Public Usage Notes

- Use the official frontend for normal browser access.
- Treat `contract/api-schema.yaml` as authoritative for request and response structures.
- Treat the contract subproject docs as authoritative for route grouping and review workflow.

## See Also

- `./backend.md`
- `./frontend.md`

---