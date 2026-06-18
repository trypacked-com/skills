---
name: packed-ui
description: Install and compose @packed components from ui.trypacked.dev. Use when adding registry components, wiring theme/tokens, forms, floating menus, or styling UI in a consumer app. Avoid editing pulled registry files; push fixes upstream to packed.ui and keep project-specific changes in app code.
paths:
  - "components.json"
  - "**/*.tsx"
  - "**/globals.css"
  - "app/**/*.css"
---

# packed.ui (consumer)

shadcn-compatible registry at [ui.trypacked.dev](https://ui.trypacked.dev/). Same CLI workflow as shadcn; different defaults (warm cream/orange, rounded corners, warm-tinted shadows, Lora/Figtree/DM Mono).

For full brand rules (colour, type, voice), also use the **packed-design** skill. For copy, use **packed-writing**.

## Setup

Add the registry to `components.json`:

```json
"registries": {
  "@packed": "https://ui.trypacked.dev/r/{name}.json"
}
```

Install **theme first** — it merges tokens and Tailwind theme into your CSS and registers Lora / Figtree / DM Mono:

```bash
bunx shadcn@latest add @packed/theme
```

Then components as needed:

```bash
bunx shadcn@latest add @packed/button
bunx shadcn@latest add @packed/form
```

Catalog and docs: [ui.trypacked.dev](https://ui.trypacked.dev/) · manifest: [registry.json](https://ui.trypacked.dev/registry.json)

Optional dark mode:

```bash
bunx shadcn@latest add @packed/theme-provider
```

Wire `ThemeProvider` and the theme init script per the installed `theme-provider` file comments so `.dark` does not flash on load.

## After install

- **Tokens** live in the CSS file shadcn targets (usually `app/globals.css`). Prefer theme utilities (`bg-app`, `text-muted-foreground`, `border-border-subtle`, `rounded-lg`, `shadow-card`, `duration-base`) — not `gray-*`, not raw scale steps (`orange-500`, `sand-900`), not hard-coded hex / px / shadow.
- **Aliases** come from the consumer project's `components.json`. Installed files land under your configured `ui` / `lib` paths; import from those aliases, not from `@/registry/*` unless your project uses the same layout as the docs site.
- **Dependencies** — registry items declare npm deps; let the CLI install them. Many components need `radix-ui`, `clsx`, `tailwind-merge`, `lucide-react`, etc.

## Composing UI

### Forms

Stack: `react-hook-form` + `zod` + `@hookform/resolvers/zod`.

```bash
bunx shadcn@latest add @packed/form
```

Wire: `Form` → `FormField` → `FormItem` → `FormLabel` / `FormControl` / `FormDescription` / `FormMessage`.

- Hints: `text-sm text-muted-text` on `FormDescription`.
- Errors: `text-sm text-destructive` on `FormMessage`; warm, direct copy (see **packed-writing**).
- Do not restyle inside `FormControl`; use `aria-invalid` on the slotted control.

### Floating surfaces

Menus, popovers, selects, and similar panels must match installed components. If you add a **new** floating surface, follow the same patterns as the registry (white/card surface, `border-border-subtle`, warm role elevation — `shadow-card` / popover/modal utilities — not ad-hoc hard-black shadows):

- use semantic tokens and `--elev-popover` / `--elev-modal` role aliases
- gentle motion (`duration-base`, `--ease-out`)
- glass/blur only for floating chrome over content — never decorative

Dialogs/sheets use the modal surface pattern from installed registry components.

### Custom components

- Use `cn()` from the installed utils module.
- Focus: `--ring-focus` halo at `--ring-width 3px` — do not invent a new ring colour.
- Hover/press: darken one step (`--brand` → `--brand-hover`) and lift `-1px`; ghost/soft fill `--brand-subtle`; press settles back. No colour inversion.
- Icons: Lucide, stroke **2** (`2.4` active), `currentColor`, sizes 16/20/24.
- Logo: `@packed/logo` — do not hand-roll the mark.

## Do not reintroduce

These break the system and fight installed components:

- `gray-100` … `gray-900` or other cool-grey neutrals
- hard-black shadows (use warm `--elev-*` / `shadow-card` aliases)
- sharp corners (use the `--radius-*` scale)
- serif (Lora) on body or UI copy — headlines only
- orange on every element (70/20/10 — orange is for *the* action)
- raw scale utilities (`orange-500`, `sand-900`) or hard-coded hex / px / shadow values

## Updating components

Re-run `bunx shadcn@latest add @packed/<name>` to refresh a component. Diff carefully if you have local edits on generated files.

## Local edits vs upstream

Installed registry files are **copies** from [packed.ui](https://github.com/trypacked-com/packed.ui). Prefer not to edit them in the consumer app.

| Change | In consumer app | Upstream |
|--------|-----------------|----------|
| Project-only (props, layout, composition, app-specific wrappers) | Yes — edit your code, not the pulled file | Not needed |
| Bug fix, token/style alignment, accessibility, shared behaviour | Only if unavoidable; keep the diff minimal | **Yes** — fix in packed.ui, then reinstall |

When you must patch a pulled component (fix or style update):

1. Make the smallest change that solves the problem.
2. Tell the user to **push the same fix upstream** to packed.ui so the next `shadcn add` does not wipe it.
3. Do not refactor or restyle pulled files for convenience — wrap or compose in app code instead.

Do not treat consumer copies as the source of truth for the design system.

## Install this skill (Cursor + Claude)

```bash
bunx skills add trypacked-com/skills --skill packed-ui -a cursor -a claude-code -y
```

List skills in this repo: `bunx skills add trypacked-com/skills --list`
