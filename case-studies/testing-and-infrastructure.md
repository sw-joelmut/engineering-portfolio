# Making SDK tests easier to run and diagnose

[Back](../README.md) · Bot Framework · 2022–2024

I updated the authentication-test pipeline to create and clean up user-assigned managed identities, and added four single-tenant app registrations to the setup script. I verified creation and deletion of the resources.

I also replaced the JavaScript SDK's consumer-test script with generated Mocha tests. Each TypeScript version appears as a separate test, making it easier to see which compatibility check failed. The change supports parallel execution and retries for intermittent failures.

PRs: [Authentication-test resources #589](https://github.com/microsoft/BotFramework-FunctionalTests/pull/589) · [Consumer tests #4793](https://github.com/microsoft/botbuilder-js/pull/4793)
