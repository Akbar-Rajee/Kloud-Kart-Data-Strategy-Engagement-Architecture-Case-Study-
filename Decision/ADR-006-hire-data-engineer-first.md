# ADR-006: Hire a Data Engineer before an Analytics Engineer

- **Status:** Accepted
- **Date:** 2026-11-12
- **Decision owner:** Nana

## Context

The budget allows only two strategic hires. Kloud Kart must address both unreliable data movement and inconsistent business definitions.

Reliable data movement is a prerequisite for trusted reporting.

## Decision

Hire a Data Engineer first and an Analytics Engineer second.

## Alternatives considered

### Alternative A: Hire an Analytics Engineer first

- **How it would work:** Reporting and business metrics are addressed before improving data movement reliability.
- **Why it is attractive:** Faster reporting improvements.
- **Why rejected:** Does not address the underlying reliability problems that feed reporting.

### Alternative B: Hire a Data Engineer first

- **How it would work:** Reliable movement and storage of data are established before standardizing business metrics.
- **Why it is attractive:** Addresses root causes before downstream reporting issues.
- **Why rejected:** Not rejected.

## Consequences

- **What this buys:** Reliable foundations, reduced rework, and trusted reporting.
- **What this costs:** Some reporting enhancements may arrive later.
- **What it costs the client if I am wrong:** Delayed access to improved business reporting.
- **What would make me revisit this:** Existing staff demonstrate sufficient engineering capability to support the architecture without an additional engineering hire.

## What this survives

- Growth in reporting demand.
- Expansion of reporting consumers.
- Increased governance requirements.