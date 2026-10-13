# MealsOn Security Project Scope

## Objective
Implement and test server-side controls that protect order access,
delivery updates, and wearable-data consent.

## Workflows

| Workflow | Security requirement |
|---|---|
| View an order | Customers can access only their own orders. |
| Update delivery status | Only the courier assigned to an order can update its delivery status. |
| Sync wearable data | Syncing requires active consent. Revoking consent blocks subsequent syncing. |

## Test identities
- Customer A and Customer B, each with their own order.
- Courier A and Courier B, with different delivery assignments.

## Evidence to produce
- A role-and-permission table.
- Automated tests for allowed and denied actions.
- Server-generated audit logs.
- An investigation report referencing test events.

## Out of scope for the first release
- Real payments and deliveries.
- Real wearable integrations.
- AI meal recognition.
- Production deployment and formal compliance assessment.

## Current status
The existing prototype uses browser-local demo data.
Authentication and server-side security controls are not yet implemented.

## Data
All accounts, orders, addresses, and health records will be fictional.
