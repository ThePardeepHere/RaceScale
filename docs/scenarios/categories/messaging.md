# Messaging and background jobs

[All scenarios](../README.md) | [Documentation home](../../README.md)

Handle duplicate deliveries, worker crashes, and asynchronous consistency.

> **Status:** Planned backlog. The links lead to actual GitHub issues, not to implemented source code.

## Scenarios

| ID and issue | Scenario | Bad case | Good case candidate | Principal trade-off |
| --- | --- | --- | --- | --- |
| [Q01](https://github.com/ThePardeepHere/RaceScale/issues/38) | Duplicate message delivery | Redelivery repeats a side effect | Idempotent consumer and dedupe key | Inbox storage and concurrency control |
| [Q02](https://github.com/ThePardeepHere/RaceScale/issues/39) | Worker crash during task | Worker dies after partial progress | Durable messaging, safe acknowledgment and retry | Re-execution remains possible |
| [Q03](https://github.com/ThePardeepHere/RaceScale/issues/40) | Poison message | Permanent failures retry forever | Bounded attempts and dead-letter handling | Operational replay and triage policy |
| [Q04](https://github.com/ThePardeepHere/RaceScale/issues/41) | Dual-write failure | DB commit succeeds but publish fails | Transactional outbox with dispatcher | Dispatch lag, outbox cleanup and monitoring |
| [Q05](https://github.com/ThePardeepHere/RaceScale/issues/42) | Queue backlog overload | Producers outrun worker capacity | Backpressure, task limits and queue monitoring | Longer wait or explicit rejection |

## Engineering lens

At-least-once delivery is common. Broker acknowledgments alone cannot prevent duplicate business effects. Make consumers idempotent, define retry boundaries, and use the transactional outbox for the DB-to-broker consistency problem.

## What to record when implementing

For each selected scenario, use the [scenario template](../TEMPLATE.md) to capture the actual failure, root cause, corrected behavior, repeatable verification, and measured evidence. Keep intentionally unsafe code isolated from the standard application path. Update this page with real source and benchmark links only after those artifacts exist.
