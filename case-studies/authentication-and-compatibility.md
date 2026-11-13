# Authentication and backward compatibility

[Back to the portfolio](../README.md)

**Focus:** cross-language implementation, authentication and API migration trade-offs.

**Public work:** Microsoft Bot Framework and Agents SDK, 2021–2025.

## Problem

Authentication behavior must fit both the identity platform and the SDK's existing public surface. A direct language port may require different token-acquisition mechanisms. Replacing a deprecated library can also break consumers if public constructors or extension points disappear.

## My contribution

I authored upstream contributions porting managed identity and single-tenant authentication to JavaScript, migrating .NET authentication internals from ADAL to MSAL, and refactoring the Agents SDK authorization flow.

## Design choices and constraints

**Cross-language parity.** The JavaScript port introduced credential factories, token acquisition and tests for supported host/skill combinations. It documented unsupported combinations rather than implying that all tenant modes interoperate. [Managed identity PR #3923](https://github.com/microsoft/botbuilder-js/pull/3923).

**Compatibility-preserving migration.** The .NET migration moved internal authentication paths to MSAL, added replacement extension methods and deprecated ADAL-related entry points. One transitive ADAL-related dependency remained because removing it would break the public surface. The result is a compatibility-aware migration, not complete removal of every legacy dependency. [MSAL migration PR #6605](https://github.com/microsoft/botbuilder-dotnet/pull/6605).

**Explicit migration boundaries.** The Agents authorization refactor separates route authorization, active-handler management, public token operations and Azure Bot authorization. Unlike the MSAL migration, this PR explicitly documents breaking changes. It illustrates that avoiding unnecessary breaks and recognizing necessary migration boundaries are both part of SDK work. [Authorization PR #650](https://github.com/microsoft/Agents-for-js/pull/650).

## Validation and outcome

The managed-identity port includes unit tests and a documented host/skill compatibility matrix. The MSAL migration reports updated and new tests plus functional bot validation. The authorization refactor documents tested flows and the public API changes.

These changes establish concrete capabilities and migration behavior. They do not prove every authentication scenario is supported or that no later regression occurred. The earlier authorization proposal #573 closed without merging; #650 is the final merged contribution referenced here, not a second independent achievement.

## Original contributions

- [Managed identity and single-tenant support #3923](https://github.com/microsoft/botbuilder-js/pull/3923) — merged September 27, 2021.
- [ADAL-to-MSAL internal migration #6605](https://github.com/microsoft/botbuilder-dotnet/pull/6605) — merged May 10, 2023.
- [Agents authorization refactor #650](https://github.com/microsoft/Agents-for-js/pull/650) — merged October 15, 2025.
