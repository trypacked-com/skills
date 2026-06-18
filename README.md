# packed.skills

Installable agent skills for [Packed](https://trypacked.com). Brand and design system rules, adapted from the `packed.ui` handoff.

## Skills

| Skill | Description |
| ------------------------ | ------------------------------------------------------------------------------------------------ |
| **packed-design** | Brand and visual design — sunset palette, type, spacing, rounded corners, warm shadows, motion, logo. |
| **packed-ui** | Install and compose `@packed` components from the Packed registry in consumer apps. |
| **packed-ui-maintainer** | Maintain the Packed design system / registry (use in the `packed.ui` repo only). |
| **packed-writing** | Copy and content voice — warm, calm, "you" / "we", sentence case. |

Brand guide: `packed-design/references/README.md` · token source of truth: `packed.ui/handoff/`.

## Install

```bash
bunx skills add ./skills --list

# consumer app
bunx skills add ./skills --skill packed-ui --skill packed-design -a cursor -a claude-code -y

# working in packed.ui
bunx skills add ./skills --skill packed-ui-maintainer --skill packed-design -a cursor -a claude-code -y

# writing (optional global)
bunx skills add ./skills --skill packed-writing -g -a cursor -a claude-code -y
```
