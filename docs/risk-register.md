# MealsOn Security Risk Register

These risks describe the planned security lab.
Controls are proposed and have not yet been implemented or tested.

| ID | Risk | Potential impact | Proposed control | Verification |
|---|---|---|---|---|---|
| R01 | A customer accesses another customer's order by changing the order ID. | Exposure of purchases and delivery address. | Server-side order ownership check. | Customer B requests A's order; access is denied and no protected fields are returned. |
| R02 | An unassigned courier accesses or updates a delivery. | Address exposure or false delivery information. | Server-side courier assignment check. | Unassigned courier requests access and updates; both are denied. |
| R03 | Wearable syncing continues after consent is revoked. | Unwanted collection of private activity data. | Check current consent before every sync. | Revoke consent, attempt sync, and confirm no new wearable record is created. |
| R04 | The server trusts a client-supplied user ID or role. | Impersonation or elevated permissions. | Derive identity and role from a verified server-side session. | Changing client-supplied identity fields does not grant access. |
| R05 | An allowed response includes unnecessary sensitive fields. | Exposure of addresses or wearable data to support or couriers. | Role-specific response fields. | Inspect response content and confirm restricted fields are absent. |
| R06 | Delivery status skips stages or moves backward. | Incorrect order tracking and unreliable records. | Validate permitted state transitions. | Invalid transitions are denied and stored status remains unchanged. |
| R07 | Security logs contain secrets or unnecessary personal data. | Sensitive information leaks through logs. | Log only approved fields; exclude tokens, passwords, full addresses, and raw health metrics. | Inspect generated events for prohibited content. |

## Priorities
- Implement R04's identity control before trusting ownership checks.
- Implement order ownership, courier assignment, and consent controls.
- Add response filtering, transition validation, and safe logging.

## Status tracking
Each risk starts as: Proposed.
Update it to Implemented when the control exists.
Update it to Tested only when verification evidence is recorded.

## Remaining risk
A proposed control does not reduce risk by itself.
Record test results and limitations before assessing remaining risk.
