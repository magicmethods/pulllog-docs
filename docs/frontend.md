# PullLog Frontend Documentation

The PullLog frontend is the **client-side implementation** of the PullLog web application, designed to record and analyze individual gacha histories.  
It is built with Nuxt.js 3 (SSR) and integrates with the backend API through a secure proxy layer, providing a responsive UI/UX and multilingual support.

---

## Key Features

- Record and manage gacha logs (title, date, number of pulls, highest rarity, spending, tags, etc.)
- Rich UI components based on PrimeVue
- Timezone-aware operations with Luxon
- Statistical visualization with Chart.js (pull counts, spending trends, etc.)
- Type-safe form validation with Zod
- Dark / light theme switching
- Multilingual support (Japanese / English / Chinese)
- Social login with Google (OAuth)
- Authenticated API integration via proxy

---

## Technology Stack

- **Framework**: Nuxt.js v3
- **UI**: PrimeVue v4, TailwindCSS v4, SCSS
- **State Management**: Pinia v3
- **Language**: TypeScript
- **Date/Time Handling**: Luxon
- **Charts**: Chart.js
- **Validation**: Zod
- **Other**: SortableJS, Marked, ESLint, TypeDoc

---

## Architecture Summary

- The frontend uses **Nuxt 3 SSR** and is hosted on **Cloudflare Workers**.
- Browser-originated API traffic is mediated by the **Nuxt (Nitro) API proxy**.
- Type-safe application code, internationalization, validation, and chart rendering are handled inside the frontend subproject.

Detailed implementation choices such as store boundaries, type placement, middleware behavior, runtimeConfig usage, and proxy routing are maintained as canonical technical documentation in the frontend subproject.

## Canonical Implementation References

- Frontend architecture and implementation overview: `frontend/docs/architecture/overview.md`
- Frontend build and deployment procedure: `frontend/docs/operations/deploy-and-build.md`
- API contract source of truth: `contract/api-schema.yaml`

---

## Public E2E Testing Overview

The frontend repository also maintains a **manifest-driven Playwright E2E architecture** for critical user flows.

### Public characteristics
- Standard default device matrix:
  - `chromium` (PC)
  - `ipad-pro-11` (tablet)
  - `iphone-14` (smartphone)
- Case definitions are managed as JSON manifests.
- Every E2E execution produces a Markdown report.
- Successful runs may also be archived as PDF evidence.
- Reporting uses shared templates, including a PullLog-specific template set for branded Japanese output.

### Reporting model
- One case id maps to one logical scenario.
- When multiple projects/devices run for the same case, the generated case report aggregates **all executed project results** into a single report.
- PDF evidence can include a fixed PC / Tablet / Smartphone comparison table while preserving per-project detail sections.

> This public documentation describes the architecture at a high level and intentionally omits credentials, private endpoints, and internal-only operational details.

---

## Related Links

- [PullLog Backend Documentation](./backend.md)
- [PullLog API Specification](./api-overview.md)
- [Terms of Service](../public/terms.md)  
- [Privacy Policy](../public/privacy.md)

---
