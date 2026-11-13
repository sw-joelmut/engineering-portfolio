# Joel Mut — Selected engineering work

I'm a Senior Software Engineer at SOUTHWORKS, working with Microsoft as a vendor on Bot Framework and Microsoft 365 Agents SDK. Here are a few examples of what I've worked on.

[GitHub](https://github.com/sw-joelmut) · [LinkedIn](https://www.linkedin.com/in/joel-mut/)

## Automating Teams sample migrations

Moving a sample to another SDK involves more than replacing imports. I built a workflow that plans the migration, uses an agent to make the changes, then validates them before publishing a patch for review. The contribution also included seven migrated .NET samples.

I also wrote reusable skills for Bot Framework migrations and production-readiness checks, with documentation and runnable examples.

[Workflow PR](https://github.com/microsoft/Agents/pull/726) · [More detail](case-studies/ai-skills-and-automation.md)

## Fixing storage bugs

I fixed .NET storage issues where stale writes could overwrite newer data, failed initialization prevented retries, and reads could affect stored data. I added 35 regression cases to cover those scenarios.

I also ported Storage V2 from .NET to JavaScript, keeping the existing storage contract as the default so consumers could continue using it.

[Storage fixes PR](https://github.com/microsoft/Agents-for-net/pull/1053) · [More detail](case-studies/storage-correctness.md)

## Updating authentication without forcing API changes

I migrated Bot Framework's .NET authentication internals from ADAL to MSAL while keeping the public interfaces compatible. One legacy dependency had to stay because removing it would have broken those interfaces.

Other authentication work included porting managed identity to JavaScript and refactoring authorization in the Agents SDK.

[MSAL migration PR](https://github.com/microsoft/botbuilder-dotnet/pull/6605) · [More detail](case-studies/authentication-and-compatibility.md)

## Connecting Copilot Studio to WebChat

I added the connection between Copilot Studio Client and WebChat, including activity exchange, browser builds and a sample showing how to configure authentication. I checked that the new WebChat sample worked and that the existing console sample still worked.

[Integration PR](https://github.com/microsoft/Agents-for-js/pull/398) · [More detail](case-studies/webchat-integration.md)

## Other work

- **Tracing and rate limiting:** added a way to filter automatic typing activity from traces and configurable rate-limit rules. Also helped integrate the team's OpenTelemetry work. [Details and PRs](case-studies/observability-and-reliability.md).
- **Test infrastructure:** added setup and cleanup for authentication-test resources, and changed consumer tests to show results separately for each TypeScript version. [Details and PRs](case-studies/testing-and-infrastructure.md).
