# RaceScale

RaceScale is a planned, locally runnable backend engineering lab built around a small event ticket booking system. It will use paired **bad** and **good** implementations to demonstrate common problems in concurrency, data consistency, performance, and operations. Each lesson is intended to include reproducible tests, measured evidence where useful, and an explanation of the fix and its trade-offs.

## Current status

The project is in the planning stage. The Django application, API, dashboard, database setup, and scenarios have **not** been implemented yet. There are no setup or run commands at this stage.

## Planned approach

- Start with Django, Django REST Framework, and PostgreSQL for the ticket booking core.
- Add a simple Django template dashboard for browsing scenarios.
- Build one small, verifiable scenario at a time, beginning with double booking and its prevention.
- Introduce Redis, background workers, FastAPI, load testing, and observability only when a specific scenario needs them.

The database will remain the authoritative source for booking decisions. Any intentionally unsafe example will be isolated for local experiments.

## Development roadmap

1. Establish repository documentation and Git hygiene.
2. Bootstrap a minimal Django and PostgreSQL app with a health check and smoke test.
3. Add event and seat reads, then demonstrate and fix a double booking race.
4. Expand into idempotency, database performance, caching, queues, scaling, and observability through separate lessons.

The detailed project blueprint is currently kept locally at `docs/PROJECT_BLUEPRINT.md` and excluded from Git. This README summarizes its direction; it is not a claim that the planned features already exist.

## Contributing

Keep changes focused on one requested step or scenario. Include tests and evidence for behavior claims, and document assumptions and limitations. No application setup is available yet; setup instructions will be added with the first runnable milestone.
