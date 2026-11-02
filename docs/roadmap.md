# Incremental roadmap

[Documentation home](README.md) | [Local setup](setup.md) | [Development workflow](workflow.md)

RaceScale progresses from **correctness**, to **reliability**, to **performance**, to **distributed operations**. This is a dependency-oriented roadmap, not a schedule or a demand to implement everything.

## Phase gates

| Gate | Selected GitHub tasks | Deliverable | Must not happen yet |
| --- | --- | --- | --- |
| 0. Inspect and document | [STEP-000](https://github.com/ThePardeepHere/RaceScale/issues/1), [STEP-001](https://github.com/ThePardeepHere/RaceScale/issues/2), [STEP-002](https://github.com/ThePardeepHere/RaceScale/issues/3), [STEP-003](https://github.com/ThePardeepHere/RaceScale/issues/4) | Repository baseline and clean Git workflow | Application scaffolding during discovery |
| 1. Minimal local baseline | [STEP-010](https://github.com/ThePardeepHere/RaceScale/issues/5), [STEP-011](https://github.com/ThePardeepHere/RaceScale/issues/6) | Django, DRF, PostgreSQL, smoke tests and CI | FastAPI or queue infrastructure |
| 2. Minimal booking domain | [STEP-020](https://github.com/ThePardeepHere/RaceScale/issues/7), [STEP-021](https://github.com/ThePardeepHere/RaceScale/issues/8) | Simple schema and isolated bad-case reservation | Unsafe routes in default app behavior |
| 3. First verified lesson | [C01](https://github.com/ThePardeepHere/RaceScale/issues/16) | Double-booking reproduction, fix, tests and trade-offs | Unsupported performance claims |
| 4. Explorer | [STEP-030](https://github.com/ThePardeepHere/RaceScale/issues/9) | Read-only metadata-driven scenario dashboard | Fabricated completion badges or run buttons |
| 5. API and DB lessons | [I01](https://github.com/ThePardeepHere/RaceScale/issues/22), [D01](https://github.com/ThePardeepHere/RaceScale/issues/27), others as chosen | Additional independently verified lessons | Bulk implementation of the entire backlog |
| 6. Redis | [INFRA-REDIS](https://github.com/ThePardeepHere/RaceScale/issues/10) | Measurable caching lessons | Redis as booking authority |
| 7. Queue and workers | [INFRA-QUEUE](https://github.com/ThePardeepHere/RaceScale/issues/11) | Duplicate delivery, retries, outbox labs | Claims of exactly-once delivery |
| 8. FastAPI | [INFRA-FASTAPI](https://github.com/ThePardeepHere/RaceScale/issues/12) | Explicit independent service boundary | Shared writable ownership of booking schema |
| 9. Load and telemetry | [INFRA-LOAD](https://github.com/ThePardeepHere/RaceScale/issues/13), [INFRA-OBS](https://github.com/ThePardeepHere/RaceScale/issues/14) | Reproducible comparisons and diagnostics | Imaginary metrics |
| 10. Documentation audit | [DOCS-RELEASE](https://github.com/ThePardeepHere/RaceScale/issues/15) | Verified references and runnable user guide | Calling planned code complete |

## Rule for implementation slices

A selected scenario may require multiple PRs, for example (1) failure reproduction, (2) correction plus tests, (3) benchmarks plus documentation. Only the selected slice is in scope. Prerequisite status should be checked before starting.

## Architecture decision triggers

Add a new dependency only when its scenario provides a clear question that Django and PostgreSQL alone cannot illustrate adequately. Record the decision, alternatives, operational cost, testing requirements, and reason it is preferable in that particular experiment.

The [46-scenario catalogue](scenarios/README.md) is the backlog. It is **not** the build order. The [GitHub Issues list](https://github.com/ThePardeepHere/RaceScale/issues) is the operational source of truth for current tasks.
