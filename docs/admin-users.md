---
title: Users
description: Manage who has access to Logic AI and their roles.
---

The Users tab lets you manage who has access to Logic AI and what role they have.

## Roles

| Role | Access |
|---|---|
| **User** | Chat interface, standard tools as defined by policy |
| **Admin** | Everything above, plus full admin console access, admin-mode tools, and gateway management |

## Managing Users

- **Add a user** — Search by name or email and assign a role. This assigns the appropriate permission set automatically.
- **Remove a user** — Revokes their permission set. They will no longer see the Logic AI component or be able to chat.
- **Change role** — Promote a User to Admin or demote an Admin to User.

## Notes

- The installing admin is automatically assigned the Admin role during package installation
- Removing a user does not delete their chat history or saved memories — it only revokes access
- Users still need appropriate Salesforce object permissions to read/write data through Logic AI. Logic AI enforces sharing rules and field-level security on every operation.
