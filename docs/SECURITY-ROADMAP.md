# Phase 2: MealsOn security portfolio

The front-end prototype demonstrates user workflows. It does not demonstrate secure multi-user access. Build a backend before making security claims.

1. Add supported authentication with server-validated sessions. Never derive identity or role from an editable browser profile selector. Keep credentials and API secrets out of the repository.
2. Move orders, consent and nutrition logs into a database. Scope each query to the authenticated owner. Customers cannot read another customer's order; assigned couriers get minimal delivery fields; support permissions are explicitly defined.
3. Enforce consent before every wearable fetch/write. Revocation stops new collection. Deletion of stored records is a separate workflow.
4. Log minimal server-generated audit events, with event ID, actor, action, resource, outcome and UTC timestamp. Exclude secrets, card data, precise addresses and raw health metrics.
5. Test ownership denial, role denial, unauthenticated requests, consent revocation, and response-field minimization. Verify database side effects and event contents, not only HTTP status.
6. Detect repeated cross-order access denials, unexpected allowed customer-owner mismatches, and allowed sync after consent revocation. Add positive, negative and rolling-time-window boundary cases.
7. Write an incident timeline and risk register tied to test evidence. Map selected outcomes to NIST CSF 2.0, without claiming formal compliance.
8. Integrate payment sandbox only after webhook signature verification and replay/idempotency tests. Treat AI/scanner output as untrusted and verify user-specific retrieval scope.

The prior MealsOn Security Portfolio Guide remains the detailed plan. None of these server controls are implemented in this front-end release.
