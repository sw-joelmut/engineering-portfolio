# Teams sample automation and AI skills

[Back](../README.md) · Microsoft Agents · 2026

I built a workflow to move Teams .NET samples to the Agents SDK. It separates planning, implementation and publication: the plan pins the source revisions, an agent applies the changes, and validation runs before a patch is published for review. The migration job has no repository-write credentials.

The contribution included seven migrated samples. I checked the workflow with automated tests and manual runs; the PR records 19 passing automation tests, with the optional live integration test skipped.

I also worked on two reusable skills:

- **Bot Framework migration:** guidance for handlers, state, dialogs, hosting and authentication, including cases that need a rewrite or a decision rather than a direct replacement.
- **Production readiness:** a guide and skill with a runnable JavaScript reference sample covering configuration, identity, persistent state, telemetry, health checks and deployment guidance.

PRs: [Sample workflow #726](https://github.com/microsoft/Agents/pull/726) · [Migration skill #667](https://github.com/microsoft/Agents/pull/667) · [Production guide and skill #710](https://github.com/microsoft/Agents/pull/710)
