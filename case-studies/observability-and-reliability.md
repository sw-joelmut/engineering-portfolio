# Observability and runtime reliability

[Back to the portfolio](../README.md)

**Focus:** tracing, configurable runtime behavior and integration quality.

**Public work:** Microsoft Agents for JavaScript, 2026.

## Problem

SDK telemetry needs consistent behavior across packages, and users need control over noisy automatic activity. Runtime protection also needs explicit rules for scope, retry behavior and storage failures rather than hard-coded limits.

## My contribution

I integrated a combined OpenTelemetry branch, resolved conflicts and applied loader/type fixes. That integration PR includes work from multiple contributors; I do not claim sole authorship of all instrumentation. Separately, I authored the typing-indicator span and configurable rate-limiting contributions.

## Design choices and constraints

**Preserve trace structure.** A dedicated parent span wraps each automatic typing activity, with adapter and connector spans kept as children. A consumer's sampler can exclude that span and its descendants while retaining other traces. [Typing telemetry #1265](https://github.com/microsoft/Agents-for-js/pull/1265).

**Make limits configurable.** Rate limiting evaluates fixed-window rules before routing. Rules can select activity types, define a scope, override storage and configure behavior when storage fails. Invoke activities receive a 429 response with retry timing. [Rate limiting #1187](https://github.com/microsoft/Agents-for-js/pull/1187).

**Keep integration behavior inspectable.** The combined telemetry work aligns tracing and logging across runtime packages, with dependency/configuration changes and tests. [Telemetry integration #1056](https://github.com/microsoft/Agents-for-js/pull/1056).

## Validation and outcome

Rate-limit tests cover reset behavior, retry timing, rule ordering, filters, storage fallback/failures and invoke responses. The sample demonstrates activity-scoped and conversation-scoped limits. Typing telemetry includes a sampler example and reported trace validation. The combined telemetry PR demonstrates browser and Node.js telemetry in Aspire.

These provide controllable SDK behavior and diagnostic capabilities. No measured telemetry-cost reduction, avoided-outage figure or globally atomic distributed rate-limit guarantee is claimed.

## Original contributions

- [Telemetry integration #1056](https://github.com/microsoft/Agents-for-js/pull/1056) — merged April 23, 2026.
- [Typing telemetry #1265](https://github.com/microsoft/Agents-for-js/pull/1265) — merged August 26, 2026.
- [Rate limiting #1187](https://github.com/microsoft/Agents-for-js/pull/1187) — merged September 28, 2026.
