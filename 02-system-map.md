# System map — where everything actually lives

Written after reading the Notion workspace. **The system is not being built from scratch** — a
good deal of it already exists. This file maps it and names the gaps, so nothing gets rebuilt
twice and nothing real gets overwritten.

## The Notion workspace: Eyeball Factory OPS

```
👁️‍🗨️ Eyeball Factory OPS
├── 🏠 Home                      — blank
├── 💡 VSL Production SOP        — v0.1, the written process. Substantial.
├── 📹 Creatives
│   ├── Core Pipeline            — the tracker. Schema built, no real rows.
│   ├── Batches
│   └── Angles & Hypotheses
└── ⛔ Decisions & Blockers       — added 2026-10-06
    └── Open Decisions           — 15 real rows
```

## What already exists and is good

**The VSL Production SOP** is a real process document, not a sketch. It has the 13-status flow
with a named ball holder and exit condition per status, roles by channel, gates, a review
checklist, a naming convention, an escalation ladder, and eight templates. It was drafted
2026-10-05 from Shabir's voice note.

Notably, it already encodes all three rules in §8 Gates and guardrails — client gate, no
commitments on his behalf, version check — and §9 states the silence rule outright: *"Shabir's
silence means he assumes it is handled. So the Ops Assistant never waits on him to ask."*

**Core Pipeline** carries the columns the follow-up loop needs: `Current Owner`, `Status`,
`Version (e.g. v2)`, `Next Action`, `Blocked` + `Blocker`, `Founder OK for Client`, `Editor ETA`,
`Client`, plus relations to Batches and Angles & Hypotheses.

That is a well-designed tracker. It does not need redesigning.

## The gaps

| # | Gap | Consequence |
|---|---|---|
| 1 | **Core Pipeline has no real rows** — one blank row only. | The tracker cannot show him anything. Nothing to read means nothing replaces the chasing. This is the whole sprint goal, and it is purely a data-entry problem now, not a design one. |
| 2 | **The team has no Notion access** — the workspace has one member plus the integration bot. | The SOP has editors linking cuts on the card and the Media Buyer recording live dates on the card. Neither can happen. Every update falls to me by hand and the tracker drifts from reality within days. Logged as `Blocking now`. |
| 3 | **15 `[TBC]` defaults sat invisible inside the SOP.** | A proposed default in a document is not a decision. Now extracted into Open Decisions with an owner, an age and what each one blocks. |
| 4 | **No "needs Shabir" view.** | The end-of-day note is assembled by hand each day. A saved view filtered to blocking items would make it a read rather than a rebuild. |
| 5 | **SOP §11 is missing** — numbering jumps §10 → §12. | Cosmetic, but he will notice it in a read-through. Logged. |

## Division of labour between Notion and this repo

**Notion is the system.** Live state, cards, the SOP, open decisions. It is what Shabir opens and
what the team works in. Nothing here duplicates it.

**This repo is my working layer.** The operating brief, the guardrail procedures and ready-to-send
language, the note templates and time-saved method, the sent-note archive. Reference material for
how I do the job, versioned so changes are visible.

Rule: **if it is live state, it goes in Notion.** If it is how I work, it lives here.

## Next, in order

1. **Get the live work into Core Pipeline.** Still blocked on the inventory — see
   `04-open-questions.md` Q1. Nothing else matters as much.
2. **Resolve team access** (Open Decisions, `Blocking now`). Decides whether the tracker is
   self-maintaining or hand-maintained.
3. **Put the six `Blocking now` decisions to Shabir** in one numbered burst he can answer by voice note.
4. **Build the saved views** that make the daily note a read: Needs Shabir, Blocked, Waiting on
   someone, Due this week.
5. **Fold confirmed answers back into the SOP**, replacing each `[TBC]` and adding a change-log line.
