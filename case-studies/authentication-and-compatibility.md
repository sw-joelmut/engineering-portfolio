# Authentication and compatibility

[Back](../README.md) · Bot Framework / Agents SDK · 2021–2025

I migrated Bot Framework's .NET authentication internals from ADAL to MSAL. The main constraint was keeping existing public interfaces usable. I added replacement extension methods and deprecated the old entry points, but retained one legacy dependency because removing it would break compatibility. I checked the changes with updated tests and functional bots.

I also ported managed identity and single-tenant authentication to JavaScript, including token acquisition, credential factories and tests. The PR documents which host/skill combinations are supported.

Later, I refactored authorization in the JavaScript Agents SDK to separate route authorization, handler management and token operations. That change did require public API changes, which are documented in the PR.

PRs: [MSAL migration #6605](https://github.com/microsoft/botbuilder-dotnet/pull/6605) · [Managed identity #3923](https://github.com/microsoft/botbuilder-js/pull/3923) · [Authorization refactor #650](https://github.com/microsoft/Agents-for-js/pull/650)
