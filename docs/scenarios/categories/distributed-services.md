# Distributed services and FastAPI

[All scenarios](../README.md) | [Documentation home](../../README.md)

Explore justified service boundaries and failure isolation after the Django baseline works.

> **Status:** Planned backlog. The links lead to actual GitHub issues, not to implemented source code.

## Scenarios

| ID and issue | Scenario | Bad case | Good case candidate | Principal trade-off |
| --- | --- | --- | --- | --- |
| [S01](https://github.com/ThePardeepHere/RaceScale/issues/43) | Downstream service outage | Django waits indefinitely on FastAPI | Timeout, concurrency limits and fallback | Circuit-breaker tuning and partial availability |
| [S02](https://github.com/ThePardeepHere/RaceScale/issues/44) | Chatty service calls | One request fans out into many remote calls | Batch or aggregate service responses | API coupling and larger payloads |
| [S03](https://github.com/ThePardeepHere/RaceScale/issues/45) | Partial multi-service success | Distributed operation stops midway | Saga states and compensating actions | Eventual consistency and recovery workflow |
| [S04](https://github.com/ThePardeepHere/RaceScale/issues/46) | Blocking in async endpoints | Synchronous I/O blocks event loop | Nonblocking I/O or bounded thread offload | Scheduler and thread pool resource limits |
| [S05](https://github.com/ThePardeepHere/RaceScale/issues/47) | Cross-service duplicated operations | Retries repeat downstream mutations | Operation identifiers and receiver idempotency | Cross-service coordination overhead |

## Engineering lens

FastAPI is a separately deployed service in the target design, not a reason to split every Django app into a microservice. Start with a read-oriented responsibility and an explicit API contract. Avoid two services independently owning writes to the same tables.

## What to record when implementing

For each selected scenario, use the [scenario template](../TEMPLATE.md) to capture the actual failure, root cause, corrected behavior, repeatable verification, and measured evidence. Keep intentionally unsafe code isolated from the standard application path. Update this page with real source and benchmark links only after those artifacts exist.
