# Testing Strategy

Tests provide confidence that code satisfies requirements today and tomorrow. Balance coverage, relevance, and execution speed using the guidance below.

## Coverage Philosophy
- Every bug fix must include a regression test guarding against recurrence.
- Critical paths (authentication, payments, data migration, etc.) require layered coverage: unit + integration + monitoring.
- Favor deterministic tests. If randomness is essential, seed it and assert within tolerances.

## Test Pyramid
- **Unit tests** validate small pieces of logic; run them on every change and keep them fast (<1s per suite).
- **Integration tests** cover module boundaries, data stores, and network calls. Stub external services unless explicitly testing integrations.
- **End-to-end (E2E) tests** verify user journeys. Limit scope to the highest-value flows and run on CI/CD, not every commit.

## Writing Quality Tests
- Name tests to describe behavior (`does_x_when_y`), not implementation.
- Arrange using AAA (Arrange, Act, Assert) or Given/When/Then conventions; keep setup reusable with fixtures/factories.
- Avoid brittle assertions tied to incidental implementation details.
- Clean up external side effects (files, sockets, database entries) so tests may run in parallel.

## Tooling Expectations
- Keep test dependencies pinned and isolated (virtualenv, venv, npm workspaces, Go modules, etc.).
- Run linting and tests locally before opening a pull request. Automate the same checks in CI.
- Fail builds on flaky tests rather than muting them—investigate and stabilize quickly.

## Monitoring in Production
- Complement automated tests with runtime checks: feature flags, health checks, alerting, and dashboards.
- Instrument key metrics so you can confirm behavior after deploying significant changes.
