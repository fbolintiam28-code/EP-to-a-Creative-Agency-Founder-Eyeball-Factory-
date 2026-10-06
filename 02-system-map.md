# System map — where everything lives

Both service lines, one Notion workspace. Updated 2026-10-06 after Shabir's second voice note.

## Structure

```
👁️‍🗨️ Eyeball Factory OPS
├── 🏠 Home                        — the single entry point, spans both sides
├── 🎙️ Founder Brief — Day 1       — his voice note, verbatim. Primary source.
├── 💡 VSL Production SOP          — v0.1, written process for paid video
├── 📹 Creatives                   — PAID VIDEO
│   ├── Core Pipeline              — VSLs through 13 stages. Schema good, no rows.
│   ├── Batches
│   └── Angles & Hypotheses
├── 🎬 Creator Programs            — CREATOR / UGC  (added 2026-10-06)
│   ├── Creator Deliveries         — brief → used. Schema built, no rows.
│   ├── Creators                   — the roster. Replaces Kayhan's private list.
│   └── Creator Briefs             — angles, dos and don'ts, prohibited claims
└── ⛔ Decisions & Blockers
    └── Open Decisions             — 25 rows, 11 Blocking now
```

## The architecture decision: one home, two pipelines

Asked whether the creator side should be a second dashboard. It should not, and it should not be
merged into the first either.

**Against two dashboards.** His test is *"I need to know what's happening without asking anyone."*
He runs across all of it. Two dashboards means two places to look, and the moment something falls
between them he asks. Two dashboards fail the test by construction.

**Against one pipeline.** The objects are different in kind. A VSL is an *asset* moving through
stages and then it is done. A creator is a *relationship* that persists across many deliveries. One
table for both leaves half of every row empty, and nobody maintains a table like that.

**What settles it** is in his own words: *"sometimes an editor cuts it into something."* Creator
footage becomes raw material for VSL edits. These are not two businesses sharing an owner — one
feeds the other. Separate dashboards would cut that link exactly where it matters. Care & Bloom's
claims rules apply on both sides too, so the compliance asset is shared.

So: **separate databases, one Home, and a real relation at the join.** Creator Deliveries carries
`VSL Creative`; Core Pipeline now carries `Creator Footage` back. Traceable in both directions.

## Design choices on the creator side, and why

The creator pipeline is not a copy of the VSL one. It is shaped around a different failure mode.

| Choice | Reason |
|---|---|
| **`5 Usability review` is its own named stage** | The step Shabir called *"where it goes quiet."* It was not a slow step — it was an unassigned one. Content arrived, got filed, and became nobody's job. A stage with an owner and an age is the fix. |
| **`Days Since Delivered` on every row** | *"Sometimes it just sits in that drive from months ago nobody's touched."* Content already shot and already paid for, producing nothing. The age column makes rot visible without anyone remembering to look. |
| **`Waiting To Hear` and `Last Contacted` on every creator** | His second explicit ask: *"I don't want a creator chasing Kayhan or me because nobody told them anything."* |
| **`Creator Told` checkbox on each delivery** | A finished delivery with this unticked is a creator left in silence. Finishing the work is not finishing the job. |
| **`Payment Status` with an `Overdue` state** | *"I get asked about it when something's late."* Late payments currently reach him. An overdue flag with a due date means they surface before a creator chases. |
| **`Current Owner` includes `Nobody`** | Deliberately available, deliberately alarming. The whole creator-side problem was work with no owner, so the system has to be able to say so out loud rather than leaving the field blank. |
| **Same `Founder OK for Client` gate** | Creator content sometimes goes straight to a client, so rule 1 applies identically. Built defaulting to requiring his OK — the safe direction — and flagged as my assumption, not his instruction. |
| **No separate Payments database** | Payment lives as fields on each delivery. A fourth database adds weight before volume justifies it, and an unused database is worse than a tight one. Revisit if payments get complicated. |

## Different failure modes, deliberately

Worth stating plainly, because it is why the two pipelines are not symmetrical:

- **Paid video:** when something stalls, **work is late.** An internal cost, recoverable.
- **Creator side:** when something stalls, **a creator is left in silence.** The cost is the talent
  pool — ignored creators stop answering, and the ones who chase go to Kayhan or Shabir. Not
  recoverable by working faster afterwards.

Hence the anti-silence fields on the creator side have no equivalent on the VSL side. Same
principle, different mechanism.

## The gaps

| # | Gap | Consequence |
|---|---|---|
| 1 | **Both pipelines are empty.** | Neither side can tell him what is happening. Purely a data problem now, not a design one. |
| 2 | **The team has no Notion access** — one member plus the integration bot. | Every update is by hand and the cards drift from reality. `Blocking now`. |
| 3 | **The creator roster lives in Kayhan's own list**, location unknown even to Shabir. | The creator side cannot run independently of Kayhan — the same single-point-of-failure this engagement exists to remove. |
| 4 | **No written Care & Bloom claims list.** | A compliance exposure on both sides, not an admin gap. A prohibited claim in live UGC for a consumer health brand costs the client relationship. |
| 5 | **No saved views yet.** | The daily note is assembled by hand. Views need rows to be meaningful, so this follows the data. |
| 6 | **Creator-side process is unwritten.** | Shabir's account was explicitly second-hand — *"Kayhan runs this one, not me."* There is no SOP equivalent until Kayhan confirms the flow. |

## Next, in order

1. **Get live work into both pipelines.** Still the biggest blocker on the paid side; on the creator
   side the drive backlog is a free source of starting rows.
2. **Resolve team access.** Decides whether this is self-maintaining or hand-maintained.
3. **Put the Shabir-owned blocking decisions to him** in one numbered burst.
4. **Get Kayhan on the creator flow** — the usability owner, the roster, and who handles payment.
5. **Build the saved views** once there are rows: Needs Shabir, Gone quiet, Overdue payments, Due this week.
6. **Write the creator-side SOP** once Kayhan has corrected the map.
