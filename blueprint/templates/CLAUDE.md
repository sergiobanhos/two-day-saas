# {{NAME}}

Instructions for agents working on this project. Read before any change.

## Source of truth
- `docs/PRD.md`: what the product does and its acceptance criteria. Wins in a conflict.
- `docs/ARCHITECTURE.md`: stack, data, permissions, integrations and decisions.
- `docs/DESIGN.md` + `design/`: visuals, voice and every screen and state. Build what the screens show.
- `docs/epics/`: epics and tasks. Work one task at a time and keep its `status` current.
- `docs/STATUS.md`: current phase, decisions, approvals and open questions.

## How to work
- Make the smallest change that meets the task's "Done when" criteria. Nothing beyond the ask.
- Reuse existing components and patterns before creating new ones.
- New logic gets a test. Run the tests before saying you're done.
- Never mark a task `done` without passing tests and verified criteria.
- Secrets only in `.env` (never in git). Never expose keys to the front end.
- Screens: follow `docs/DESIGN.md`. One primary action per screen, little text, every state (empty, loading, error, success).
- Never move to the next stage without a summary and the person's explicit approval.
- When mentioning files to the person, use clickable links with absolute paths.
- Unsure about a business rule? Ask. Don't invent.

## Commands
<!-- filled in by the foundation task -->
- Run: `…`
- Test: `…`
- Lint/format: `…`
