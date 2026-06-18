# Packed — UI rules (consuming app)

> Generic agent file. Identical to CLAUDE.md — use whichever your tool reads.

This app consumes the Packed registry (`@packed` via shadcn CLI). It does **not**
redefine the design system — the registry owns tokens, components, and styling.
Your job is to compose installed components correctly and keep net-new layout on-brand.

## Do
- **Use installed `@packed` components** (Button, Card, Input, Logo, …) instead of
  hand-rolling or restyling. If a component is missing a variant, add it upstream
  in [packed.ui](https://github.com/trypacked-com/packed.ui) — don't fork its styles here.
- **Use theme tokens** for any net-new markup: the CSS variables / Tailwind classes
  from `@packed/theme` (`bg-app`, `text-muted-foreground`, `border-border-subtle`,
  `shadow-card`, etc.). Never hardcode hex values or introduce a new color.
- **Load the packed skills** when building a new screen or layout — **packed-ui** for
  install/compose rules, **packed-design** for brand, **packed-writing** for copy.

## Don't
- ❌ Override component internals with one-off CSS, `!important`, or wrapper hacks.
- ❌ Edit pulled registry files — push fixes upstream to packed.ui and reinstall.
- ❌ Use cool-grey ramps (`gray-*`), hard-black shadows, sharp corners, or serif body copy.
- ❌ Add emoji in UI copy.

## Net-new layout rules (when the registry has no component for it)
- **Spacing:** 4px base — 4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 64 / 80 / 96.
- **Radius:** soft — inputs/buttons 12, cards 16, pills full.
- **Type:** Lora for headlines (600), Figtree for UI/body (300–800), DM Mono for
  numbers/times/codes. Long body is never serif.
- **Motion:** `--dur-fast 120ms`, `--dur-base 200ms`, `--dur-slow 320ms`. Nothing harsh.
- **States:** hover → brand darken + lift `-1px`; press settles back; focus →
  `--ring-focus` halo at `--ring-width 3px`.

## Voice (any UI copy)
Warm, calm, quietly capable. **You** for the user, **we** for Packed. Sentence case,
no emoji. Lead with the helpful fact.
- ✅ "Heads up — your gate just moved to B7."
- ❌ "ALERT: Gate reassignment event detected."

## Setup reminder

```json
"registries": {
  "@packed": "https://ui.trypacked.dev/r/{name}.json"
}
```

```bash
bunx shadcn@latest add @packed/theme
bunx shadcn@latest add @packed/button
```
