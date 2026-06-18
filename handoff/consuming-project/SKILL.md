---
name: packed-design
description: Build on-brand UI in a project that consumes the Packed registry. Use when creating new screens, layouts, or product surfaces. Covers how to compose installed @packed components, the design voice, and layout/spacing rules. Does NOT redefine tokens — the registry owns those.
user-invocable: true
---

# Packed — building UI in a consuming app

This project installs components from [ui.trypacked.dev](https://ui.trypacked.dev/) via
`@packed`. When you build a screen or layout, follow this skill. The registry owns
tokens, colors, type, and component styling — your job is to **compose**, not redefine.

## First, orient
- Check which `@packed` components are already installed (`components/ui`, `components.json`).
  Prefer an existing component over building one.
- Use theme tokens for any net-new markup (`bg-app`, `text-muted-foreground`,
  `border-border-subtle`, `shadow-card`, …). Never hardcode a hex or invent a color.
- If a needed variant is missing, add it **upstream in packed.ui**, not here.

## The rules that always hold
- **Tokens are the contract.** Every colour, radius, shadow, and font comes from
  `@packed/theme` — no raw scale steps or hard-coded values.
- **Colour:** warm sand + sunset orange; sky blue sparingly (weather/flight only).
  Proportion **70/20/10** — one orange for *the* action, not every element.
- **Type:** Lora headlines (600), Figtree UI/body (300–800), DM Mono for numbers/times/codes.
  Sentence case; ALL-CAPS only for the eyebrow.
- **Spacing:** 4px base. **Radius:** soft (12 inputs, 16 cards, full pills).
- **Shadows:** warm role aliases (`shadow-card`, popover/modal elevation) — never hard black.
- **Motion:** `--dur-fast 120ms` / `--dur-base 200ms` / `--dur-slow 320ms`. Nothing harsh.

## Voice (any copy you write)
Warm, calm, quietly capable. **You** for the user, **we** for Packed. Sentence case.
No emoji. Lead with the helpful fact.

## Layout approach
- Generous breathing room. Don't crowd. Use the registry's Card, Sidebar, and layout
  primitives first. Drop to raw markup only for page scaffolding — and even then, use
  theme tokens.
- Logo: `@packed/logo` — never hand-roll the mark.

## When in doubt
Load **packed-ui** for install/compose rules and **packed-writing** for copy. Full
brand narrative: **packed-design** skill in [trypacked-com/skills](https://github.com/trypacked-com/skills)
(`packed-design/references/README.md`).
