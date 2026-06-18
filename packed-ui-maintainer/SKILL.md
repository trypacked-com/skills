---
name: packed-ui-maintainer
description: Maintain the packed.ui shadcn registry — add or update registry components, build registry.json, stories, and docs. Use in the packed.ui repo when editing registry/ui, running build:registry, or changing tokens in app/globals.css. Not for consuming @packed in other apps.
paths:
  - "registry/**"
  - "stories/**"
  - "public/registry.json"
  - "registry.json"
  - "app/globals.css"
  - "app/(docs)/**"
---

# packed.ui (maintainer)

Use only in the [packed.ui](https://github.com/trypacked-com/packed.ui) repo. Follow `AGENTS.md` and `app/globals.css`. Full brand narrative: **packed-design** skill (`references/README.md`). Voice: **packed-writing**.

Consumers install via `@packed` — use the **packed-ui** skill, not this one.

## Add or change a component

1. Source in `registry/ui/` (and `registry/lib/` if shared)
2. Register in `registry.json`
3. `bun run build:registry`
4. Story in `stories/`
5. Docs route in `app/(docs)/components/[slug]/page.tsx`
6. Visual + build checks (`bun run test:visual`, `bun run build`)

Match existing registry patterns: reuse role elevation aliases (`--elev-card` / `--elev-popover` / `--elev-modal`) and token utilities — extend those patterns, do not one-off restyle each component.

## Registry publish

- Manifest: `public/registry.json` (built, committed)
- Per-item JSON: `public/r/{name}.json` via `build:registry`
- Consumer namespace: `"@packed": "https://ui.trypacked.dev/r/{name}.json"`

## Tokens

`registry/styles/packed-theme-tokens.css` and `app/globals.css` are the source of truth for theme tokens. The theme registry item (`registry:theme`) is generated from here — change tokens in CSS first, then rebuild registry if the theme item needs to reflect it. `STYLE_GUIDE.md` is the prose brief; when prose and a token disagree, the token wins — update the guide to match.

## Do not

- Add consumer-app setup instructions to registry components (no `components.json` advice in component source)
- Reintroduce shadcn defaults (cool-grey ramps, hard-black shadows, sharp corners) — see `AGENTS.md`

## Install

```bash
bunx skills add trypacked-com/skills --skill packed-ui-maintainer -a cursor -a claude-code -y
```
