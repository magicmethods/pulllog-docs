# <img src="./public/images/pulllog-icon.svg" height="28" width="auto"> PullLog Documentation (Public)

> This repository hosts **public technical documentation** for PullLog.  
> **Source code is private**. Issues & discussions are welcome here.

> Japanese version: [README-ja.md](README-ja.md)

> Terminology policy: PullLog as a whole is called the workspace, and each top-level directory such as `frontend/`, `backend/`, `contract/`, and `pulllog-docs/` is called a subproject. The canonical definition is documented in `docs/workspace-terminology.md`. When referring to VS Code or pnpm features, use their official terminology.

## What is PullLog
PullLog is a web application that **records and analyzes gacha histories** (draw counts, rare drop rates, spending) across multiple titles.

- Frontend: Nuxt 3 (SSR) with an API proxy layer
- Backend: Laravel 12 + PostgreSQL 14
- Infra: Cloudflare Workers + VPS

| ![Demo Video](./public/video/demo-v1.gif "Demo Video") |
|:---:|
| Demo Video |

| ![Application Management](./public/images/gallery-image1.webp "Apps") | ![History Management](./public/images/gallery-image2.webp "History") | ![Stats Viewer](./public/images/gallery-image3.webp "Stats") |
|:---:|:---:|:---:|
| Application Management | History Management  | Stats Viewer |

## Documentation Map
- Workspace terminology: [`docs/workspace-terminology.md`](docs/workspace-terminology.md) / [(Japanese ver.)](docs/workspace-terminology-ja.md)
- Document governance: [`docs/document-governance.md`](docs/document-governance.md) / [(Japanese ver.)](docs/document-governance-ja.md)
- Architecture: [`docs/architecture.md`](docs/architecture.md) / [(Japanese ver.)](docs/architecture-ja.md)
- Frontend: [`docs/frontend.md`](docs/frontend.md) / [(Japanese ver.)](docs/frontend-ja.md)
- Backend: [`docs/backend.md`](docs/backend.md) / [(Japanese ver.)](docs/backend-ja.md)
- API Overview: [`docs/api-overview.md`](docs/api-overview.md) / [(Japanese ver.)](docs/api-overview-ja.md)
- Operations (public info only): [`docs/ops.md`](docs/ops.md) / [(Japanese ver.)](docs/ops-ja.md)
- Terms & Privacy (public ver.): [`public/terms.md`](public/terms.md), [`public/privacy.md`](public/privacy.md)
- Roadmap: [`ROADMAP.md`](ROADMAP.md)
- Changelog (docs-only): [`CHANGELOG.md`](CHANGELOG.md)

> **Note:** Credentials, internal endpoints, and secrets are **never** published.

## Feedback
- 🐞 Bug reports: GitHub [Issues](https://github.com/magicmethods/pulllog-docs/issues)
- 💡 Feature requests: GitHub [Issues](https://github.com/magicmethods/pulllog-docs/issues) / [Discussions](https://github.com/magicmethods/pulllog-docs/discussions)
- 🔐 Security reports: see [`SECURITY.md`](SECURITY.md)

## License
Documentation is published under [**Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)**](https://creativecommons.org/licenses/by-nc/4.0/) unless noted otherwise.

[![CC BY-NC 4.0](https://licensebuttons.net/l/by-nc/4.0/80x15.png)](https://creativecommons.org/licenses/by-nc/4.0/)
