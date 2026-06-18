---
name: packed-ui-maintainer
description: Maintain the Packed design system & @packed registry — add or update registry components, build registry.json, stories, and docs. Use in the packed.ui repo when editing registry/handoff, building the registry, or changing tokens. Not for consuming @packed in other apps.
paths:
  - "registry/**"
  - "handoff/**"
  - "stories/**"
  - "public/registry.json"
  - "registry.json"
  - "app/globals.css"
  - "app/(docs)/**"
---

# packed.ui (maintainer)

Use only in the `packed.ui` repo. Full brand narrative: **packed-design** skill (`references/README.md`). Voice: **packed-writing**.

Consumers install via `@packed` — use the **packed-ui** skill, not this one.

> **⚑ Confirm.** `packed.ui` currently ships the design system as a **handoff** (`handoff/tokens/*.css`, `handoff/components/*`, `STYLE_GUIDE.md`) and is not yet a published shadcn registry. The registry steps below describe the target workflow — align paths with the repo once the registry build exists.

## Add or change a component

1. Source in `registry/ui/` (and `registry/lib/` if shared)
2. Register in `registry.json`
3. `bun run build:registry`
4. Story in `stories/`
5. Docs route in `app/(docs)/components/[slug]/page.tsx`
6. Visual + build checks (`bun run test:visual`, `bun run build`)

Match existing patterns — reuse shared surface/elevation helpers (role aliases `--elev-card` / `--elev-popover` / `--elev-modal`) rather than one-off restyling each component. Build any new component for **both platforms** (web + React Native) with an identical prop API; native equivalents use `Pressable` / `View` / `Text` / `TextInput` against `theme.ts`.

## Registry publish

- Manifest: `public/registry.json` (built, committed)
- Per-item JSON: `public/r/{name}.json` via `build:registry`
- Consumer namespace: `"@packed": "https://ui.trypacked.com/r/{name}.json"`

## Tokens

`handoff/tokens/*.css` (web) and `theme.ts` (React Native) are the source of truth for theme tokens. The theme registry item is generated from these — change tokens there first (keep web and native mirrors in sync), then rebuild the registry. `STYLE_GUIDE.md` is the prose brief; when prose and a token disagree, the token wins — update the guide to match.

## Do not

- Add consumer-app setup instructions to registry components (no `components.json` advice in component source)
- Hard-code hex / px / font / shadow — reference semantic tokens
- Reintroduce cool-grey neutrals, hard-black shadows, sharp corners, or serif body copy — see **packed-design**

## Definition of done

Reads from tokens on both platforms · matching prop API web + native · passes voice + sentence-case review.

## Install

```bash
bunx skills add ./skills --skill packed-ui-maintainer -a cursor -a claude-code -y
```
