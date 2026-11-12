# ADR-002: Use a warehouse architecture rather than a lake or lakehouse

- **Status:** Accepted
- **Date:** 2026-11-12
- **Decision owner:** Nana

## Context

Kloud Kart requires trusted reporting, governance, and consistent business metrics. The company has limited budget, limited staffing, and structured operational data.

The primary business problem is trust in reporting, not flexibility for unknown future use cases.

## Decision

Implement a warehouse-based reporting architecture.

## Alternatives considered

### Alternative A: Data lake

- **How it would work:** Store raw data in a flexible repository and apply structure later.
- **Why it is attractive:** Low-cost storage and flexibility.
- **Why rejected:** Places greater governance burden on a small team and increases the risk of poorly governed data assets.

### Alternative B: Lakehouse

- **How it would work:** Combine a data lake and warehouse approach.
- **Why it is attractive:** Supports a wider range of future use cases.
- **Why rejected:** Adds complexity and operational burden that cannot be justified by Kloud Kart's current requirements.

### Alternative C: Warehouse

- **How it would work:** Load governed, structured business data into a reporting platform optimized for trusted reporting.
- **Why it is attractive:** Directly supports consistent reporting and strong governance.
- **Why rejected:** Not rejected.

## Consequences

- **What this buys:** Faster reporting, easier governance, lower support burden, and trusted business metrics.
- **What this costs:** Reduced flexibility if future unstructured-data requirements emerge.
- **What it costs the client if I am wrong:** Future migration work if business requirements change substantially.
- **What would make me revisit this:** More than 30% of analytical workloads require unstructured or semi-structured data that cannot be efficiently supported by the warehouse approach.

## What this survives

- Team growth.
- Reporting growth.
- Governance requirements.
- Moderate increases in data volume.