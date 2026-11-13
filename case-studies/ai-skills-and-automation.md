# AI skills and Teams sample automation

[Back to the portfolio](../README.md)

**Focus:** agent workflows, reusable skills, validation and developer documentation.

**Public work:** Microsoft Agents, 2026.

## Problem

Migrating a sample between SDKs requires more than changing imports. Handlers, state, authentication, manifests and dependencies must remain coherent. An agent can produce plausible code while overlooking those contracts. Repeated migrations also need a consistent way to plan, validate and review changes.

## My contribution

I authored the upstream pull requests for a Teams-to-Agents .NET sample synchronization workflow, a Bot Framework migration skill, and a JavaScript production-readiness guide and skill. These are related contributions within a collaborative Microsoft open-source project.

The synchronization work combined a frozen migration plan, agent-assisted implementation, validation and patch publication, alongside seven migrated .NET samples. The workflow separates planning, migration and publication into distinct jobs, with plans, patches and diagnostics available as artifacts. [Teams synchronization PR #726](https://github.com/microsoft/Agents/pull/726).

## Design choices and constraints

- **Separate generation from publication.** Validation and patch verification sit between agent-produced changes and repository publication. The migration job is not given repository-write credentials.
- **Make the plan explicit.** Pin the source/base revisions and freeze the migration plan before implementation, so the intended scope can be inspected.
- **Encode repeatable guidance.** The migration skill classifies work as direct migration, rewrite, decision or unsupported, and covers handlers, state, dialogs, hosting and authentication. This makes uncertainty visible instead of assuming every API has a direct replacement.
- **Treat production readiness as an evidence process.** The production skill provides discovery, assessment, implementation, verification and handoff guidance. It does not certify deployment readiness without deployed evidence.

These are the mechanisms implemented in the linked work. They should not be read as a claim that agent execution is a proven security sandbox or that every migration can run unattended.

## Validation and outcome

The original synchronization PR reports 19 passing automation tests, with an opt-in live integration test skipped, plus a successful build and manual workflow exercises. Tests cover aspects of the workflow rather than establishing general correctness for arbitrary generated code.

The migration skill includes a migration map and verification/reporting requirements. The production-readiness work adds an executable reference sample, configuration and identity checks, durable state, telemetry, health probes, and deployment/rollback guidance. These deliverables turn the approach into something another engineer can inspect and use; no measured time-saving or adoption figure is claimed.

## Original contributions

- [Teams sample synchronization #726](https://github.com/microsoft/Agents/pull/726) — merged September 25, 2026.
- [Bot Framework migration skill #667](https://github.com/microsoft/Agents/pull/667) — merged August 20, 2026.
- [Production-readiness guide, skill and samples #710](https://github.com/microsoft/Agents/pull/710) — merged October 28, 2026.
