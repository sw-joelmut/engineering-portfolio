# Storage contracts and correctness

[Back to the portfolio](../README.md)

**Focus:** API evolution, persistence semantics, concurrency and regression testing.

**Public work:** Microsoft Bot Framework and Agents SDK, 2023–2026.

## Problem

Storage APIs need precise behavior for missing data, conditional writes, expiry and failures. A successful-looking call can still be wrong if it overwrites newer state, hides a container failure or exposes mutable backing data. Adding a richer contract must also account for applications using the existing interface.

## My contribution

I contributed the .NET-to-JavaScript Storage V2 port and authored upstream fixes for .NET storage concurrency, initialization and isolation defects. Earlier work addressed allowed-type serialization in Bot Framework. These are implementation contributions, not a claim of sole design ownership of all storage providers.

## Design choices and constraints

The JavaScript V2 work introduces keyed operation results, explicit write modes, version conditions and expiry support across Memory, File, Blob and Cosmos providers. V1 remains the default contract, with compatibility helpers where internal consumers need V2. TTL is a V2 write option rather than a change to the V1 write signature. [Storage V2 PR #1272](https://github.com/microsoft/Agents-for-js/pull/1272).

In the .NET correctness work:

- Explicit V2 write options separate versioned behavior from legacy payload ETag semantics.
- Initialization is treated as complete only after successful setup; later operations can retry after a failure.
- Missing items are distinguished from container failures so infrastructure errors are not silently reported as absent data.
- Memory data is cloned before deserialization so failed reads or caller mutations cannot alter stored state.
- Null batches are validated before storage access to avoid partial writes caused by invalid input.

[Storage correctness PR #1053](https://github.com/microsoft/Agents-for-net/pull/1053).

## Validation and outcome

The correctness PR reports 35 regression cases and 187 storage tests passing on each target framework. Reproduction scenarios exercised stale writes, container failures, failed deserialization and invalid batches against MemoryStorage, Azurite and the Cosmos emulator. The reported checks confirm stale writes are rejected, initialization retries succeed and failed reads preserve data.

The JavaScript port reports manual V1/V2 checks for Memory, Blob and Cosmos, including restart, restore and delete scenarios. File storage is part of the implementation but is not asserted to have received the same manual exercise. These are validation results, not production incident-reduction metrics.

## Original contributions

- [JavaScript Storage V2 #1272](https://github.com/microsoft/Agents-for-js/pull/1272) — merged September 28, 2026.
- [.NET storage correctness #1053](https://github.com/microsoft/Agents-for-net/pull/1053) — merged October 16, 2026.
- [Bot Framework serialization #6585](https://github.com/microsoft/botbuilder-dotnet/pull/6585) — merged February 13, 2023; dynamic loading and validation of allowed types, with updated tests.

Expiry work and the later V2 port are successive stages of the same storage workstream, not separate claims of business impact.
