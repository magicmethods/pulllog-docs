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

## Design & Development Principles

### State Management and Responsibility Separation
- Pinia stores are **scoped by responsibility**:
  - `useUserStore`: user authentication and profile
  - `useAppStore`: application metadata
  - `useLogStore`: gacha log retrieval and caching
  - `useStatsStore`: statistical data management
  - `useOptionStore`: user preferences and options
  - `useCsrfStore`: CSRF token handling
  - `useLoaderStore`: global loading state
  - `useCurrencyStore`: currency data management
  - `globalStore`: temporary global values
- Caching is strictly limited. No caching of empty arrays or failed responses.

### Type Safety and Coding Rules
- All code is written in TypeScript.  
- `any` and non-null assertions (`!`) are disallowed in principle.  
- Indentation: **4 spaces**  
- Semicolons: **not required**  
- Types are centralized in `types/` and documented with JSDoc (TypeDoc compatible).

### Date and Internationalization
- Dates are handled strictly as ISO8601 strings or `Date` objects with Luxon.  
- i18n manages locale files, and UI text is referenced exclusively via `t()`.

### Charts
- Chart.js is wrapped in a common component layer.  
- Real-time updates are supported during theme switching.

### Validation
- PrimeVue’s Form component is not used.  
- Validation is implemented exclusively with Zod.

### Styling
- Base styling with TailwindCSS, detailed overrides with SCSS.  
- Avoid in-component scoped styles. Styling is centralized or handled via PassThrough API.

---

## Deployment & Hosting

- The frontend uses **SSR (Server-Side Rendering)** and is hosted on **Cloudflare Workers**.  
- All API requests are routed through the **Nuxt (Nitro) API proxy**, which attaches secrets and forwards to the backend Laravel API.  
- Environment-specific API endpoints are configured via `.env` and `runtimeConfig`.

---

## Related Links

- [PullLog Backend Documentation](./backend.md)
- [PullLog API Specification](../docs/api_overview.md)
- [Terms of Service](../public/docs/terms_en.md)  
- [Privacy Policy](../public/docs/privacy_policy_en.md)

---
