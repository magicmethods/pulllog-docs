# Audit Reports

This directory stores reviewable evidence for agent-driven documentation audits and approved maintenance work.

## Purpose
- preserve the approved finding set behind a documentation change
- leave a durable trail for why a maintenance edit happened
- separate audit evidence from public-facing documentation pages

## Naming convention
- one file per audit or maintenance run
- filename format: `YYYY-MM-DD-short-topic.md`

## Required metadata
- Store the required metadata as YAML front matter at the top of each record.
- `record-id`: stable identifier, normally matching the filename stem without `.md`
- `record-type`: classify the record, for example `audit-review`, `maintenance-run`, or `project-records-maintenance`
- `date`: run date in `YYYY-MM-DD`
- `trigger`: approved request, audit follow-up, or other concrete source
- `acting-agent`: agent responsible for the documented maintenance run
- `status`: controlled value such as `planned`, `instructions-prepared`, `approved`, `applied`, or `superseded`
- `scope`: approved change scope captured by the record
- `exclusions`: explicit out-of-scope items for the run
- `source-records`: YAML list of repo-relative evidence files that this record depends on, or an empty list
- `target-files`: YAML list of repo-relative files that the run planned to change or actually changed, or an empty list

## Metadata conventions
- Keep `record-id` equal to the filename stem unless there is a strong reason not to.
- Use repo-relative paths for `source-records` and `target-files`.
- Use YAML sequences for `source-records` and `target-files`, even when they contain only one item.
- Do not place prose summaries inside front matter values when a short factual phrase is enough.
- If a record supersedes an older one, set `status: superseded` on the older record only when that replacement is confirmed.

## Required contents
- confirmed findings or maintenance basis
- approved maintenance actions
- changed files
- validation result
- residual follow-up

## Record template
```yaml
---
record-id:
record-type:
date:
trigger:
acting-agent:
status:
scope:
exclusions:
source-records: []
target-files: []
---
```

## Boundaries
- do not place secrets, credentials, or private operational detail here
- keep evidence factual and tied to observable file changes or approved plans