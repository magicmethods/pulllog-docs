# PullLog Backend Documentation

The PullLog backend is the **API server** of the PullLog web application, enabling secure communication between the frontend and the PostgreSQL database.  
It is implemented with Laravel and provides RESTful endpoints returning JSON responses that conform to OpenAPI schema definitions.  
For local development and prototyping, a lightweight mock environment based on [MockAPI-PHP](https://github.com/ka215/MockAPI-PHP) is also provided.

---

## Key Features

- API endpoints returning JSON responses
- Token-based authentication per request
- Database persistence and validation
- No UI layer (backend is API-only)
- Responses conform to OpenAPI schema specifications
- Mock environment for rapid prototyping

---

## Technology Stack

- **Language**: PHP 8.3 (dev environment: v8.4.2)
- **Framework**: Laravel 12.20.0
- **Database**: PostgreSQL 14.13 (dev environment: v17.4)
- **Mock Environment**: MockAPI-PHP v1.3.1
- **Image Processing**: Intervention Image v3.11.4 (driver: GD)
- **Mail (dev use)**: Mailtrap
- ~~OpenAPI generator: openapi-generator-cli v7.14.0 (deprecated in favor of contract-first docs)~~

---

## Data Model Summary

- The backend persists user, app, log, stats, auth, and gallery-related data in PostgreSQL.
- The `logs` domain uses partitioning and supporting views for read patterns.
- Detailed schema design, ER documentation, deployment setup, APP_KEY / API_KEY handling, and mock-environment wiring are maintained as canonical technical documents in the backend subproject.

## Canonical Implementation References

- Backend architecture overview: `backend/docs/architecture/overview.md`
- Deployment and rollback procedure: `backend/docs/operations/deploy-and-release.md`
- Service operations overview: `backend/docs/operations/service-operations-overview.md`
- Backend setup, mock environment, and repository-level technical notes: `backend/README.md`

This public document intentionally omits environment-specific setup commands, secret-generation steps, mock endpoint wiring, and deployment configuration details.

---

## License
All rights reserved by **MAGIC METHODS**.

---

## Contribution
Contributions via Pull Requests and Issues are welcome.  
Discussion of designs and specifications is encouraged in Issues/Discussions.

---

## Related Links

- [PullLog Frontend Documentation](./frontend.md)
- [PullLog API Specification](./api-overview.md)
- [Terms of Service](../public/terms.md)  
- [Privacy Policy](../public/privacy.md)

---
