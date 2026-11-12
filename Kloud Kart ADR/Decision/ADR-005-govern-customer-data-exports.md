# ADR-005: Govern customer-data exports through a controlled register

- **Status:** Accepted
- **Date:** 2026-11-12
- **Decision owner:** Nana

## Context

Customer information is copied into spreadsheets, exports, and other files throughout the organization. Kloud Kart lacks a complete inventory of where customer data exists.

Under Ghana's Data Protection Act (Act 843), Kloud Kart must be able to locate and respond to customer-data requests, including deletion requests.

Every copy created becomes another place a deletion request must reach.

## Decision

All customer-data exports must be recorded in a controlled register containing owner, purpose, storage location, approval, retention period, and deletion method.

## Alternatives considered

### Alternative A: Department-managed exports

- **How it would work:** Teams manage exported files independently.
- **Why it is attractive:** No additional administrative effort.
- **Why rejected:** Does not provide traceability, accountability, or deletion-response capability.

### Alternative B: Controlled export register

- **How it would work:** Every export is logged, owned, reviewed, and tracked through its lifecycle.
- **Why it is attractive:** Enables governance, traceability, and deletion-response readiness.
- **Why rejected:** Not rejected.

## Consequences

- **What this buys:** Traceability, accountability, auditability, and improved compliance readiness.
- **What this costs:** Additional process and review overhead.
- **What it costs the client if I am wrong:** Administrative effort that may provide limited additional value.
- **What would make me revisit this:** Automated governance tooling provides equivalent accountability and auditability.

## What this survives

- Team growth.
- Increased export activity.
- Customer deletion requests.
- Governance reviews.