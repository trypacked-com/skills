---
name: packed-ui
description: Install and compose @packed components from the Packed registry. Use when adding registry components, wiring theme/tokens, forms, or styling UI in a consumer app (agent dashboard, marketing site, or RN client). Avoid editing pulled registry files; push fixes upstream to packed.ui and keep project-specific changes in app code.
paths:
  - "components.json"
  - "**/*.tsx"
  - "**/globals.css"
  - "app/**/*.css"
---

# packed.ui (consumer)

shadcn-compatible registry served from the Packed design system (`packed.ui`). Same CLI workflow as shadcn; different defaults (warm cream/orange, rounded corners, warm-tinted shadows, Lora/Figtree/DM Mono).

For full brand rules (colour, type, voice), also use the **packed-design** skill. For copy, use **packed-writing**.

> **⚑ Confirm.** The registry URL below is a placeholder (`ui.trypacked.com`) — replace with the real Packed registry host before relying on it.

## Setup

Add the registry to `components.json`:

```json
"registries": {
  "@packed": "https://ui.trypacked.com/r/{name}.json"
}
```

Install **theme first** — it merges tokens and the Tailwind theme into your CSS and registers Lora / Figtree / DM Mono:

```bash
bunx shadcn@latest add @packed/theme
```

Then components as needed:

```bash
bunx shadcn@latest add @packed/button
bunx shadcn@latest add @packed/form
```

## After install

- **Tokens** live in the CSS file shadcn targets (usually `app/globals.css`), mirroring `packed.ui/handoff/tokens/*.css`. Prefer semantic theme utilities (`bg-app`, `text-muted`, `border-subtle`, `rounded-lg`, `shadow-card`) — never raw scale steps (`orange-500`), never hard-coded hex / px / shadow.
- **Aliases** come from the consumer project's `components.json`. Installed files land under your configured `ui` / `lib` paths; import from those aliases.
- **Dependencies** — registry items declare npm deps; let the CLI install them (e.g. `radix-ui`, `clsx`, `tailwind-merge`, `lucide-react`).
- **React Native** consumers read tokens from `theme.ts` (the mirror of the web tokens), not CSS. Register one font file per weight (`Figtree-Regular/SemiBold/Bold`, `Lora-SemiBold`, `DM Mono`).

## Composing UI

### Proportion

Lead with cream + white surfaces, then **one** orange for the primary action, then sky blue sparingly (weather / flight-status only). If a screen looks orange-heavy, it is overused.

### Forms

Stack: `react-hook-form` + `zod` + `@hookform/resolvers/zod`.

```bash
bunx shadcn@latest add @packed/form
```

Wire: `Form` → `FormField` → `FormItem` → `FormLabel` / `FormControl` / `FormDescription` / `FormMessage`.

- Controls: `1.5px` border, turning `--border-brand` on focus with a `--ring-width 3px` `--ring-focus` halo.
- Hints: `text-sm text-muted` on `FormDescription`.
- Errors: `text-sm` in the cancel/error pair on `FormMessage`; warm, direct copy (see **packed-writing**).
- Do not restyle inside `FormControl`; use `aria-invalid` on the slotted control.

### Surfaces

Cards: white surface, `1px` `--border-subtle`, `--radius-lg`, `--elev-card`; interactive cards lift `-2px` to `--elev-card-hover`. Floating chrome (menus, popovers, sheets) uses the role elevation aliases (`--elev-popover`, `--elev-modal`) — not ad-hoc shadows. Glass/blur is allowed only for floating chrome over content.

### Custom components

- Use `cn()` from the installed utils module.
- Focus: `--ring-focus` halo at `--ring-width 3px` — do not invent a new ring colour.
- Hover/press: darken one step (`--brand` → `--brand-hover`) and lift `-1px`; ghost/soft fill `--brand-subtle`; press settles back. No colour inversion. **Touch has no hover** — collapse hover + press into pressed on native.
- Icons: Lucide, stroke **2** (`2.4` active), `currentColor`, sizes 16/20/24.
- Numbers, times, codes: DM Mono.

## Do not reintroduce

These fight the system and the brand:

- Cool grey or pure-black neutrals (use warm sand / `--text-*`)
- Hard-black shadows (use the warm `--elev-*` aliases)
- Hard-coded hex / px / font / shadow values (reference semantic tokens)
- Sharp corners (everything is rounded; use the `--radius-*` scale)
- Body or UI copy set in the serif (Lora is headlines only)
- Orange on every element (70/20/10 — orange is for *the* action)
- ALL-CAPS outside the eyebrow
- Emoji or unicode as icons

## Updating components

Re-run `bunx shadcn@latest add @packed/<name>` to refresh a component. Diff carefully if you have local edits on generated files.

## Local edits vs upstream

Installed registry files are **copies** from `packed.ui`. Prefer not to edit them in the consumer app.

| Change | In consumer app | Upstream |
|--------|-----------------|----------|
| Project-only (props, layout, composition, app-specific wrappers) | Yes — edit your code, not the pulled file | Not needed |
| Bug fix, token/style alignment, accessibility, shared behaviour | Only if unavoidable; keep the diff minimal | **Yes** — fix in packed.ui, then reinstall |

When you must patch a pulled component:

1. Make the smallest change that solves the problem.
2. Tell the user to **push the same fix upstream** to packed.ui so the next `shadcn add` does not wipe it.
3. Do not refactor or restyle pulled files for convenience — wrap or compose in app code instead.

Do not treat consumer copies as the source of truth for the design system.

## Install this skill (Cursor + Claude)

```bash
bunx skills add ./skills --skill packed-ui -a cursor -a claude-code -y
```

List skills in this repo: `bunx skills add ./skills --list`
