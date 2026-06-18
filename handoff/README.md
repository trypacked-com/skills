# Packed handoff

Drop-in brief for AI coding agents (Claude Code, Cursor, Zed, …). Two repos, two
roles: the **library** *implements* the design system; **consuming apps**
*compose* it.

```
handoff/
├─ CLAUDE.md                  ← UI LIBRARY: full ruleset (always-on)
├─ AGENTS.md                  ← UI LIBRARY: same rules, generic format
├─ .cursor/rules/…mdc         ← UI LIBRARY: same rules, Cursor native
└─ consuming-project/
   ├─ CLAUDE.md               ← CONSUMING APP: thin "use the lib" rules
   ├─ AGENTS.md               ← CONSUMING APP: same, generic format
   └─ SKILL.md                ← CONSUMING APP: full system, invoked on demand
```

## UI library repo (packed.ui)

This repo *is* the design system, so the rules are **always-on guardrails**.

1. Copy **`CLAUDE.md`** (Claude Code) **or** **`AGENTS.md`** (Cursor/Zed/others)
   **or** the **`.cursor/`** folder (Cursor native) to the repo root — pick one.
2. Install maintainer skills from [trypacked-com/skills](https://github.com/trypacked-com/skills):
   `bunx skills add trypacked-com/skills --skill packed-ui-maintainer --skill packed-design -a cursor -a claude-code -y`
3. Example prompt: *"Read `STYLE_GUIDE.md` and `registry/styles/packed-theme-tokens.css`.
   Map warm sand tokens onto shadcn variables, rounded corners, warm shadows, no cool
   grey ramp. Match components on [ui.trypacked.dev](https://ui.trypacked.dev/)."*

## Consuming app(s)

These install `@packed` via the shadcn CLI, so rules are **thin + on-demand**.

1. Copy **`consuming-project/CLAUDE.md`** *or* **`AGENTS.md`** to the repo root —
   the short "use the registry, don't restyle, follow the voice" guardrail.
2. Install the skills:
   `bunx skills add trypacked-com/skills --skill packed-ui --skill packed-design -a cursor -a claude-code -y`
3. Optionally copy **`consuming-project/SKILL.md`** to
   `.claude/skills/packed-design/SKILL.md` for on-demand depth when building screens.

## Why the split

- **Library** edits touch tokens and component styling every time → load the full
  rules always.
- **Consuming** work is mostly composition → keep the always-on file thin to save
  context, and let the skill supply depth only when a new screen is being built.

All rule files carry consistent guidance; use whichever format your tool reads.
