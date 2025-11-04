# Working With AI Coding Assistants

AI tools extend the team, but they require structure and oversight. Use these guardrails to keep AI contributions aligned with our standards.

## Prepare the AI
- Provide the relevant principle files and current project context in every session.
- State the desired outcome clearly: bug fix, refactor, design feedback, test writing, etc.
- Set explicit quality expectations (tests required? backwards compatibility? performance constraints?).

## During Collaboration
- Ask the AI to explain reasoning or trade-offs for non-trivial suggestions.
- Keep sessions scoped. Reset context when switching features to prevent bleed-over of assumptions.
- Treat generated code as proposals. Review diffs, run tests, and validate behavior before adopting changes.

## Guardrails
- Never paste secrets, proprietary data, or regulated information into AI prompts.
- Keep humans in the review loop; AI cannot approve its own code.
- Reject outputs that contradict the principles in this repository, even if they appear to work.

## Example Prompt Template
```
You are assisting on <project>. Apply the attached coding principles (core, style, testing, process).
Task: <describe goal>.
Constraints: <performance/security requirements>. Provide reasoning, tests, and validation steps.
Identify any conflicts with the principles before proposing a solution.
```

## Continuous Improvement
- Capture successful prompt patterns or lessons learned and add them back to this document.
- When AI output reveals gaps in these principles, update the relevant files and propagate changes downstream.
