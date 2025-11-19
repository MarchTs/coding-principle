# Requirement Versioning Guide

This document explains how to express requirement changes so they stay aligned with the engineering principles and downstream consumers.

## Version Number Format
Use `MAJOR.MINOR.PATCH`:
- **MAJOR** — Incompatible requirement changes, such as new compliance rules or deprecated workflows.
- **MINOR** — Backwards-compatible additions, clarifications, or optional steps.
- **PATCH** — Editorial changes (typos, formatting) that do not alter intent.

Example: `2.3.1` means the third patch to the third minor release of the second major revision.

## Release Workflow
1. Draft the change in the relevant `principles/` document or auxiliary doc.
2. Update this guide with the new version identifier and a summary table entry.
3. Communicate the release to stakeholders and ensure dependent repositories resync.

## Changelog Template
| Version | Date | Author | Summary |
| --- | --- | --- | --- |
| 1.0.0 | YYYY-MM-DD | Owner Name | Initial publication of requirements playbook. |

## Tagging and Distribution
- Tag git commits with `requirements-v<version>` to mark canonical releases.
- When exporting to other repositories, embed the version string in a header or metadata block.
- Record validation evidence (tests, reviews) alongside the tagged commit for future audits.
