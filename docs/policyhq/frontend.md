# Frontend (policyhq-frontend)

The frontend is a React 18 SPA built with Vite and TypeScript.

## Tech stack

- React 18 + React Router
- Vite build pipeline
- MSAL (Azure Entra ID) for authentication
- Axios for API calls
- Lucide icons, Recharts for charts

## Entry points

- App routes: `policyhq-frontend/src/App.tsx`
- MSAL config: `policyhq-frontend/src/config/authConfig.ts`
- API base URL: `policyhq-frontend/src/config/apiConfig.ts`

## Core pages and flows

- Landing and onboarding: `LandingPage`, `StartPage`, `OnboardingPage`
- Policies: list, detail, creation, and draft workflows
- Templates: template list and editor
- Approvals and reviews: approval queue and policy review actions
- Admin tools: business units, users, imports, audit logs, exports, reports

## Role-based routing

Protected routes are enforced by `ProtectedRoute` and match backend roles.
Roles in use:

- SuperAdmin
- ConsultantAdmin
- OrgAdmin
- PolicyAuthor
- PolicyApprover
- OrgUser
- AuditorReadOnly

## Local development

```
cd policyhq-frontend
npm install
npm run dev
```

The frontend expects the API at `VITE_API_BASE_URL` (defaults to `http://localhost:8000/api`).

## Environment variables

- `VITE_API_BASE_URL`: API base URL for the backend
- `VITE_ENTRA_SPA_CLIENT_ID`: Entra SPA app registration client ID
- `VITE_ENTRA_TENANT_ID`: Entra tenant ID
