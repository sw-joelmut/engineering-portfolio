# Copilot Studio Client and WebChat integration

[Back to the portfolio](../README.md)

**Focus:** frontend/backend integration, runtime compatibility and developer experience.

**Public work:** Microsoft Agents for JavaScript, 2025.

## Problem

Connecting WebChat to Copilot Studio Client requires more than displaying a UI. The connection must forward activities in both directions, fit WebChat's connection model and support the browser environment without breaking the existing Node.js use case.

## My contribution

I authored the upstream integration PR, adding the client/WebChat connection, browser compilation and a documented sample. The connection forwards outbound WebChat activities to the client and incoming client activities back to WebChat.

## Design choices and constraints

- Provide a DirectLine-like connection through a dedicated creation method, allowing WebChat to use the client without taking over the SDK's internal implementation.
- Add browser builds and the required polyfills and dependencies while preserving the Node.js path.
- Explain sample setup and the redirect-URI requirement for authentication, so the example includes the environment needed to run it.

The work spans Node.js and browser ESM/IIFE configurations. Build and package configuration are part of the integration problem: making one environment work must not silently break another.

## Validation and outcome

The PR reports the WebChat sample working while the console sample continues to work. The result is a reusable connection and documented integration example. It does not establish customer adoption or usage volume, and later follow-up work should not be inferred to have been included in this initial PR.

## Original contribution

[Copilot Studio Client and WebChat #398](https://github.com/microsoft/Agents-for-js/pull/398) — merged June 26, 2025.
