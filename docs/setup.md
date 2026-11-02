# Local development and setup

[Documentation home](README.md) | [Architecture](architecture.md) | [Roadmap](roadmap.md)

> **Status:** This is the pre-implementation setup contract. The repository has a documented plan, but an executable Django application and Docker Compose configuration have **not** been verified. No application-specific command should be presented as tested yet.

## 1. Prerequisite discovery (STEP-000)

Record these details **before** installing project-specific dependencies or generating files:

| Check | Why it matters | Expected report |
| --- | --- | --- |
| Operating system and shell | Paths and Docker behavior differ by host | Exact OS, shell, native vs WSL if applicable |
| Git and repository | Prevent overwriting existing work | Branch, commit, `git status`, untracked files |
| Python availability | Establish compatible runtime | Installed version and executable path |
| Docker and Compose availability | Support planned local services | Versions, daemon access, resource limits |
| Available memory and disk | Choose optional service profiles safely | Reported limits, not assumptions |
| Existing app configuration | Avoid duplicate scaffolding | Actual requirements, Compose, Django files if present |

Useful **discovery-only** commands, where available:

```bash
git status --short --branch
git remote -v
python --version
docker --version
docker compose version
```

A missing command is a finding, not an instruction to install everything immediately. Check the host platform first. `python` may be `python3` or `py` on some systems.

## 2. Clone the repository

```bash
git clone https://github.com/ThePardeepHere/RaceScale.git
cd RaceScale
git status --short --branch
```

This is a generic Git operation, not proof that an application can run. If you already have local uncommitted work, **do not reclone or overwrite it**. Inspect that checkout instead.

## 3. Target local topology, introduced incrementally

| Milestone | Intended component | Required before adding |
| --- | --- | --- |
| Initial bootstrap | Django, DRF, PostgreSQL | Environment inventory and issue approval |
| First lab lesson | Event/seat model, isolated unsafe reproduction | Seed fixtures and test database safety |
| Scenario explorer | Django template pages | A stable metadata schema |
| Caching | Redis | Baseline correctness and read workload |
| Queue reliability | RabbitMQ and Celery | A real asynchronous scenario |
| Distributed service | FastAPI | Explicit read boundary and contract |
| Load and monitoring | Locust or k6, optional NGINX, metrics stack | Reproducible baseline workload |

**Avoid adding every component to the default Compose configuration.** Optional infrastructure should be introduced with the corresponding scenario and should have an explicit resource budget.

## 4. Planned runtime configuration

When the application bootstrap issue is implemented, it should provide:

- An example environment file (for example `.env.example`) without credentials or live secrets.
- Documented Python and dependency versions, and a reproducible dependency installation method.
- A Compose configuration for the minimum viable services.
- PostgreSQL connection configuration and migration instructions.
- An explicit **development/test database separation** with safeguards against accidental destructive resets.
- Health checks, startup and shutdown commands, and a first successful local smoke test.
- Clear notes for Windows, macOS, or Linux based on the tested environment, not speculation.

Do not commit `.env`, secret tokens, production credentials, `.venv`, or generated benchmark artifacts unless explicitly approved and safe.

## 5. Setup validation gates

Before the README advertises a runnable project, verify and record:

1. Dependencies install from a fresh checkout using documented versions.
2. PostgreSQL starts, application can connect, and migrations succeed on the intended local environment.
3. A health-check or smoke endpoint returns the documented response.
4. An automated test runs against an isolated test database.
5. Services stop and restart without losing required persisted data.
6. Destructive scenario fixtures are confined to disposable lab data.
7. Exact working commands and expected outputs are copied into this document from actual test runs.

The startup commands will be added **only after these checks pass**. Until then, this page is a planning guide, not a quick-start promise.

## 6. Troubleshooting policy

When an environment step fails, report the **exact command, exit code, relevant logs, platform, and versions**. Do not guess or silently replace a failing dependency. Resolve a single issue before changing unrelated infrastructure. Avoid running seed reset, database drop, or cleanup commands against any non-lab database.

Next: [STEP-000: inspect the local environment](https://github.com/ThePardeepHere/RaceScale/issues/1).
