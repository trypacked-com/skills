# packed.skills

Installable agent skills for [Packed](https://trypacked.com).

## Skills

| Skill | Description |
| ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| **packed-design** | Brand and visual design — sunset palette, type, spacing, rounded corners, warm shadows, motion, logo. |
| **packed-ui** | Install and compose `@packed` components from [ui.trypacked.dev](https://ui.trypacked.dev/) in consumer apps. |
| **packed-ui-maintainer** | Maintain the packed.ui registry (use in that repo only). |
| **packed-writing** | Copy and content voice — warm, calm, "you" / "we", sentence case. |

Brand guide: `packed-design/references/README.md`

## Install

```bash
bunx skills add trypacked-com/skills --list

# consumer app
bunx skills add trypacked-com/skills --skill packed-ui --skill packed-design -a cursor -a claude-code -y

# working in packed.ui
bunx skills add trypacked-com/skills --skill packed-ui-maintainer --skill packed-design -a cursor -a claude-code -y

# writing (optional global)
bunx skills add trypacked-com/skills --skill packed-writing -g -a cursor -a claude-code -y
```

Local sibling checkout:

```bash
bunx skills add ../skills --skill packed-ui-maintainer --skill packed-design -a cursor -a claude-code -y
```

## Versioning

Tag releases when the public registry or brand rules change materially:

```bash
bunx skills add trypacked-com/skills@v1.0.0 --skill packed-ui -a cursor -y
```
