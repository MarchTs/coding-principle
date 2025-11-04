# Code Style and Readability

Consistent style amplifies velocity. Follow these practices across languages; adapt them per tooling or language norms as needed.

## General Expectations
- Use automated formatters (`prettier`, `black`, `gofmt`, etc.) and keep configs versioned.
- Default to descriptive names. Reserve abbreviations for widely understood terms (e.g., `id`, `URL`).
- Keep functions focused on one responsibility; extract helpers when logic grows past ~20 lines.
- Write comments sparingly; when you do, explain *why* the code exists, not *what* it does.
- Favor immutable data and pure functions where practical to simplify reasoning and testing.
- Limit optional/null/undefined values; validate inputs at module boundaries.

## Function Naming Conventions
- `get*` functions retrieve a single resource and must throw a 404 (or domain-specific not-found error) when the target ID is missing.
- `find*` functions also target a single resource but return `null`/`undefined` when nothing matches; never throw for a simple miss.
- `list*` functions return collections and accept query/filter parameters. Always return a list (possibly empty) and document supported options.

## Error Handling and Logging
- Bubble errors with context; wrap or annotate exceptions so the call site can act.
- Log actionable messages (include identifiers, scope, and impact). Avoid logging secrets or PII.
- Use structured logging formats (JSON or key-value) in production services.

## Documentation
- Maintain a project-level `README` or equivalent with setup, build, and deployment notes.
- Co-locate ADRs (architecture decision records) or mini design docs with the code they describe.
- Keep API contracts (OpenAPI, GraphQL schemas, protobuf definitions) in source control and up to date.

## Language Notes

### JavaScript / TypeScript
- Use TypeScript or JSDoc types for non-trivial modules; keep type definitions narrow and explicit.
- Never disable `eslint` or `tsconfig` rules without documenting the rationale and follow-up.
- Prefer modules (`import` / `export`) over namespace or global patterns.
- Keep async flows linear; avoid nested promises when `async`/`await` can clarify intent.

### Python
- Target Python 3.10+ unless constraints dictate otherwise; document any deviation.
- Adopt `ruff` or `flake8` linting with a minimal, enforced rule set. Treat warnings as errors.
- Type annotate public functions and critical modules; enforce with `mypy` or `pyright`.
- Structure packages with explicit `__init__.py` exports to control surface area.

### Markdown and Documentation
- Keep line width < 100 characters to ease diffing.
- Use ordered lists only when sequence matters; otherwise prefer unordered lists for clarity.
- Link to source or tickets when referencing external context so future readers can investigate.
