# Joel Mut — Selected engineering work

I'm a Senior Software Engineer at SOUTHWORKS, working with Microsoft as a vendor on Bot Framework and Microsoft 365 Agents SDK. Here are a few examples of what I've worked on.

[GitHub](https://github.com/sw-joelmut) · [LinkedIn](https://www.linkedin.com/in/joel-mut/)

## Keeping Teams samples up to date

The Teams SDK changes frequently, including breaking changes that we need to reflect in our Agents SDK samples. I built an AI-assisted workflow to keep those samples up to date: it plans the changes, applies them, and validates a patch before publishing it for review.

I also wrote reusable skills for Bot Framework migrations and production-readiness checks, with documentation and runnable examples.

[Workflow PR](https://github.com/microsoft/Agents/pull/726) · [More detail](case-studies/ai-skills-and-automation.md)

## Improving storage behavior and flexibility

Storage V2 addresses limitations dating back to Bot Framework, including user-reported ETag conflicts with Blob and Cosmos storage. I ported V2 from .NET to JavaScript, adding more control over writes, version checks and expiry while keeping the existing contract as the default.

Separately, I fixed .NET storage bugs involving stale writes, initialization retries and data isolation, with 35 regression cases.

[Storage V2 PR](https://github.com/microsoft/Agents-for-js/pull/1272) · [Storage fixes PR](https://github.com/microsoft/Agents-for-net/pull/1053) · [More detail](case-studies/storage-correctness.md)

## Updating authentication without forcing API changes

I migrated Bot Framework's .NET authentication internals from ADAL to MSAL while keeping the public interfaces compatible. One legacy dependency had to stay because removing it would have broken those interfaces.

Other authentication work included porting managed identity to JavaScript and refactoring authorization in the Agents SDK.

[MSAL migration PR](https://github.com/microsoft/botbuilder-dotnet/pull/6605) · [More detail](case-studies/authentication-and-compatibility.md)

## Connecting Copilot Studio to WebChat

I added the connection between Copilot Studio Client and WebChat, including activity exchange, browser builds and a sample showing how to configure authentication. I checked that the new WebChat sample worked and that the existing console sample still worked.

[Integration PR](https://github.com/microsoft/Agents-for-js/pull/398) · [More detail](case-studies/webchat-integration.md)

## Troubleshooting production timeouts

I investigated HTTP 504 failures affecting a Microsoft customer's Bot Framework application under load. The work involved connection reuse, Azure networking and SDK configuration fixes. Later validation runs with up to 5,000 simulated clients showed no HTTP 504 errors, although one run hit rate limits.

[Investigation details](case-studies/observability-and-reliability.md#troubleshooting-a-customers-http-504-failures)

## Other work

- **Unblocking a legacy release:** during temporary team-lead coverage, I took ownership of helping restore an unfamiliar project's Azure DevOps build and release process. The work involved environment fixes, compiling C++ and connecting it to Node.js through node-gyp. [Details](case-studies/testing-and-infrastructure.md#recovering-a-legacy-build-and-release).
- **Tracing and rate limiting:** added a way to filter automatic typing activity from traces and configurable rate-limit rules. Also helped integrate the team's OpenTelemetry work. [Details and PRs](case-studies/observability-and-reliability.md).
- **Test infrastructure:** added setup and cleanup for authentication-test resources, and changed consumer tests to show results separately for each TypeScript version. [Details and PRs](case-studies/testing-and-infrastructure.md).
