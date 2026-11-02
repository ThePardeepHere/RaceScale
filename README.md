# RaceScale

**RaceScale** is an incremental, locally runnable backend engineering lab built around a deliberately small ticket-booking domain. Its purpose is to explain, reproduce, test, and improve real-world failures in concurrency, idempotency, data consistency, caching, background work, distributed services, performance, and reliability.

Every scenario compares a **bad case** with a **good case**. The lesson must explain the problem, root cause, corrective mechanism, guarantees, alternatives, trade-offs, and reproducible verification. A fast implementation is not necessarily a correct implementation.

> **Project status (documentation baseline, 2 November 2026):** Planning and GitHub Issues backlog are established. Django, database schema, service APIs, interactive dashboard, benchmarks, and local Compose stack are **not verified as implemented**. This documentation is a plan, not a working application. The setup instructions below intentionally do not invent application commands.

## Explore the project

| Start here | Purpose |
| --- | --- |
| [Documentation home](docs/README.md) | Clear entry point to all technical documents |
| [Architecture](docs/architecture.md) | How Django, PostgreSQL, and later FastAPI and infrastructure fit together |
| [Local setup](docs/setup.md) | Prerequisites, first-run plan, and setup verification gates |
| [Scenario catalogue](docs/scenarios/README.md) | **46 planned scenarios**, split by category and linked to GitHub Issues |
| [Engineering workflow](docs/workflow.md) | Git branches, PRs, issue workflow, and scope control |
| [Testing and benchmarks](docs/testing.md) | Reproducibility and evidence requirements |
| [Roadmap](docs/roadmap.md) | Incremental development sequence and dependencies |

## Planned architecture

- **Django + Django REST Framework:** Initial API, booking domain, transactions, and scenario catalogue.
- **Django templates (optional HTMX):** Educational dashboard for bad-case/good-case explanation and real test results.
- **PostgreSQL:** Authoritative source of seat and reservation correctness.
- **FastAPI:** Later independent read-focused service to demonstrate service boundaries, async I/O, and failure handling.
- **Redis, RabbitMQ, Celery, NGINX, observability and load-testing tools:** Introduced only when a specific scenario needs them.

The project starts as a **modular Django monolith** and evolves incrementally into a hybrid architecture. The separate FastAPI service is not part of the first milestone. No cloud subscription is required for the intended local experiments.

## First local steps

1. Clone the repository and inspect the existing files.
2. Read [Local setup](docs/setup.md) to check prerequisites, safety requirements, and the planned bootstrap sequence.
3. Read [STEP-000](https://github.com/ThePardeepHere/RaceScale/issues/1). It is a repository and environment **inspection only**.
4. Implement just the selected issue, and document actual setup and testing commands when those implementations exist.

**There is no verified application startup command yet.** Do not assume `docker compose up` or `python manage.py runserver` will work until the corresponding implementation issues have been completed and checked.

## Progress and contribution rules

Use the [GitHub Issues backlog](https://github.com/ThePardeepHere/RaceScale/issues) for task state. Keep changes small, link them to an issue, and update documentation alongside source changes. Scenario documentation must distinguish **planned**, **in progress**, and **verified** work. Never invent test output or performance numbers.

For Codex: follow `PROJECT_BLUEPRINT.md`, then perform only the explicitly selected issue. Do not scaffold the whole system from this README.
