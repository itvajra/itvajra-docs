# Data Model

The backend uses SQLAlchemy models in `policyhq-backend/app/models`.

## Core entities

- Organization: tenant root entity
- UserOrg: user-to-organization mapping, role, and business units
- BusinessUnit: org-level business units
- OrgPolicyProfile: org profile settings and metadata
- PolicyTemplate: source templates for policy generation
- Policy: policy metadata and lifecycle state
- PolicyVersion: versioned policy content
- PolicyApproval: approvals and approval history
- ApprovalRequest/Decision: approval workflow entities
- PolicyReview: review history
- PolicyAcknowledgement: end-user acknowledgements
- PolicyExport: export jobs and file metadata
- BulkImportJob: bulk user import tracking
- AuditLog: audit events for changes across entities

## Multi-tenancy

Most entities include `client_org_id` and are scoped by tenant context. API access uses the tenant context to ensure isolation.
