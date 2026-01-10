# Role Matrix

This matrix shows which pages are available to each role in the current UI and API setup.

Legend:
- R = read/view access
- W = create/update/delete access
- A = approve decisions

| Area / Page | OrgUser | PolicyAuthor | PolicyApprover | OrgAdmin | ConsultantAdmin | SuperAdmin | AuditorReadOnly |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Policies to Acknowledge | R | R | R | R | R | R | R |
| Drafts Dashboard | - | R/W | - | - | R | R | - |
| Policies List | - | - | - | R/W | R/W | R/W | - |
| Policy Detail (from lists) | R | R/W | R | R/W | R/W | R/W | R |
| Policies to Approve | - | - | A | - | A | A | - |
| Templates | R | R | - | R | R | R/W | - |
| Org Profile | - | - | - | R/W | R/W | R/W | - |
| Business Units | - | - | - | R/W | R/W | R/W | - |
| Exports | - | - | - | R | R | R | - |
| Reports | - | - | - | R | R | R | R |
| Audit & Logs | - | - | - | R | R | R | R |

Notes:
- `Templates` create/edit/delete is restricted to SuperAdmin.
- `Policies to Approve` is limited to PolicyApprover, ConsultantAdmin, and SuperAdmin.
- AuditorReadOnly access is allowed at the API layer for reports and audit logs; UI visibility may be configured per deployment.
