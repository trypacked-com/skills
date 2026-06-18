---
name: packed-writing
description: Use when writing product copy, docs, commit messages, UI strings, or any Packed (trypacked.com) prose. Warm, calm, "you" for the user / "we" for Packed, sentence case.
---

# Packed — writing

Copy and content voice for Packed. Visual layout and components are **packed-design** or **packed-ui** — use those when strings also need typography, spacing, or registry patterns.

## Voice

Warm, calm, quietly capable. Quiet confidence — lead with the helpful fact, no alarm, no jargon. The emotional job is reassurance: Packed is "the friend who already checked the departures board for you".

**We** for Packed — not I. **You** for the user ("Heads up — your gate just moved to B7."). Sentence case by default (including labels and most headings). ALL-CAPS only for the small tracked eyebrow. Brand: **Packed** or **trypacked.com** as proper nouns.

No emoji in product UI. Short sentences; one idea per line. Numbers, times and codes go in the mono face (`TP1234`, `08:45`, `Gate B7`).

## Examples

- ✅ "Heads up — your gate just moved to B7."
- ✅ "All set. We'll watch the flights from here."
- ✅ "Your trip to Lisbon"
- ❌ "ALERT: Gate reassignment event detected." *(alarm, jargon)*
- ❌ "Configuration successfully submitted." *(robotic)*
- ❌ "Trip Entity #4471" *(machine-speak)*

Marketing headlines lean lyrical in the serif (*"The trip is booked. The magic is what comes after."*). Body stays plain and concrete.

## Pronouns

**You** for the user. **We** for Packed ("we'll watch the flights from here"). Avoid machine-speak and passive corporate tone.

## Punctuation and numbers

Period > em-dash > comma. Ellipses are fine, used literally. Numbers and stats only when real and useful. No vanity metrics, no charts-for-decoration.

## UI strings

Keep labels and errors in sentence case unless a proper noun requires otherwise. Error messages: warm and direct, no blame — state what happened and what to do next, lead with the reassuring fact.

When copy sits in a designed surface, load **packed-design** or **packed-ui** as appropriate.

## Install this skill

```bash
bunx skills add trypacked-com/skills --skill packed-writing -g -a cursor -a claude-code -y
```
