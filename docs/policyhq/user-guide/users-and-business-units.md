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

Columns (required by import):

- `display_name` (string, required)
- `email` (string, required)
- `role` (string, required)
- `business_groups` (string, optional, list of business units; `business_units` is accepted as an alias)

Download the template: `policyhq/user-guide/assets/user-import-template.csv`

### Example CSV

```csv
display_name,email,role,business_groups
Alex Lee,alex.lee@example.com,OrgAdmin,IT;Security
Priya Sharma,priya.sharma@example.com,PolicyAuthor,HR
Mina Choi,mina.choi@example.com,OrgUser,Finance;Procurement
Chris Patel,chris.patel@example.com,PolicyApprover,Compliance
```

### Data types and validation

- `display_name`: required. Use the full name shown in the UI.
- `email`: required and must be valid. Duplicates are updated if updates are allowed.
- `role`: must match one of the allowed roles exactly.
- `business_groups`: list of existing unit names. Separate with `;` or `,`.

### Allowed roles for import

- OrgUser
- PolicyAuthor
- PolicyApprover
- OrgAdmin
- ConsultantAdmin

### Import preview statuses

- Valid: no issues detected
- Warning: row can import but may create new business units or update an existing user
- Error: row cannot import and must be fixed

### Common import options

- Send invites: emails users after import so they can sign in.
- Allow updates: updates existing users instead of rejecting duplicates.

### Business unit creation during import

If the CSV lists a business unit that does not exist, PolicyHQ will create it automatically and assign the user to it. To avoid unintended units, use exact existing names.

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
