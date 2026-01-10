# Architecture Overview

PolicyHQ is split into two major components:

- policyhq-frontend: React + Vite single-page application
- policyhq-backend: FastAPI service with SQLAlchemy, JWT validation, and file export services

## High-level flow

1. Users authenticate via Microsoft Entra ID (SPA uses MSAL).
2. The SPA requests access tokens for the backend API scope.
3. The backend validates JWTs, resolves tenant context, and enforces RBAC.
4. Domain services manage policies, templates, approvals, reporting, and exports.
5. Exports are stored in Azure Blob Storage (or local storage fallback in debug mode).

## Key subsystems

- Authentication: MSAL in the frontend; JWT validation and role mapping in the backend
- Multi-tenancy: Tenant context derived from token claims and database user-org mapping
- Policy generation: Template-based policy generation with optional AI provider
- Exports: PDF/DOCX/ZIP generation and storage with signed URLs
- Email: Pluggable providers (Azure Communication Services, SendGrid, SMTP)
