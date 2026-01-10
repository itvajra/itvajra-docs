# Authentication and Authorization

PolicyHQ uses Microsoft Entra ID for authentication and JWT access tokens for API authorization.

## Frontend (MSAL)

- MSAL config: `policyhq-frontend/src/config/authConfig.ts`
- Authorization code flow with PKCE
- Token scopes requested:
  - `openid`
  - `profile`
  - `email`
  - `api://policyhq-api/access_as_user`

## Backend (JWT validation)

- Token validation: `policyhq-backend/app/auth/jwt_validator.py`
- Entra config: `policyhq-backend/app/auth/entra_config.py`
- Token validation checks:
  - Signature via JWKS
  - Audience and issuer
  - Expiration
  - Required scope `access_as_user`

## Role-based access control (RBAC)

Roles are resolved in this order:

1. Database role from `UserOrg` mapping
2. Token role claim (`roles`)
3. Fallback to `OrgUser`

Defined roles:

- SuperAdmin
- ConsultantAdmin
- OrgAdmin
- PolicyAuthor
- PolicyApprover
- OrgUser
- AuditorReadOnly

## Tenant context

Tenant context uses:

- `oid` for user ID
- `client_org_id` from token, or the database mapping
- Optional fallback to `DEFAULT_CLIENT_ORG_ID`
