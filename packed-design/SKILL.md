---
name: packed-design
description: Use when generating branded UI, HTML mocks, marketing surfaces, or when the user asks for Packed (trypacked.com) look-and-feel. Not for shadcn registry install steps (use packed-ui).
user-invocable: true
---

Read `references/README.md` in this skill first (vendored brand guide). The machine source of truth for tokens lives in `packed.ui/handoff/` (`styles.css` → `tokens/*.css` for web, `theme.ts` for React Native) — when prose and a token disagree, the token wins.

For static mocks and throwaway prototypes: output standalone HTML the user can open, linking the handoff `styles.css`. For production apps consuming `@packed`, also load **packed-ui** for install and compose rules. For copy and voice, load **packed-writing**.

## Quick reference

- **One rule: tokens are the contract.** Never hard-code a hex, px, font name, or shadow. Reference semantic tokens (`--brand`, `--text-muted`, `--grad-cta`), not raw scale steps (`--orange-500`).
- **Colour.** Warm, sunset-led. Brand orange `#FF6B2C` is the single anchor (actions, logo, active). Sky blue `#2B8CD9` is the only accent, reserved for weather / sky / flight-status. Warm "sand" neutrals (cream `#FBF7F2` app bg, white cards). Status green / amber / red. Proportion is **70/20/10**: lead with cream + white, then one orange for action, then blue sparingly.
- **Type.** Three families, three jobs. **Lora** serif for display/headlines (600, `-0.02em`). **Figtree** sans for all UI/body (300–800). **DM Mono** for numbers, times, flight codes, gates. Sentence case everywhere; ALL-CAPS only for the small tracked eyebrow.
- **Spacing.** 4px base unit (`4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 64 / 80 / 96`).
- **Radius.** Rounded and soft — nothing sharp. Inputs/buttons 12, cards 16, hero 20–28, chips/avatars/pills full.
- **Borders.** Hairlines — 1px (`--border-subtle`/`--border-default`), 1.5px on form controls turning `--border-brand` on focus.
- **Shadows.** Warm-tinted, soft, never hard black (brown undertone). Use the role aliases (`--elev-card`, `--elev-popover`, `--elev-modal`); `--elev-cta` (orange glow) for primary CTAs only.
- **Motion.** Gentle and brief. `--dur-fast 120ms`, `--dur-base 200ms`, `--dur-slow 320ms`. `--ease-soft` (slight overshoot) for one moment only — the switch thumb. Nothing harsh. Respect reduced-motion.
- **Glass/blur.** Allowed, but for floating chrome over content only (sticky bars, on-photo badges) — never decorative.
- **Imagery.** Warm, golden-hour travel photography. Always scrim photos behind text. No cold/clinical stock. No data slop.
- **Voice.** Warm, calm, quietly capable. "you" for the user, "we" for Packed. No emoji. (Full rules: **packed-writing**.)

## Files

```
references/README.md       · brand guide (read this first)
```

Token source of truth (in the repo, not vendored here):

```
packed.ui/handoff/styles.css            · global entry (link this on web)
packed.ui/handoff/tokens/*.css          · colours, brand, type, spacing, base
packed.ui/handoff/STYLE_GUIDE.md        · full decision-level brief
packed.ui/handoff/components/           · React primitives + prompt specs
```

## Install this skill (Cursor + Claude)

```bash
bunx skills add ./skills --skill packed-design -a cursor -a claude-code -y
```

List skills in this repo: `bunx skills add ./skills --list`
