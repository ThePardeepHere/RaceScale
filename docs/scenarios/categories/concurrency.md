# Concurrency and consistency

[All scenarios](../README.md) | [Documentation home](../../README.md)

Keep shared state correct when requests overlap or workers compete.

> **Status:** Planned backlog. The links lead to actual GitHub issues, not to implemented source code.

## Scenarios

| ID and issue | Scenario | Bad case | Good case candidate | Principal trade-off |
| --- | --- | --- | --- | --- |
| [C01](https://github.com/ThePardeepHere/RaceScale/issues/16) | Double booking | Two overlapping requests both claim the final seat | Row lock or atomic conditional reservation | Lock waits and throughput under contention |
| [C02](https://github.com/ThePardeepHere/RaceScale/issues/17) | Lost updates | One writer silently overwrites another writer | Optimistic concurrency with version checks | Conflicts require a retry or rejection policy |
| [C03](https://github.com/ThePardeepHere/RaceScale/issues/18) | Deadlocks | Transactions obtain locks in opposing order | Consistent lock order and bounded retry | Retry load and transaction complexity |
| [C04](https://github.com/ThePardeepHere/RaceScale/issues/19) | Inventory overselling | Concurrent decrements produce invalid stock | Conditional atomic update plus DB constraint | Simple stock decrement differs from seat selection |
| [C05](https://github.com/ThePardeepHere/RaceScale/issues/20) | Long database transactions | Remote I/O holds locks unnecessarily | Short transactions and follow-up work | Extra workflow states and failure handling |
| [C06](https://github.com/ThePardeepHere/RaceScale/issues/21) | Reservation expiry race | Expiry and confirmation modify same reservation | Conditional state transitions and reconciliation | Background cleanup lag and state-machine complexity |

## Engineering lens

A database lock is not always the best answer. Compare row locking, conditional updates, optimistic version checks, database constraints, and recovery behavior. Measure contention rather than assuming the most serialized approach is optimal.

## What to record when implementing

For each selected scenario, use the [scenario template](../TEMPLATE.md) to capture the actual failure, root cause, corrected behavior, repeatable verification, and measured evidence. Keep intentionally unsafe code isolated from the standard application path. Update this page with real source and benchmark links only after those artifacts exist.
