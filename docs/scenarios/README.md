# Scenario catalogue

[Documentation home](../README.md) | [Architecture](../architecture.md) | [Scenario template](TEMPLATE.md)

**46 planned scenarios across nine categories.** Each ticket is an engineering task, not a statement that the corresponding code or benchmark exists.

## Categories

| Category | Scenarios | IDs |
| --- | ---: | --- |
| [Concurrency and consistency](categories/concurrency.md) | 6 | `C01` to `C06` |
| [Idempotency and API reliability](categories/idempotency.md) | 5 | `I01` to `I05` |
| [Database performance](categories/database.md) | 5 | `D01` to `D05` |
| [Caching and Redis](categories/caching.md) | 5 | `R01` to `R05` |
| [Messaging and background jobs](categories/messaging.md) | 5 | `Q01` to `Q05` |
| [Distributed services and FastAPI](categories/distributed-services.md) | 5 | `S01` to `S05` |
| [Traffic and scaling](categories/performance.md) | 5 | `P01` to `P05` |
| [Observability and recovery](categories/observability.md) | 5 | `O01` to `O05` |
| [Security and adversarial edges](categories/security.md) | 5 | `X01` to `X05` |

## Progress and navigation

Use the [GitHub Issues backlog](https://github.com/ThePardeepHere/RaceScale/issues) to check current work status, prerequisites, and acceptance criteria. Scenario pages below contain intentionally concise descriptions and link to the corresponding issue.

A planned `scenarios/<ID>-<slug>/` implementation directory will be added only when that scenario begins. The code, experiment, tests, and results should then be linked from its category page and the Django explorer. Until then, **GitHub issue links are the canonical scenario links**.

## What makes a scenario complete?

| Evidence | Required explanation |
| --- | --- |
| Bad case | A reproducible, controlled failure or inefficiency |
| Root cause | Why the failure happens under the specified conditions |
| Good case | Implementation and the correctness or performance guarantee it provides |
| Trade-offs | Contention, memory, latency, complexity, or availability consequences |
| Verification | Tests or benchmark runs with enough context to repeat them |

Use [TEMPLATE.md](TEMPLATE.md) when creating an individual scenario document. For the project-wide incremental rules, see [workflow.md](../workflow.md).
