# Phases 4 and 5: visual direction and every screen

Screens come **after** the conversation and the v0 PRD: first understand the system, then draw it. The screens, in turn, reveal gaps that feed the final PRD.

## Phase 4: visual direction (always ask)

Ask in 2 or 3 rounds, always with options. When the question tool supports previews, show mini-mockups.

1. **Personality**: three named directions, each with a one-line mood. E.g. "Calm clinic (light, teal, lots of air)", "Pro tool (dark, dense, one strong accent)", "Friendly and colorful (round corners, light illustrations)". Derive the options from the personas: Carla, using it on her phone between clients, needs something different from a financial analyst.
2. **Accent color and typography**: 2 or 3 combinations. One accent only; status colors (green/yellow/red) only for state.
3. **Product voice**: how the system "talks" in buttons, errors and empty screens. Give the same message in three different tones.
4. **References** (optional): "Is there an app you find pleasant to use?" Use it as inspiration; never copy another company's brand or layout.

Record everything in `docs/DESIGN.md`: tokens (hex colors, fonts, radii, spacing), voice with ✅/❌ examples and principles. Then run the approval gate.

## Phase 5: generate every screen

### Where to draw
- **Claude Design / artifact canvas available** (an artifact tool with a "Design" type): create one canvas with a page per flow and an artboard per screen/state, linked to each other so Play can navigate. Follow the type's own instructions. Share the canvas link.
- **Otherwise (default in Claude Code)**: a local HTML prototype in `design/prototype/`:
  - `tokens.css` with the DESIGN.md variables and components (button, card, input, pill, skeleton, modal, toast);
  - one `.html` per screen/state, all using `tokens.css`, linked with `<a href>` so it navigates like the real app;
  - `index.html` as a map: flows in columns, title of each screen, link to open it;
  - no frameworks and no build step: it opens with a double click. For many screens, write a small generator (`design/prototype/build.mjs`) with shared layout functions to keep everything consistent.
- Show progress flow by flow and ask for a reaction before the next one, with a clickable link: "I did the sign-up flow (5 screens): [open the map](/abs/path/design/prototype/index.html). Anything bothering you?"

### What to cover: every flow, every state

For each flow in the architecture, draw the happy path **and** each of the states below that applies. This table is the phase checklist:

| State | Question |
|---|---|
| **First time / empty** | What does someone see with no data? Is there a clear call to action? |
| **Loading** | A skeleton shaped like the content, or real steps. Never a made-up percentage. |
| **Filled** | Realistic data from the niche. No lorem ipsum. |
| **Success** | A short confirmation and the next step. |
| **Recoverable error** | What happened, in human words, and the button that fixes it. |
| **Blocked** | Why they can't proceed and what the way out is. |
| **Permission / no access** | For each different user type. |
| **Destructive confirmation** | Delete, cancel, pay. |
| **Offline** | When the audience uses it on a phone on the go. |

Plus the cross-cutting screens: onboarding/first run, login/sign-up/forgot password, settings/profile, billing/plan (for a SaaS) and notifications (if any).

### Quality rules (mandatory)

**Clarity**
- **One primary action per screen**, in the accent color. Everything else is secondary or lives in a menu.
- **Little text.** A short title and at most one supporting line. If a screen needs a paragraph to explain itself, the screen is wrong.
- Build hierarchy with size and space, not boxes and borders.
- Button labels are verb + object: "Book appointment", not "Submit" or "OK".

**Designed for the persona**
- Reread each persona's "Design implication" before each flow and apply it (mobile first, big buttons, high density for pro users…).
- Use the audience's vocabulary, not the developer's ("Clients", not "Records").

**No "made by AI" look.** Avoid:
- purple/blue gradient backgrounds, glows, glassmorphism for no reason;
- emojis as icons; ✨ everywhere; a sparkle icon on everything;
- cards with a colored left border; too many badges and tags;
- the generic hero "Welcome to X, the platform that revolutionizes…";
- marketing copy inside the app; invented numbers and testimonials;
- everything centered, at the same weight and size.

Prefer: a typeface with personality for titles, one accent, white space, real niche data, consistent stroke icons.

**Usability and accessibility**
- AA contrast (4.5:1 for text), touch targets ≥ 44px, visible focus, a label on every field.
- Errors next to the field, saying how to fix them.
- Current state always visible (which step am I on, what's saved).
- Respect reduced motion; keep animations short (150–250ms).

### Closing the phase
List the screens by flow, each with its clickable link, and run the approval gate. Record in `docs/STATUS.md` the gaps the screens revealed (new business rules, missing fields); they go into the final PRD.
