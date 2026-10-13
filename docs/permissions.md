# MealsOn Permission Rules

These are planned rules for the security lab.
They are not yet implemented in the prototype.

## Permission matrix

| Action | Customer | Courier | Support agent |
|---|---|---|---|
| View order | Own orders only | Assigned orders; delivery fields only | Order ID and status only |
| View delivery address | Own orders only | Assigned orders only | Denied |
| Update delivery status | Denied | Assigned orders; valid transitions only | Denied |
| Change wearable consent | Own consent only | Denied | Denied |
| Sync mock wearable data | Own account; active consent required | Denied | Denied |
| View wearable records | Own records only | Denied | Denied |
| View security audit logs | Denied | Denied | Denied |

Audit-log review will use a separate restricted security-review
mechanism, outside these application roles.

## Enforcement rules

1. Requests require a server-verified identity.
2. The server determines the user's role.
3. Customer order access requires matching the authenticated
   customer ID to the order's owner.
4. Courier access requires matching the authenticated
   courier ID to the order's assigned courier.
5. Responses contain only fields permitted for that role.
6. Wearable syncing requires active consent at the time
   of each sync.
7. Actions not explicitly allowed are denied by default.
8. Delivery status follows:
   Confirmed → Preparing → On the way → Delivered.
   Skipped or backward transitions are denied.

## Initial test cases

| Test | Expected result |
|---|---|
| Customer A views A's order | Allowed |
| Customer B views A's order | Denied |
| Assigned courier views delivery address | Allowed |
| Unassigned courier views delivery address | Denied |
| Customer updates delivery status | Denied |
| Assigned courier makes the next valid transition | Allowed |
| Assigned courier skips a delivery stage | Denied |
| Support views order ID and status | Allowed; no address returned |
| Customer syncs with active consent | Allowed |
| Customer syncs after revoking consent | Denied; no new wearable record |
| Request has no valid authenticated identity | Denied |
