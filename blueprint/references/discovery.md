# Phases 1 and 2: idea, problem and target audience

Goal: understand **which pain** the system solves, **for whom** and **why now**, before talking about screens or technology. Ask in the person's language; the examples below are just prompts.

## Phase 1: idea and problem

Open wide: "Tell me the idea the way it lives in your head, even if it's messy." Then go deeper with questions picked from these, one or two at a time, only those not yet answered:

**The problem**
- What annoying situation happens today? Tell me about the last time it happened.
- How do people solve it today (spreadsheet, WhatsApp, another app, nothing)? What's bad about that?
- What happens if nobody solves it? Lost money, time, customers?

**The solution**
- If the system existed tomorrow, what is the first thing someone would do in it?
- What is the "wow" moment, when they realize it was worth it?
- What does it definitely **not** do? (helps cut scope)

**The business** (only when it applies; a personal app or internal tool skips this)
- Who pays? Is it the same person who uses it?
- How does it make money: subscription, usage, fee, one-time, free?
- Is anyone already interested, or is there a waitlist?

**Constraints**
- Deadline? Budget for tools and servers?
- Does it need to work on phone, computer or both?
- Any sensitive data (health, finance, minors)? That changes security and legal requirements (e.g. GDPR/LGPD).

The phase is done when you can write **the problem in one sentence**, **the solution in one sentence** and **the wow moment**. Put all three at the top of `docs/DISCOVERY.md`, then run the approval gate.

If the idea is too big, help find the **core**: "If you could launch only ONE thing from this in two weeks, what would it be?"

## Phase 2: target audience

Goal: know who you are designing for. Screens for a 55-year-old accountant differ from screens for a 17-year-old gamer.

Ask:
- Who uses it day to day? Describe a real person you know.
- Is that person comfortable with technology? Phone or computer? At what moment of the day will they open it?
- Is there more than one kind of user? (e.g. salon owner × customer booking × staff)
- Is the person who decides to buy the same one who uses it?

Write **1 to 3 short personas** in `docs/DISCOVERY.md`:

```
### Persona: Carla, salon owner (primary user)
- Context: 42, three employees, books everything over WhatsApp and a paper notebook.
- Tech: phone all day, computer almost never.
- Wants: stop losing appointments and answering messages at 11pm.
- Fear: "a complicated system I won't know how to use".
- Moment of use: between clients, 2 minutes, one hand.
- Design implication: mobile first, big buttons, no long sign-up.
```

The **Design implication** line is mandatory: it carries the persona all the way to the screens.

Close the phase with a simple table of **user types and what each can do**. It becomes the system's permissions in the architecture.
