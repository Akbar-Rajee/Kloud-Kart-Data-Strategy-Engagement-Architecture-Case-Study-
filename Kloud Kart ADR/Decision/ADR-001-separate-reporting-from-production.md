# ADR-001: Use a dedicated reporting environment instead of querying production directly

- **Status:** Accepted
- **Date:** 2026-11-12
- **Decision owner:** Nana

## Context

Monday reporting activity slows the customer-facing website because reporting queries compete for the same database resources used by customers.

Kloud Kart's immediate problem is protecting customer transactions while still supporting business reporting.

## Decision

Reporting workloads will run in a dedicated reporting environment populated from production data rather than querying the production environment directly.

## Alternatives considered

### Alternative A: Continue reporting directly from production

- **How it would work:** Reports execute against the same environment that serves customers.
- **Why it is attractive:** No additional infrastructure cost and no migration effort.
- **Why rejected:** The existing problem already demonstrates that this approach harms customer experience and creates business risk.

### Alternative B: Dedicated reporting environment

- **How it would work:** Reporting queries execute against a separate reporting environment that receives regular data updates.
- **Why it is attractive:** Protects customer transactions while preserving reporting capability.
- **Why rejected:** Not rejected.

## Consequences

- **What this buys:** Stable website performance, reduced operational risk, and predictable reporting.
- **What this costs:** Additional infrastructure, monitoring, and maintenance effort.
- **What it costs the client if I am wrong:** Unnecessary infrastructure expenditure and operational overhead.
- **What would make me revisit this:** Reporting workloads exceed the capacity assumptions used in the design or business requirements demand significantly lower latency.

## What this survives

- Growth in users.
- Growth in reporting volume.
- Additional reporting consumers.