# Phases 6 and 7: final PRD, epics and tasks

## Phase 6: full PRD, written from the approved screens (`docs/PRD.md`)

Only start after the screens are approved. The screens are now the map of everything the system must do; the full PRD turns them into a precise spec. Work through them systematically:

1. **Inventory**: list every screen and state from the prototype/canvas, grouped by flow, each with its clickable link. Nothing may be skipped.
2. **Flow specs**: for each flow, the end-to-end path step by step (screen → action → next screen), including the branches into error, empty, blocked and permission states.
3. **Screen specs**: for each screen:
   - purpose (one line) and how you get there (entry points);
   - elements and actions (every button, field, link) and what each does;
   - states shown (empty, loading, filled, success, error, blocked, no access) and what triggers each;
   - business rules and validations (limits, formats, what's required);
   - data read and written (entities and fields);
   - who can see or use it (permissions);
   - key microcopy (titles, errors, empty states) in the product voice.
4. **Functional requirements**, numbered (R01…), each with a priority (P0/P1/P2), a **verifiable acceptance criterion** ("when saving a booking at a taken time, the screen shows the conflict and suggests 3 free slots") and the screens it covers.
5. **Traceability check**: every screen maps to at least one requirement and every requirement to at least one screen (or is explicitly non-visual, such as a backup job). Fix gaps or ask about them before closing.

Then complete the rest of the template from the mini PRD and the recorded gaps:
- **Non-functional requirements**: perceived performance, security, accessibility, devices, data-protection law.
- **Success metrics**, as targets to validate and not as promises.
- **Out of scope**, made explicit.
- **Risks and open questions.**

Show a summary of at most 10 lines with a link to the PRD and run the approval gate. Record the approval in `docs/STATUS.md`.

## Phase 7: epics and tasks

### How to split
- An **epic** is something the person can test end to end ("Customer booking"), not a technical layer ("Backend").
- Typical order: E01 Foundation (project, login, base layout, deploy) → epics for the P0 flows in order of value → final epic Launch (payments, e-mails, monitoring, security review).
- Each **task** fits one agent work session (half an hour to two hours) and changes one testable thing.
- Every P0 task tied to a screen links to it, and lists the requirement IDs it delivers. Every P0 requirement must end up in at least one task.

### Task format (the build skill depends on it)

Headings and prose go in the person's language. The **field keys and values below stay exactly as written**, so the build skill can parse them in any language:

```
## T03 · New booking screen
- status: todo
- complexity: medium
- depends_on: T01, T02
- screens: design/prototype/booking-new.html, booking-conflict.html
- requirements: R04, R05

### What to do
Two to five plain lines.

### Done when
- [ ] Verifiable criterion 1
- [ ] Verifiable criterion 2
- [ ] Tests cover the happy path and the time conflict
```

`status`: `todo` · `doing` · `review` · `done` · `blocked`.

**complexity** decides which model implements the task:
- **simple**: a small, well-defined change such as copy, styling, a new field or config. → fast model.
- **medium**: an ordinary screen or endpoint following existing patterns. → default model.
- **complex**: sets a pattern (the first task of each layer), data modeling, login and permissions, payments, integrations, concurrency, migrations, logic with many rules. → strongest model.

When torn between two levels, pick the higher one.

### Where to keep them: ask the person

**Option A: folders** (default; works offline and without an account)
```
docs/epics/
  README.md               ← index: order, dependencies, status of each epic
  E01-foundation/EPIC.md  ← goal, how to test the epic, tasks in the format above
  E02-booking/EPIC.md
```

**Option B: GitHub Issues** (good for tracking in the browser or working with others)
1. Check `gh auth status`. If not logged in, explain how (`gh auth login`) and wait.
2. Ask whether a repository exists. To create one, **confirm first** (public or private?), then `gh repo create <name> --private --source . --push`.
3. Create the labels once: `epic`, `E01`…`Enn`, `complexity:simple|medium|complex`.
4. One issue per epic with the `epic` label. One issue per task with the body in the format above and the epic and complexity labels. In the epic body, a `- [ ] #123` checklist of its tasks.
5. Also keep `docs/epics/README.md` with the index and issue numbers, so the build skill finds everything locally.

Show what will happen before creating anything: "I'll create 6 epics and 31 issues in repository X. OK?" Creating issues is publishing.

### Wrap-up
Update `docs/STATUS.md` to "Planning complete" with the epic order, run the final approval gate and follow the wrap-up in SKILL.md.
