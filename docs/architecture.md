# Architecture

PullLog is split across **separate domains** for frontend (Nuxt 3 SSR) and backend (Laravel 12 API).  
Sessions are **not** cookie-based across origins; requests are authenticated via **API key & tokens** injected by the SSR **API proxy**.

```mermaid
flowchart LR
  U[User Browser] --> N[Nuxt 3 SSR (Cloudflare Workers)]
  N -- fetch with secret headers --> A[Laravel API (VPS)]
  A -->|JSON| N --> U
  A --- P[(PostgreSQL 14)]
```

## Key Decisions
- **SSR API Proxy:** Hide secrets and add auth headers server-side.
- **CORS-friendly:** No cross-site cookies; stateless API tokens instead.
- **Cloudflare Workers:** Cost-effective SSR & edge caching.


