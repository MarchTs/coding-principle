# Collaboration Process

Define how work flows from idea to production so contributors share expectations and avoid friction.

## Planning and Scope
- Start every sizable change with a short design note capturing goals, constraints, and trade-offs.
- Track work in a shared system (tickets, project board) with clear owners and acceptance criteria.
- Challenge scope creep early. Split work rather than merging risky, sprawling pull requests.

## Branching and Commits
- Keep `main` releasable; branch from the latest `main` for all features and fixes.
- Write focused commits with meaningful messages (`<type>: <summary>` works well). Link to tickets/issues.
- Rebase interactively to tidy a branch before opening a pull request; avoid force-pushing shared branches.

## Code Review
- Submit concise PRs (<400 lines changed when possible) to enable thorough review.
- Provide context: summary, screenshots, test results, and any follow-up tasks.
- Reviewers focus on correctness, maintainability, security, and alignment with these principles.
- Resolve conversations on the PR when the actionable feedback is addressed; avoid off-thread resolutions unless documented.

## Releases
- Automate builds, tests, and deployments where practical.
- Tag releases and maintain a changelog so teams can trace which code is in production.
- Roll back aggressively if a deployment causes regressions; do not patch forward without diagnosis.

## Documentation Hygiene
- Update README files, configuration docs, and runbooks as part of the same change that affects them.
- Capture significant architectural decisions in an ADR and store it near the affected code.
- Share learnings from outages, incidents, or retrospectives—document preventive measures.
