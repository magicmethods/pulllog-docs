# PullLog Operations Guide

This document provides a **public overview** of how PullLog is operated and maintained.  
It covers service monitoring, deployment, incident handling, and backup strategies.

---

## Hosting & Infrastructure

- **Frontend**: Nuxt 3 app (SSR) hosted on **Cloudflare Workers**  
- **Backend**: Laravel 12 running on VPS (Linux)  
- **Database**: PostgreSQL 14 (partitioned tables for logs)  
- **CDN / DNS**: Cloudflare  
- **Domain**: pulllog.net

All communication is secured via HTTPS (TLS 1.3).

---

## Deployment Strategy

- **Branches**
  - `main`: production-ready code
  - `staging`: staging / mock testing environment

- **Release Process**
  1. Merge into `main`
  2. CI/CD pipeline builds and deploys to production
  3. Staging (`staging`) is updated more frequently for testing

- **Versioning**
  - API is versioned under `/api/v1`
  - Breaking changes trigger new paths (`/api/v2`)

---

## Monitoring & Logging

- **Error Logging**
  - Application logs stored on backend VPS
  - Critical errors trigger alerts

- **Performance Monitoring**
  - Cloudflare analytics for traffic overview
  - Database performance monitored with PostgreSQL statistics

- **Availability**
  - Health check endpoint:  
    `GET https://api.pulllog.net/api/v1/dummy`

---

## Backup Policy

- **Database**
  - Daily logical backups (pg_dump) retained for 30 days
  - Weekly full snapshots retained for 3 months

- **Application**
  - GitHub repositories act as source of truth
  - Assets (avatars, imports) stored on VPS with weekly backups

---

## Incident Response

- **Detection**
  - Errors reported through logs and monitoring
  - Community reports via [GitHub Issues](https://github.com/magicmethods/pulllog-docs/issues)

- **Communication**
  - Minor incidents: status posted on official X account  
  - Security-related: direct reporting by email (`support@pulllog.net`)

- **Resolution**
  - Issues triaged and prioritized
  - Hotfixes deployed to `stable` branch as needed

---

## Maintenance Windows

- Planned updates may cause short downtime (usually < 5 minutes)
- Announcements are made on:
  - [PullLog Official X](https://x.com/pulllog_app)
  - GitHub repository issues

---

## Security Operations

- **Dependencies**: Regularly updated with Dependabot
- **Authentication**: API keys are rotated periodically
- **Data Protection**:
  - Sensitive data encrypted at rest (PostgreSQL)
  - HTTPS enforced on all endpoints

For vulnerability disclosures, please see [SECURITY.md](../SECURITY.md).

---

## Roadmap for Ops Improvements

- Introduce structured status page for uptime transparency
- Automated database failover setup
- Extended monitoring with external services (e.g., UptimeRobot)

---

_Last updated: August 2025_
