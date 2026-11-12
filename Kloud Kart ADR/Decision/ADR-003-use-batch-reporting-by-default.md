# ADR-003: Use batch reporting as the default processing model

- **Status:** Accepted
- **Date:** 2026-11-12
- **Decision owner:** Nana

## Context

Stakeholders have expressed interest in real-time reporting. However, the brief provides no evidence that most business decisions require second-by-second information.

The key DE01 question is: What decision changes if data is 10 seconds old instead of 24 hours old?

## Decision

Use daily batch processing for reporting and reserve lower-latency processing only for inventory freshness requirements.

## Alternatives considered

### Alternative A: Full real-time processing

- **How it would work:** Data is continuously processed and continuously available.
- **Why it is attractive:** Maximum freshness.
- **Why rejected:** Increased cost and operational burden without proven business value.

### Alternative B: Daily batch processing with inventory exception

- **How it would work:** Reporting data updates daily while inventory data can update more frequently where required.
- **Why it is attractive:** Aligns cost and complexity with demonstrated business needs.
- **Why rejected:** Not rejected.

## Consequences

- **What this buys:** Lower operational cost, lower support burden, and simpler operations.
- **What this costs:** Most reports will not reflect minute-by-minute changes.
- **What it costs the client if I am wrong:** Important decisions may be delayed by insufficient freshness.
- **What would make me revisit this:** A verified business decision requires data less than one hour old to avoid measurable financial loss.

## What this survives

- Reporting growth.
- Additional departments consuming reports.
- Increased reporting usage.