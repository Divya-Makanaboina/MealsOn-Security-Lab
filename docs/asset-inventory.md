# MealsOn Security Asset Inventory

This inventory describes the proposed security lab.
All data will be fictional.

| Asset | Why it needs protection | Proposed access |
|---|---|---|
| Account identity and session | Misuse could let someone impersonate a user. | User manages their account; server verifies sessions. |
| Order records | Exposure reveals another customer's purchases. | Customer sees their own orders; other roles receive only permitted fields. |
| Delivery address | Exposure reveals a customer's location. | Customer and assigned courier for delivery purposes. |
| Courier assignment | Unauthorized changes could redirect access to deliveries. | Controlled server-side assignment process. |
| Delivery status | Unauthorized updates could falsely mark an order delivered. | Assigned courier updates; customer views. |
| Wearable consent record | Unauthorized changes could permit unwanted data collection. | User manages their own consent; server checks it before syncing. |
| Mock wearable records | Exposure reveals private activity information. | Record owner and authorized processing service. |
| Security audit logs | Alteration could hide unauthorized activity. | Restricted security review; server generates events. |

## Data minimization
- Couriers do not receive wearable records or health goals.
- Customers do not receive other customers' order information.
- Logs exclude passwords, session tokens, full addresses,
  and raw health metrics.

## First-release priorities
1. Protect order ownership.
2. Restrict delivery updates to the assigned courier.
3. Enforce active consent before wearable syncing.
