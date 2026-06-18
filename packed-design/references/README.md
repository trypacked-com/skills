# Packed — Design System

Travel companion for booking agents and their clients. Packed helps travel **agents** deliver a great client experience *after* booking — agents build itineraries in a **web dashboard**; their clients use a **React Native app** for live flight alerts and destination weather. There is also a **marketing website**.

> **Tagline.** The trip is booked. The magic is what comes after.

Three surfaces, one language: agent-dashboard (web), marketing-site (web), client app (React Native). Same tokens, same voice, same components.

## Sources

The token source of truth is `packed.ui/handoff/`: `styles.css` → `tokens/*.css` (web) and `theme.ts` (React Native). The full decision-level brief is `packed.ui/handoff/STYLE_GUIDE.md`. This file is the brand narrative — when prose here and a token disagree, **the token wins**. Edit this file when brand rules change.

## The single non-negotiable rule

**Tokens are the contract.** Never hard-code a hex, px, font name, or shadow. Reference **semantic** tokens (`--brand`, `--text-muted`, `--grad-cta`), not raw scale steps (`--orange-500`). One token edit must reskin all three surfaces.

---

## Brand personality

| Trait | Means in practice |
|---|---|
| **Warm** | Cream surfaces, sunset orange, warm-tinted shadows — never cool grey or hard black. |
| **Friendly** | Generous rounded corners, soft geometric sans, no sharp edges. |
| **Calm & capable** | Quiet confidence. Lead with the helpful fact; no alarm, no jargon. |
| **All-ages** | High legibility, comfortable sizes, plain words. |

Warmth comes from **colour, type and copy** — never from emoji or decoration. The emotional job is **reassurance**: Packed is "the friend who already checked the departures board for you".

---

## Content fundamentals

Voice is **warm, calm, quietly capable**. Speak to the user as **"you"**; Packed is **"we"** ("we'll watch the flights from here"). Sentence case everywhere; ALL-CAPS only for the small tracked eyebrow. Short — one idea per line. Lead with the helpful fact, then the detail. No emoji in product UI. Numbers, times and codes go in the mono face.

**Examples (in voice).**

- ✅ "Heads up — your gate just moved to B7."
- ✅ "All set. We'll watch the flights from here."
- ✅ "Your trip to Lisbon"
- ❌ "ALERT: Gate reassignment event detected." *(alarm, jargon)*
- ❌ "Configuration successfully submitted." *(robotic)*
- ❌ "Trip Entity #4471" *(machine-speak)*

**Words we like:** journey, trip, sorted, set, heads up, in the loop, cared for.
**Avoid:** leverage, utilize, seamless, synergy, "event", "entity".

Marketing headlines lean lyrical in the serif (*"The trip is booked. The magic is what comes after."*); body stays plain and concrete. Full rules live in the **packed-writing** skill.

---

## Visual foundations

### Palette

Warm and sunset-led. Orange anchors; sky carries weather/flight; warm sand neutrals keep surfaces cosy.

| Role | Token | Value |
|---|---|---|
| Brand primary | `--brand` | `#FF6B2C` |
| Brand hover | `--brand-hover` | `#ED5418` |
| Brand pressed | `--brand-press` | `#C4400F` |
| Brand subtle (ghost fill) | `--brand-subtle` | `#FFF3ED` |
| On brand | `--on-brand` | `#FFFFFF` |
| Accent (sky) | `--accent` | `#2B8CD9` |
| App background (cream) | `--bg-app` | `#FBF7F2` |
| Card surface | `--surface-card` | `#FFFFFF` |
| Sunken (wells, inputs) | `--surface-sunken` | `#F5EEE6` |
| Text strong | `--text-strong` | `#221F1A` |
| Text body | `--text-body` | `#38322B` |
| Text muted | `--text-muted` | `#6F6456` |
| Text subtle (large only) | `--text-subtle` | `#938573` |
| Border subtle / default | `--border-subtle` / `--border-default` | `#EAE0D4` / `#D9CCBC` |
| Border on focus | `--border-brand` | `#FF9F6E` |

**Proportion — the 70/20/10 of Packed:** lead with cream + white surfaces, then one orange for action, then blue sparingly. If a screen looks orange-heavy, it is overused — orange is for *the* action, not every element. Sky blue is reserved for weather / sky / flight-status moments. Utility hues are functional, never decorative.

**Status pairs** (foreground / background — always paired): on-time `#1D6640`/`#E8F6EE`, delayed `#9C6A09`/`#FEF6E7`, cancelled `#9C2424`/`#FDECEC`, info `#195C93`/`#ECF6FD`.

**Contrast.** Small white text on solid orange fails AA — for small text on orange use `--brand-press` as background (`--pair-on-brand-safe`), or keep white text ≥18px semibold. `--text-subtle` is large/decorative only. White on `--accent` is large/semibold only.

### Type

Three families, three jobs.

- **Lora** (serif) — display and headlines. Warm, travel-journal feel. Weight **600**, tracking `-0.02em`. Never set body/UI in the serif.
- **Figtree** (geometric sans) — all UI and body. Weights **300–800**, very legible at every size.
- **DM Mono** — numbers, times, flight codes, gates (`TP1234`, `08:45`, `Gate B7`, `12C`). Tabular and calm.

Scale: display `clamp(2.75rem,6vw,4.5rem)`, h1 `clamp(2.25rem,4.5vw,3.25rem)`, h2 `clamp(1.75rem,3.2vw,2.5rem)`, h3 24, h4 20, body-lg 18, body 16, small 14, xs 12, eyebrow 11 (Figtree 700, UPPERCASE, `0.12em`). Line heights: tight 1.1, snug 1.25, normal 1.5, relaxed 1.65 (body default). **RN has no `clamp()`** — resolve display sizes to fixed phone numbers (h1 ≈ 34, h2 ≈ 26, h3 ≈ 22).

**Sentence case everywhere** — headings, buttons, nav. ALL-CAPS only for the eyebrow (`.pk-eyebrow`).

### Spacing

4px base unit. `4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 64 / 80 / 96`. Lay rows and groups out with flex/grid + `gap`, not margins or inline whitespace.

### Radius

Rounded and soft — core to the friendly feel, **nothing sharp**. Inputs/buttons `12` (`--radius-md`), cards `16` (`--radius-lg`), hero/feature blocks `20–28` (`--radius-xl`/`--radius-2xl`), chips/avatars/status pills full (`--radius-pill`).

### Borders

Hairlines. `1px` `--border-subtle`/`--border-default` (warm sand), `1.5px` on form controls turning `--border-brand` on focus with a `--ring-width 3px` `--ring-focus` halo.

### Shadows

Warm-tinted, soft, **never hard black** (brown undertone `rgba(56,50,43,…)`). Use the role aliases, not raw scale: `--elev-card` (resting), `--elev-card-hover` (interactive, lift `-2px`), `--elev-popover` (menus), `--elev-modal` (dialogs/sheets), `--elev-cta` (orange glow, primary CTA only), `--elev-nav` (hairline, not a drop).

### Backgrounds & gradients

Default surfaces are flat cream (`--bg-app`) and white cards. The sunset gradient is the signature, always 135°: `--grad-sunset` (hero/logo lockups), `--grad-cta` (marketing CTA band), `--grad-ember` (deepest, small accents), `--grad-journey` (sunset→sky, trip/weather heroes only). On-gradient content is white with `--on-grad-shadow`.

### Animation

Gentle and brief — no harsh bounces, no long animations. `--dur-fast 120ms` (hover/press), `--dur-base 200ms` (toggles), `--dur-slow 320ms`. `--ease-out` to settle, `--ease-in-out` for symmetric moves, `--ease-soft` (slight overshoot) for **one** delightful moment — the switch thumb. The live status dot has a slow pulse. Always respect `prefers-reduced-motion` / Reduce Motion.

### Hover & press states

Buttons darken one step (`--brand` → `--brand-hover`) and lift `-1px` on hover; ghost/soft buttons fill with `--brand-subtle`; nav/list rows wash to `--state-row-hover`. Press settles back down — **no colour inversion**. **Touch has no hover** — on native, collapse hover + press into the pressed state and drop hover-only affordances (tooltips, row washes).

### Cards & surfaces

The default container: white surface · `1px` `--border-subtle` hairline · `--radius-lg` · `--elev-card`. Interactive cards lift `-2px` to `--elev-card-hover` on hover. Internal hierarchy is type weight + size, not boxes inside boxes.

### Glass / translucency

For floating chrome over content only — not decorative. Sticky bars use `--glass-bar-bg` + `--glass-bar-blur`; on-photo badges `--glass-on-photo`; frosted tiles over gradient heroes `--glass-tile` + `--glass-tile-blur`.

### Imagery

Warm, sunlit, **golden-hour** travel photography — sunsets, coastlines, old-town streets. Avoid cold/blue-grey or clinical stock. Store a photo URL per trip/destination; render behind the hero with a scrim (`--scrim-bottom` default) so white text stays legible; show `--photo-fallback` while loading. No device frames, no perspective tilts, no decorative numbers or fake stats.

### Layout

Generous breathing room; don't crowd. Dashboard: `264px` sidebar (`--sidebar-w`) + fluid content capped ~1120px (`--container-max 1200`). Marketing: content caps ~1140px; floating pill nav is full-width/transparent at the top, then pulls in (~940px) with blur + border + shadow once scrolled past ~24px.

---

## Iconography

- **Lucide** only — rounded line icons, **2px** stroke (`2.4` for active/emphasis), round caps/joins. `lucide-react` (web) / `lucide-react-native` (native); names match across both.
- **Colour.** `--text-muted` at rest, `--brand` when active/meaningful, white on imagery/gradients. Currentcolor only — never multicolor.
- **Never** emoji or unicode as icons; never mix in a second/filled set.

> **⚑ Substitution flagged.** Lucide is a stand-in via CDN in the kits — install the package for production.

---

## Logo & agency branding

**Packed mark** — bespoke suitcase SVG (`packed-mark.svg`, `packed-mark-white.svg` in `assets/`). On light → `--brand` fill; on dark/photo → white version. Min **24px** (`--logo-min`), clear space **50%** of mark height all sides. Ship via `react-native-svg` on native — not a Lucide glyph.

> **⚑ Substitution flagged.** The logo SVGs are not vendored into this skill yet — source them from `packed.ui` assets when available.

**Agency logos — the "brand chip" (white-label).** Agencies upload their own logo (transparent or opaque-on-white). Always place it inside a **white brand chip** (rounded white card, soft shadow) so both render cleanly — tokens `--chip-bg`, `--chip-radius`, `--chip-shadow`, `--chip-logo-h`. On photos use `--chip-shadow-on-photo`. Ask agencies for ~2–3:1 wordmarks.

---

## The one rule

**Tokens are the contract.**
