# PullLog Operations Guide

This document provides a **public overview** of how PullLog is operated and maintained.  
It covers service monitoring, deployment, incident handling, and backup strategies.

---

## Public Operations Summary

- PullLog is operated with separate frontend, backend, and database responsibilities.
- Release, monitoring, backup, and incident-handling procedures are managed in the backend subproject.
- Public communication about incidents or maintenance is handled through the appropriate public channels.

This public document intentionally avoids restating branch strategy, retention values, health-check design, and key-rotation details as canonical policy.

## Canonical References

- Backend service operations overview: `backend/docs/operations/service-operations-overview.md`
- Backend deployment and rollback procedure: `backend/docs/operations/deploy-and-release.md`
- Frontend build and deployment procedure: `frontend/docs/operations/deploy-and-build.md`
- Public security reporting policy: `../SECURITY.md`

## Public-facing Principles

- Service communication is protected with HTTPS.
- Deployment and rollback are controlled through subproject-owned procedures.
- Monitoring, backup, and security operations are maintained as implementation-owned backend documents.

## Incident Communication

- Public incident or maintenance communication may be announced through official channels.
- Security disclosures should follow [SECURITY.md](../SECURITY.md).

---

_Last updated: August 2025_
