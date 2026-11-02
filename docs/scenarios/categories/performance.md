# Traffic and scaling

[All scenarios](../README.md) | [Documentation home](../../README.md)

Understand saturation, admission control, and measured capacity.

> **Status:** Planned backlog. The links lead to actual GitHub issues, not to implemented source code.

## Scenarios

| ID and issue | Scenario | Bad case | Good case candidate | Principal trade-off |
| --- | --- | --- | --- | --- |
| [P01](https://github.com/ThePardeepHere/RaceScale/issues/48) | Traffic burst overload | API admits more work than it can serve | Rate limiting and load shedding | Some valid requests may be rejected |
| [P02](https://github.com/ThePardeepHere/RaceScale/issues/49) | Single backend bottleneck | One app instance hits process limits | Multiple replicas behind NGINX | Shared services may still saturate |
| [P03](https://github.com/ThePardeepHere/RaceScale/issues/50) | Slow dependency exhaustion | Worker slots wait on slow network calls | Timeouts and bounded concurrency | Fail-fast versus delayed responses |
| [P04](https://github.com/ThePardeepHere/RaceScale/issues/51) | Unbounded payload processing | Oversized input consumes memory or CPU | Payload limits and bounded/streamed processing | Limits exclude some legitimate jobs |
| [P05](https://github.com/ThePardeepHere/RaceScale/issues/52) | Growing-data query slowdown | Endpoint looks fast only on tiny fixtures | Profile and tune data access under growing data | Index/storage cost and query maintenance |

## Engineering lens

A higher request concurrency is not automatically higher throughput. Compare controlled load profiles, p95 and p99 latency, error rate, throughput, database CPU, and hardware constraints. More replicas do not solve a shared database bottleneck.

## What to record when implementing

For each selected scenario, use the [scenario template](../TEMPLATE.md) to capture the actual failure, root cause, corrected behavior, repeatable verification, and measured evidence. Keep intentionally unsafe code isolated from the standard application path. Update this page with real source and benchmark links only after those artifacts exist.
