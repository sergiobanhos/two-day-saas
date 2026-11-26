# Agents: which model, which brief

## Which model for which task

| Task `complexity` | Model | Why |
|---|---|---|
| **simple**: copy, styling, a field, config, a one-off tweak | `haiku` | Fast and cheap; the task is fully specified |
| **medium**: a screen or endpoint following existing patterns | `sonnet` | Great cost/benefit for everyday code |
| **complex**: sets patterns, data, auth, payments, integrations, dense rules, hard bugs | `opus` | Deeper reasoning, less rework where mistakes are expensive |
| **independent review** | another provider if available; otherwise `opus` with clean context | A view not anchored in the implementer's |
| **final epic review** | `opus` | Sees the whole: how the tasks fit together |

Adjustments:
- The **first** task of each layer (first screen, first endpoint, first migration) goes up one level: it sets the pattern the others copy.
- If a `haiku` or `sonnet` agent fails the same task twice, go up one level instead of retrying.
- Use the model names the agent tool accepts in this environment. If it can't choose a model, use the default and carry on.

## Implementer brief

The agent knows only what's in the brief. Always send:

```
You will implement ONE task in the project at <path>.

Task: <paste the whole task from EPIC.md: title, what to do, done when, screens, requirements>

Read first: CLAUDE.md, the relevant parts of docs/ARCHITECTURE.md, docs/DESIGN.md and the linked screens.
Related existing code: <files/patterns you know exist>

Rules:
- Make the smallest change that meets every "Done when" item. Nothing out of scope.
- Reuse existing components and patterns; follow the surrounding code style.
- Screens: match the prototype, with every state (empty, loading, error, success).
- Write or update tests for new logic. Run tests and the linter until they pass.
- Don't commit, push or touch git: I handle that.
- If a product decision or a credential is missing, stop and describe what's missing.

End your reply with: files changed, how you verified (commands and results), each "Done when" item marked ✓/✗, and any doubt or risk.
```

## Reviewer brief

Send the code, not your conclusion:

```
Review a change in the project at <path>. You did not write this code.

Task and criteria: <paste "What to do" and "Done when">
Reference screens: <paths>
Diff: run `git diff <base>...HEAD` (or `git diff` for uncommitted changes).

Look only for real problems:
- an acceptance criterion not met;
- a bug with a concrete scenario (input/state → wrong result);
- security: one user's data visible to another, an exposed secret, unvalidated input;
- risky logic without a test;
- a screen that differs from the prototype, or a missing state.

Format: a list ordered by severity. Each item: [important | nit] · file:line · problem · failure scenario · suggestion.
If nothing important, say "no important problems". Don't rewrite the code.
```

## Final epic review

Same reviewer brief, with the diff of the whole branch against main, the epic's task list, and one extra question: "do the tasks work together? Any duplication, a broken flow between screens, or anything in 'How to test the epic' that fails?"

## What you (the orchestrator) always do

- Run tests and lint yourself after every implementation and every fix.
- Read the diff of the critical parts: data, permissions, payments, migrations.
- Decide what in the review is important; don't apply style suggestions that contradict the project's patterns.
- Give the person one plain-language progress line per task.
