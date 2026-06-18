---
name: packed-writing
description: Use when writing product copy, docs, notifications, UI strings, or any Packed (trypacked.com) prose. Warm, calm, "you" for the user / "we" for Packed, sentence case.
---

# Packed — writing

Copy and content voice for Packed. Visual layout and components are **packed-design** or **packed-ui** — use those when strings also need typography, spacing, or registry patterns.

## Voice

Warm, calm, quietly capable. Quiet confidence — lead with the helpful fact, no alarm, no jargon. The emotional job is reassurance: Packed is "the friend who already checked the departures board for you".

**Pronouns.** Speak to the user as **"you"**. Packed is **"we"** ("we'll watch the flights from here").

**Casing.** Sentence case everywhere — headings, buttons, nav. ALL-CAPS only for the small tracked eyebrow.

**Length.** Short. One idea per line. A notification is a glanceable sentence. Lead with the helpful fact, then the detail.

No emoji in product UI. Numbers, times and codes go in the mono face (`TP1234`, `08:45`, `Gate B7`, `12C`).

## Examples

| ✅ Do | ❌ Don't |
|---|---|
| "Heads up — your gate just moved to B7." | "ALERT: Gate reassignment event detected." |
| "All set. We'll watch the flights from here." | "Configuration successfully submitted." |
| "Your trip to Lisbon" | "Trip Entity #4471" |

Marketing headlines lean lyrical in the serif (*"The trip is booked. The magic is what comes after."*). Body stays plain and concrete.

## Words

**We like:** journey, trip, sorted, set, heads up, in the loop, cared for.

**Avoid:** leverage, utilize, seamless, synergy, "event", "entity", and any machine-speak.

## UI strings

Sentence case unless a proper noun requires otherwise. Error and status messages: warm and direct, no blame — state what happened and what to do next, lead with the reassuring fact. No alarm language.

When copy sits in a designed surface, load **packed-design** or **packed-ui** as appropriate.

## Install this skill

```bash
bunx skills add ./skills --skill packed-writing -g -a cursor -a claude-code -y
```
