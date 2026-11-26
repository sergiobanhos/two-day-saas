# two-day-saas

**From idea to a working app in two days, even if you can't code.**

Two [Claude Code](https://claude.com/claude-code) skills that work as a pair:

| Skill | What it does |
|---|---|
| `/blueprint` | Plans with you through a conversation. It covers the idea, the audience, a mini PRD with architecture, the visual direction and every screen in every state. Then it writes the full PRD from the screens and splits the work into epics and tasks. |
| `/build` | Implements one epic at a time. Each task goes to the right model for its complexity (Haiku, Sonnet or Opus). The skill runs the tests, has an independent agent review the work and opens a pull request with simple how-to-test steps. |

Both skills stop at every stage. They show you a short summary, ask whether you want to change anything, and only continue once you explicitly approve. They always give documents as clickable links.

## Install

**Claude Code** (all your projects):

```bash
git clone https://github.com/sergiobanhos/two-day-saas.git
cp -R two-day-saas/blueprint two-day-saas/build ~/.claude/skills/
```

To install for a single project, copy the two folders into `<project>/.claude/skills/` instead.

**Zips:** download them from [Releases](https://github.com/sergiobanhos/two-day-saas/releases).

## Use

1. Open Claude Code in an empty folder and type `/blueprint`. Answer the questions and approve each stage.
2. When planning is complete, type `/build`. It works through the epics in order, one PR per epic.

The skills are written in English, but they talk to you in your own language.

## What it creates

```
CLAUDE.md
docs/  STATUS.md · DISCOVERY.md · PRD.md · ARCHITECTURE.md · DESIGN.md
docs/epics/  README.md · E01-foundation/EPIC.md · …
design/  screens and prototype
```

Tasks use a simple format (`status`, `complexity`, `depends_on`, `screens`, `requirements`). You can keep them as folders or as GitHub Issues.

## License

MIT
