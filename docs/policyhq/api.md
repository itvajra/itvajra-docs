# API Overview

The backend exposes a REST API under `/api`. OpenAPI docs are available at `/api/docs`.

## Route groups

- `/api/organization`: org profile and onboarding status
- `/api/orgs/{org_id}/business-units`: business unit management
- `/api/my-policies`: end-user policy assignments and acknowledgements
- `/api/policies`: policy CRUD, workflow, approvals, reviews, versions
- `/api/templates`: policy templates
- `/api/org-policy-profile`: org profile configuration
- `/api/exports`: export jobs and download URLs
- `/api/audit-logs`: audit log reporting
- `/api/reports`: reporting endpoints
- `/api/bulk-import`: bulk import processing
- `/api/users`: user management and onboarding
- `/api/static-exports`: static file serving for local export downloads

## Authentication

All routes require a Bearer token unless explicitly marked public. The SPA acquires tokens via MSAL and sends them as `Authorization: Bearer <token>`.

## Policies API (high level)

Key capabilities exposed under `/api/policies`:

- Create, update, delete, and list policies
- Create and list policy versions
- Submit policies for review and approval
- Batch operations: create, approve, archive, delete, restore
- Approval workflow endpoints for requests and decisions

For exact request/response schemas, use `/api/docs` from a running backend.
