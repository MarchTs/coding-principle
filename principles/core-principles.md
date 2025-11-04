# Core Engineering Principles

These values inform every technical decision. When trade-offs arise, use this hierarchy to choose the safer path.

## 1. Deliver Understandable Code
- Optimize for clarity over cleverness; the next engineer should grasp intent quickly.
- Write self-descriptive APIs and keep modules small enough to explain in a short paragraph.
- Prefer explicit data flow and predictable control structures. Hide complexity behind well-named abstractions only after it is proven stable.

## 2. Protect Reliability and Safety
- Treat warnings and edge cases as first-class citizens; handle failure states before polishing features.
- Fail fast where possible, fail safe where necessary, and surface actionable errors.
- Consider security, privacy, and data integrity requirements before introducing new dependencies or architecture.

## 3. Ship in Verifiable Increments
- Scope work into slices that can be reviewed, tested, and rolled back independently.
- Every change must have a testing story (automated, manual, or both) that matches its risk.
- Favor feature flags or configuration toggles for risky releases.

## 4. Keep the Feedback Loop Tight
- Automate feedback (tests, linters, static analysis) and run it locally before merging.
- Document important decisions close to the code so future readers have context.
- Use metrics and monitoring to validate that shipped code behaves as expected.

## 5. Ruthlessly Manage Complexity
- Challenge new dependencies, patterns, or abstractions that add long-term maintenance burden.
- Consolidate duplicate logic, schemas, or configs when practical.
- Remove dead code and deprecated paths as soon as it is safe.

## 6. Empower Collaboration
- Communicate early about risk, uncertainty, and scope changes.
- Keep the main branch release-ready; treat broken builds and failing tests as emergencies.
- Ensure onboarding materials and README files stay accurate—maintenance is a team sport.
