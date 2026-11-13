# Tracing and rate limiting

[Back](../README.md) · Agents SDK for JavaScript · 2026

I added a parent span around automatic typing activity so applications can filter those traces without losing the rest of the conversation traces. The change includes a sampler example and trace validation.

I also implemented configurable rate limiting before activity routing. Rules can target activity types or conversation scopes, use custom storage, and define what happens if storage fails. Invoke requests receive a 429 response with retry timing. Tests cover resets, rule ordering, filters, storage failures and responses.

For the broader OpenTelemetry integration, I combined the team's branch, resolved conflicts and fixed loader/type issues. The instrumentation itself includes work from multiple contributors.

PRs: [Typing traces #1265](https://github.com/microsoft/Agents-for-js/pull/1265) · [Rate limiting #1187](https://github.com/microsoft/Agents-for-js/pull/1187) · [Telemetry integration #1056](https://github.com/microsoft/Agents-for-js/pull/1056)
