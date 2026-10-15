# project_stakeholder

## Purpose

Stakeholders on projects: a partner with a role and a note per project; the partner form
shows the projects in which the partner is a stakeholder.

## Models

- `project.stakeholder.role`: role name (configured under Project > Configuration).
- `project.stakeholder`: `role_id`, `partner_id`, `project_id`, `note`.
- `project.project.stakeholder_ids`, `res.partner.stakeholder_ids` (One2many).

## Rules

- Project managers: full access; project users: read only.
- Roles are shared with `crm_stakeholder` (leads/opportunities).

## Pitfalls

- Not merged in OCA 19.0 yet (PR project#1783); the 20.0 branch is based on that PR.
- 20.0: `BaseCommon` tests run as a basic user, so the test class sets
  `_test_user_groups` to project manager.
- Customer views (e.g. woa_cosin_stakeholder) replace the partner page via
  `//page[field[@name='stakeholder_ids']]`; keep the field name and page structure.
