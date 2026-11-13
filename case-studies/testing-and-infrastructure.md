# Build, release and test infrastructure

[Back](../README.md) · Bot Framework · 2022–2024

I updated the authentication-test pipeline to create and clean up user-assigned managed identities, and added four single-tenant app registrations to the setup script. I verified creation and deletion of the resources.

I also replaced the JavaScript SDK's consumer-test script with generated Mocha tests. Each TypeScript version appears as a separate test, making it easier to see which compatibility check failed. The change supports parallel execution and retries for intermittent failures.

PRs: [Authentication-test resources #589](https://github.com/microsoft/BotFramework-FunctionalTests/pull/589) · [Consumer tests #4793](https://github.com/microsoft/botbuilder-js/pull/4793)

## Recovering a legacy build and release

During temporary team-lead coverage, I helped a Microsoft client unblock a release from an older project used by Bot Framework's .NET, JavaScript and Python libraries. The project was unfamiliar and the build environment was difficult to get working.

I took ownership of investigating the Azure DevOps pipeline, fixing environment-related problems, compiling the C++ code and connecting it to Node.js through node-gyp. I had no previous C++ experience, so I learned what was needed to get the build working.

The project was successfully released, helping unblock security remediation for the dependent Bot Framework libraries. The repository is private, so there is no public PR to link here.
