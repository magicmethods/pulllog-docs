# Changelog
All notable changes to this repository will be documented in this file.  
This project follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) and adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

> Note: This changelog covers **documentation updates only**.  
> The PullLog service itself evolves separately.

---

## [Unreleased]
### Added
- Initial structure for documentation repository (`README.md`, `docs/architecture.md`, `docs/frontend.md`, etc.)
- Security policy (`SECURITY.md`)
- Public roadmap (`ROADMAP.md`)
- Issue templates for bug reports & feature requests (with security disclaimer)
- Public-facing E2E architecture notes covering the manifest-driven Playwright approach, the standard PC / tablet / smartphone device matrix, and the aggregated Markdown / PDF reporting model
- Documented `docs-maintainer` as the approved execution role and introduced read-only planners for evidence-backed `CHANGELOG.md` and `ROADMAP.md` preparation
- Standardized YAML front matter metadata requirements for reviewable audit and maintenance records under `.github/audit-reports/`

### Changed
- Updated public frontend and architecture documentation to describe template-based E2E reporting and PullLog-branded evidence output at a high level
- Updated the documentation governance and orchestrator workflow so planning remains separate from execution and approved project-record edits route through `docs-maintainer`

### Fixed
- N/A

---

## [0.1.0] - 2025-08-22
### Added
- First public release of PullLog documentation repository
- Initial docs: Architecture overview, Frontend, Backend, Ops, API overview
- License (CC BY-NC 4.0)
