# Phase 3: scope, architecture and draft PRD

Goal: decide **what goes into the MVP** and **how the system is put together**, and record it in a v0 PRD. The person may be non-technical: explain every choice by its effect, not its name.

## 1. Cut the scope (MVP)

List every feature that came up in the conversation and classify it with the person:

| Priority | Meaning |
|---|---|
| **P0** | Without it the product doesn't solve the problem. In the MVP. |
| **P1** | Important, right after launch. |
| **P2** | Someday, maybe. |

Rule of thumb: a healthy MVP has 5 to 12 P0 features. If there are more, push back: "could you launch without this and do it by hand for the first few weeks?"

## 2. Main flows

Write the 3 to 6 end-to-end paths a user takes, e.g. "Customer books → gets confirmation → gets reminder → shows up". They drive the screens in phase 5.

## 3. Stack (technologies)

Ask whether they already have a preference or someone who will maintain the code. If not, **recommend a simple, popular default** and explain it in plain words:

| Situation | Default recommendation | In plain words |
|---|---|---|
| SaaS / web system (default) | Next.js + TypeScript + Tailwind + shadcn/ui · Supabase (database, login, files) · Vercel (hosting) | A modern web app, a ready-made database and login, one-click publishing |
| Must be an installable phone app | Expo (React Native) + Supabase | A real app in the stores, same database |
| Content site / landing page | Astro + Tailwind | Fast, cheap website |
| Local tool that runs on the user's computer | Vite + React + TypeScript served by a small Node process; SQLite | Opens in the browser, data stays on the machine |
| Payments | Stripe (or a local provider when the audience needs local methods, e.g. Pix/boleto in Brazil) | Whoever charges the card for you |
| Transactional e-mail | Resend | The "welcome" and "forgot password" e-mails |
| AI inside the product | Anthropic API (Claude) | The brain behind the smart features |

Before pinning versions, check each tool's current documentation. Never assume versions or prices. Offer at most one alternative per item and record the choice in `docs/STATUS.md`.

## 4. Architecture (`docs/ARCHITECTURE.md`)

Fill the template with:
- **One-picture overview**: a simple text or mermaid diagram (browser → app → database/services).
- **Data entities**: the "things" the system stores (User, Booking, Service…) with main fields and relations, in plain words: "a Salon has many Services".
- **Permissions**: user type × what they can do (from phase 2).
- **Integrations**: payments, e-mail, AI, maps. For each, what it's for and what happens if it goes down.
- **Security and privacy**: login, who sees what, sensitive data, data-protection law when there is personal data, backups.
- **Decisions**: a short list of "we chose X over Y because…".

## 5. Mini PRD (`docs/PRD.md`, mini)

One page, enough to guide the design and nothing more: fill sections 1 to 5 of the template (vision, problem, personas, P0/P1/P2 scope, main flows) plus a one-line list of data entities. Detailed requirements, screen specs and acceptance criteria wait for phase 6, after the screens exist and are approved; writing them now means rewriting them later. Then run the approval gate before going to design.
