# Storage fixes and the JavaScript V2 port

[Back](../README.md) · Bot Framework / Agents SDK · 2023–2026

I fixed several .NET storage problems: stale writes overwriting newer data, initialization failures preventing retries, and reads exposing or changing stored data. I also made sure container failures were reported as errors instead of looking like missing items, and invalid batches were rejected before any writes.

I added 35 regression cases. The PR records 187 storage tests passing on each target framework, with reproduction checks using MemoryStorage, Azurite and the Cosmos emulator.

In JavaScript, I ported Storage V2 from .NET, including write modes, version checks and expiry across the storage providers. I kept V1 as the default contract and used compatibility helpers where needed. Manual checks covered Memory, Blob and Cosmos storage.

Earlier Bot Framework work addressed loading and validating allowed types during serialization.

PRs: [.NET fixes #1053](https://github.com/microsoft/Agents-for-net/pull/1053) · [JavaScript V2 #1272](https://github.com/microsoft/Agents-for-js/pull/1272) · [Serialization #6585](https://github.com/microsoft/botbuilder-dotnet/pull/6585)
