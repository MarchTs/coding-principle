# Engineering Playbook

## Purpose
This playbook complements the `principles/` directory by providing a quick-reference guide for day-to-day execution. Treat it as the operational layer that helps apply the core standards documented elsewhere in this repository.

## Onboarding Checklist
- Review every file in `principles/` and capture open questions.
- Run through the latest project setup script or instructions.
- Pair with an experienced contributor to walk through branching, testing, and release workflows.
- Configure tooling (linters, formatters, test runners) according to `principles/code-style.md` and `principles/testing.md`.

## Delivery Cadence
1. **Plan** — Align on scope, write lightweight design notes, and confirm dependencies.
2. **Build** — Keep pull requests small, reference the applicable principle files in each description, and seek early feedback.
3. **Validate** — Execute automated tests plus any scenario-specific manual checks. Document evidence in the PR.
4. **Release** — Follow the versioning guidance in `wiki/requirement-version.md` and record any deviations.

## Decision Log Expectations
- Capture architectural decisions as ADRs or dated notes referencing affected modules.
- Include context, decision, alternatives considered, and outcomes.
- Store decision logs near the relevant code or in a shared `docs/adr/` directory.

## Incident Handling
1. Declare ownership quickly and set communication channels.
2. Stabilize production first, even if that means temporary mitigations.
3. Start a `wiki/postmortem.md` entry once the incident is understood.
4. Track follow-up tasks to completion and verify they prevent recurrence.
