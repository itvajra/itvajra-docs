# Users and Business Units (Admins)

## Manage users

1) Open `Users`.
2) Add users manually or import in bulk.
3) Assign roles and business units.
4) Send invitations if required.

## User data fields

Typical fields you will see or manage on a user:

- Email: unique identifier, lowercased for matching
- Display name: shown in the UI and audit logs
- Role: permission set for the user
- Business units: one or more units the user belongs to
- Status: invited, active, or pending (depends on org workflow)

## Roles and access (summary)

- ConsultantAdmin: admin access for multiple clients
- OrgAdmin: org-level admin access
- PolicyAuthor: create and edit policies
- PolicyApprover: approve or request changes
- OrgUser: acknowledge assigned policies
- AuditorReadOnly: view-only access

## Bulk user import

1) Open `Users` > `Import`.
2) Upload a CSV.
3) Choose options (send invites, allow updates).
4) Review import history and resolve errors.

### CSV format

Use a UTF-8 CSV file with a header row. Required columns depend on your org settings, but the common fields are below.

Columns (recommended):

- `email` (string, required)
- `display_name` (string, optional)
- `role` (string, required)
- `business_units` (string, optional, comma-separated)

### Example CSV

```csv
email,display_name,role,business_units
alex.lee@example.com,Alex Lee,OrgAdmin,IT;Security
priya.sharma@example.com,Priya Sharma,PolicyAuthor,HR
mina.choi@example.com,Mina Choi,OrgUser,Finance;Procurement
auditor@example.com,External Auditor,AuditorReadOnly,
```

### Data types and validation

- `email`: must be a valid email format; duplicates are rejected or updated based on import options.
- `display_name`: free text; use the full name shown in the UI.
- `role`: must match one of the supported roles exactly (case sensitive).
- `business_units`: list of existing unit names. Separate with `;` or `,` (your admin can confirm the delimiter).

### Common import options

- Send invites: emails users after import so they can sign in.
- Allow updates: updates existing users instead of rejecting duplicates.

## Manage business units

1) Open `Business Units`.
2) Create, edit, or retire units.
3) Assign users and policies to the appropriate unit.

## Business unit data

Business units help organize policies and user access. Typical fields:

- Name (string, required)
- Type (string enum): department, division, location, or custom
- Status (enum): active or retired
- Owner (optional): user responsible for the unit

## Business unit tips

- Keep names stable to avoid breaking CSV imports.
- Retire units instead of deleting to preserve history and audits.
