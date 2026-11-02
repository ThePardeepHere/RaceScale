# Idempotency and API reliability

[All scenarios](../README.md) | [Documentation home](../../README.md)

Prevent retries and ambiguous failures from duplicating business operations.

> **Status:** Planned backlog. The links lead to actual GitHub issues, not to implemented source code.

## Scenarios

| ID and issue | Scenario | Bad case | Good case candidate | Principal trade-off |
| --- | --- | --- | --- | --- |
| [I01](https://github.com/ThePardeepHere/RaceScale/issues/22) | Duplicate booking on retry | Repeated POST creates another booking | Scoped key plus saved response or outcome | Key storage, TTL and client contract |
| [I02](https://github.com/ThePardeepHere/RaceScale/issues/23) | Concurrent identical requests | Two first attempts with one key execute together | Atomic key claim and uniqueness | Wait or conflict behavior for in-flight work |
| [I03](https://github.com/ThePardeepHere/RaceScale/issues/24) | Lost response after commit | Server commits, client times out then retries | Persist status and replay known result | Outcome retention and ambiguous in-flight state |
| [I04](https://github.com/ThePardeepHere/RaceScale/issues/25) | Partial workflow failure | One business step finishes and another fails | Explicit state transitions and repair | Eventual consistency and reconciliation cost |
| [I05](https://github.com/ThePardeepHere/RaceScale/issues/26) | Retry storms | All failures are retried without limits | Retry classification, backoff and jitter | Higher response time and bounded abandonment |

## Engineering lens

HTTP retry safety is not the same as exactly-once execution. Define key scope, payload fingerprint, retention, concurrency handling, replay behavior, and failure recovery before claiming idempotency.

## What to record when implementing

For each selected scenario, use the [scenario template](../TEMPLATE.md) to capture the actual failure, root cause, corrected behavior, repeatable verification, and measured evidence. Keep intentionally unsafe code isolated from the standard application path. Update this page with real source and benchmark links only after those artifacts exist.
