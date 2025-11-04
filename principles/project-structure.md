# Project Structure

Adopt a domain-driven layout with six explicit layers. Keep each layer in its own directory and limit cross-layer communication to the flow described below.

- **controller** — entry points (HTTP routes, middleware) that translate external requests into domain calls and shape responses.
- **facade** — validators, orchestration logic, and the selector that chooses which domain logic to execute; this is the only layer controllers call.
- **logic** — pure business rules; no IO or framework code. Functions take validated inputs and return deterministic results while deciding whether to engage services or adapters.
- **service** — domain-oriented orchestration that coordinates data persistence, caching, and cross-service calls.
- **adapter** — external integration layer (third-party APIs, messaging, platform SDKs) that conforms external responses into domain-friendly shapes.
- **repo** — raw database interfaces and query builders (SQL, NoSQL, ORM mappers). Expose primitive operations consumed by the service layer.

## Layer Diagram
```mermaid
graph TD
  controller[controller] --> facade[facade]
  facade --> logic[logic]
  logic --> service[service]
  logic --> adapter[adapter]
  service --> repo[repo]
  adapter --> external[(external systems)]
```

## Dependency Rules
- Controllers may depend only on facades.
- Facades may call only logic.
- Logic may orchestrate services or adapters but stays free of framework code.
- Services depend on repos for persistence and must not call adapters directly.
- Adapters communicate with external systems and feed normalized data back to logic.
- Same-layer modules must not depend on each other; keep boundaries strict to avoid circular coupling.
- Lower layers never reach upward—repos cannot call services, services cannot invoke facades, etc. Enforce this rule via reviews and static analysis.

## Data Model Types
- **entity** — mirrors the database schema exactly, including column names and types. Use entities only within the repo layer or when persisting data.
- **dto** — request/response payload shapes exposed at the edge (controllers, external APIs). Keep them immutable and versioned when contracts change.
- **model** — domain-specific objects tailored to business logic needs. Create models in the logic layer to abstract multiple entities or enrich data for decision making.

Map between these forms explicitly: controllers convert DTOs to models via facades/logic, logic invokes services that translate models to entities for storage, and repos return entities that upstream layers adapt back into models or DTOs as needed.
- Repos interact with databases or query builders; they should expose the minimal surface required by services.

Enforce this dependency direction in reviews and automate boundary checks (lint rules, module boundaries) wherever tooling allows.
