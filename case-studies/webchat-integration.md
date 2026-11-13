# Connecting Copilot Studio Client to WebChat

[Back](../README.md) · Agents SDK for JavaScript · 2025

I added a connection that sends WebChat activities to Copilot Studio Client and passes the responses back to WebChat. It uses a DirectLine-like interface so WebChat can consume it.

This also needed browser builds, polyfills and package changes while preserving the existing Node.js setup. I added a sample and documented the authentication configuration, including the redirect URI.

I checked both paths: the WebChat sample worked in the browser, and the existing console sample continued to work.

PR: [WebChat integration #398](https://github.com/microsoft/Agents-for-js/pull/398)
