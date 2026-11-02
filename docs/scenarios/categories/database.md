# Database performance

[All scenarios](../README.md) | [Documentation home](../../README.md)

Improve query behavior using evidence from PostgreSQL and realistic data sizes.

> **Status:** Planned backlog. The links lead to actual GitHub issues, not to implemented source code.

## Scenarios

| ID and issue | Scenario | Bad case | Good case candidate | Principal trade-off |
| --- | --- | --- | --- | --- |
| [D01](https://github.com/ThePardeepHere/RaceScale/issues/27) | N+1 ORM queries | Accessing related rows triggers many queries | select_related or prefetch_related | Larger joins and memory use |
| [D02](https://github.com/ThePardeepHere/RaceScale/issues/28) | Missing database indexes | Selective filtering repeatedly scans large tables | Indexes verified with EXPLAIN ANALYZE | Index maintenance and storage overhead |
| [D03](https://github.com/ThePardeepHere/RaceScale/issues/29) | Deep offset pagination | Large OFFSET becomes slow and pages shift | Stable keyset pagination | No arbitrary page jumps |
| [D04](https://github.com/ThePardeepHere/RaceScale/issues/30) | Connection exhaustion | Too many application connections overload PostgreSQL | Connection limits and measured pooling | Pooler mode and session compatibility |
| [D05](https://github.com/ThePardeepHere/RaceScale/issues/31) | Oversized transactions | Big batches cause long locks and expensive rollback | Bounded batch processing with restart semantics | Extra checkpoints and partial-progress recovery |

## Engineering lens

Indexing and pooling are not default wins. Compare query plans, cardinality, write amplification, connection budgets, lock time, and rollback behavior. Never use tiny fixtures to claim production-level speedups.

## What to record when implementing

For each selected scenario, use the [scenario template](../TEMPLATE.md) to capture the actual failure, root cause, corrected behavior, repeatable verification, and measured evidence. Keep intentionally unsafe code isolated from the standard application path. Update this page with real source and benchmark links only after those artifacts exist.
