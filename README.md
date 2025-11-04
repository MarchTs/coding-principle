# Coding Principles Template

This repository captures the engineering principles, guardrails, and checklists that should travel with every new project. Copy the relevant files into a fresh codebase, share them with collaborators (humans and AI tools), and keep the rules in sync as your standards evolve.

## How to Use This Repository
- Copy the `principles/` directory (or selected files) into a new project to seed its engineering playbook.
- Reference the files when prompting AI assistants so they write and review code according to your expectations.
- Treat the content as living documentation. Update the source of truth here first, then re-sync downstream projects.

## Directory Overview
- `principles/core-principles.md` — high-level values that drive day-to-day decisions.
- `principles/code-style.md` — naming, formatting, and documentation expectations.
- `principles/project-structure.md` — domain-driven layering guide for controllers, facades, logic, services, adapters, and repos.
- `principles/testing.md` — guidance for test strategy, coverage, and tooling.
- `principles/error-handling.md` — canonical error taxonomy and error-code format.
- `principles/process.md` — collaboration workflow, version control, and review etiquette.
- `principles/ai-collaboration.md` — best practices for working alongside AI coding assistants.

## Working With AI Tools
When you involve AI, give it:
1. The specific principle files relevant to the task.
2. Any additional context about the feature, bug, or architectural intent.
3. A request to validate its work against these principles before proposing changes.

Review AI-generated output just like any human contribution—run tests, skim diffs, and enforce the checklists.

## Updating Standards
1. Make changes in this repository.
2. Communicate the update (e.g., through release notes or chat message).
3. Re-distribute the updated files to active projects so they stay aligned.

Keeping a single source here keeps expectations clear and reduces drift across codebases.
