# Tracing and rate limiting

[Back](../README.md) · Agents SDK for JavaScript · 2026

I added a parent span around automatic typing activity so applications can filter those traces without losing the rest of the conversation traces. The change includes a sampler example and trace validation.

I also implemented configurable rate limiting before activity routing. Rules can target activity types or conversation scopes, use custom storage, and define what happens if storage fails. Invoke requests receive a 429 response with retry timing. Tests cover resets, rule ordering, filters, storage failures and responses.

For the broader OpenTelemetry integration, I combined the team's branch, resolved conflicts and fixed loader/type issues. The instrumentation itself includes work from multiple contributors.

PRs: [Typing traces #1265](https://github.com/microsoft/Agents-for-js/pull/1265) · [Rate limiting #1187](https://github.com/microsoft/Agents-for-js/pull/1187) · [Telemetry integration #1056](https://github.com/microsoft/Agents-for-js/pull/1056)

## Troubleshooting a customer's HTTP 504 failures

I helped investigate HTTP 504 failures affecting a Microsoft customer's Bot Framework application under load. I reproduced the failures with root and skill bots in Azure, compared configurations, and traced issues involving connection reuse and SNAT port exhaustion.

The work included HTTP connection settings, fixes to how those settings reached internal services, and a serialization fix to keep connection options out of persisted state. I documented the findings and the SDK and Azure configuration changes for the customer.

Later load-test runs with up to 5,000 simulated clients showed no HTTP 504 errors. One run still hit HTTP 429 rate limits. These were validation runs, rather than a measurement of the customer's production uptime.
