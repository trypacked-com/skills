# Packed — design rules for Claude Code

This repo holds the Packed design system. Full brand narrative lives in the
`packed-design` skill (`references/README.md` in [packed.skills](https://github.com/trypacked-com/skills)).
Tokens: `registry/styles/packed-theme-tokens.css`; `STYLE_GUIDE.md` is the
decision-level brief. The rules below are non-negotiable — do not reintroduce
framework defaults (shadcn/MUI ship cool-grey ramps, hard-black shadows, and
sharp corners; we use warm sand, soft warm-tinted shadows, and rounded corners).

## The one rule
**Tokens are the contract.** Never hard-code a hex, px, font, or shadow. Reference
**semantic** tokens (`--brand`, `--text-muted`, `--grad-cta`), not raw scale steps
(`--orange-500`).

## Color
- Warm, sunset-led. Brand orange **`#FF6B2C`** (`--brand`) is the single anchor:
  actions, logo, active states. Sky blue **`#2B8CD9`** (`--accent`) is the only
  accent, reserved for **weather / sky / flight-status**.
- Neutrals are warm **sand** (cream `--bg-app #FBF7F2`, white cards
  `--surface-card`). **No cool grey, no pure black** — never introduce `gray-*`.
- **Proportion 70/20/10:** lead with cream + white, then one orange for action,
  then blue sparingly. If a screen looks orange-heavy, it is overused.
- Utility hues are **functional only**: status green / amber / red, always used as
  documented fg/bg pairs (`--status-*-fg` / `--status-*-bg`).
- Gradients are the signature, always 135° (`--grad-sunset`, `--grad-cta`,
  `--grad-ember`, `--grad-journey`) — on heroes/CTAs, not in resting surfaces.
- Dark mode is a **warm charcoal** foundation (`[data-theme="dark"]`), never pure
  black; brand lightens one step. Cream/light is the primary target.

## Type
- **Lora** (serif) — display and headlines. Weight **600**, tracking `-0.02em`.
  Never set body or UI in the serif.
- **Figtree** (geometric sans) — all UI, body, labels. Weights **300–800**;
  body 400, labels 500, emphasis 600. Body line-height 1.65.
- **DM Mono** — numbers, times, flight codes, gates (`TP1234`, `08:45`, `Gate B7`).
- Sentence case everywhere; ALL-CAPS only for the small tracked eyebrow
  (`.pk-eyebrow`).
- Fonts are bundled via `@fontsource` (Lora, Figtree, DM Mono) — no runtime CDN.

## Spacing · radius · borders
- Spacing: **4px base unit**. Scale: 4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 64 / 80 / 96.
- Radius: **rounded and soft — nothing sharp.** Inputs/buttons `12`
  (`--radius-md`), cards `16` (`--radius-lg`), hero `20–28` (`--radius-xl`/`2xl`),
  chips/avatars/pills full (`--radius-pill`).
- Borders: hairlines. `1px` `--border-subtle`/`--border-default` (warm sand);
  form controls use `1.5px` turning `--border-brand` on focus.

## Elevation
- Shadows are **warm-tinted, soft, never hard black** (brown undertone
  `rgba(56,50,43,…)`). Use role aliases: `--elev-card`, `--elev-card-hover`,
  `--elev-popover`, `--elev-modal`, `--elev-cta` (primary CTA only), `--elev-nav`.
- Glass/blur is allowed only for floating chrome over content — never decorative.

## Motion
- Gentle and brief. `--dur-fast 120ms`, `--dur-base 200ms`, `--dur-slow 320ms`.
- `--ease-out` to settle, `--ease-in-out` for symmetric moves, `--ease-soft`
  (slight overshoot) for **one** moment only — the switch thumb.
- No harsh bounces, no long loops on chrome. Respect `prefers-reduced-motion`.

## States
- Hover: darken one step (`--brand` → `--brand-hover`) and lift `-1px`; ghost/soft
  fill `--brand-subtle`; nav/list rows wash to `--state-row-hover`.
- Press: settles back down. **No colour inversion.**
- Focus: `--ring-focus` halo at `--ring-width 3px`.

## Voice (for any UI copy)
- Warm, calm, quietly capable. Speak to the user as **"you"**; Packed is **"we"**.
- Sentence case. **No emoji.** Lead with the helpful fact, then the detail.
- ✅ "Heads up — your gate just moved to B7." / "All set. We'll watch the flights from here."
- ❌ "ALERT: Gate reassignment event detected." / "Configuration successfully submitted."

## Iconography
- Lucide only, stroke width **2** (`2.4` for active/emphasis), currentColor.
  Sizes 16/20/24, 8px gap to label.
- No emoji or unicode as icons.

## Logo
- Use `@packed/logo` from the registry — do not hand-roll the mark.
- **Never below 24px.** Clear space = 50% of mark height.
- Agency logos always sit inside the white **brand chip** (`--chip-*`).

## Registry
- Base URL: [ui.trypacked.dev](https://ui.trypacked.dev/)
- Namespace: `"@packed": "https://ui.trypacked.dev/r/{name}.json"`
- Theme: `bunx shadcn@latest add @packed/theme`
- Components: `bunx shadcn@latest add @packed/<name>`
