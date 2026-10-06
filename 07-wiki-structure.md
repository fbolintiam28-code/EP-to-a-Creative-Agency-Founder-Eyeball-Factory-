# Wiki structure — Eyeball Factory OPS

Restructured 2026-10-06 from a flat database of mixed rows into a landing page with two work areas.

## What was wrong

The root was a database whose rows were Home, an SOP, two work areas, a decisions tracker and a
voice note — six things of four different kinds, all at the same level. Nothing in the structure
told a reader what was a category and what was a document, so every page looked equally important
and none looked like a starting point. That is the "all over the place" feeling: not too much
content, no hierarchy.

## The structure now

```
👁️‍🗨️ Eyeball Factory OPS
│
├── 🏠 Home ........................... the landing page. Start here.
│
├── 🎬 VSL Production ................. AREA 1 — paid video
│   ├── 📘 VSL Production SOP ......... the process
│   ├── Core Pipeline ................. every creative, 13 stages
│   ├── Batches ....................... what was asked for, by when
│   └── Angles & Hypotheses ........... what we test and what we learn
│
├── 📱 Creator Programs & UGC ......... AREA 2 — creator content
│   ├── 📘 Creator Programs SOP ....... draft v0.1, pending Kayhan
│   ├── Creator Deliveries ............ every piece, brief to used
│   ├── Creators ...................... the roster
│   └── Creator Briefs ................ angles, dos and don'ts, claims
│
├── ⛔ Decisions & Blockers ........... COMPANY-WIDE
│   └── Open Decisions ................ anything waiting on a person, aged
│
└── 🎙️ Founder Briefs ................. COMPANY-WIDE
    ├── Day 1 — Paid video and VSLs
    └── Day 2 — The creator side
```

Four top-level cards instead of six mixed ones, and each area now contains its own SOP rather than
having it float at the root.

## Why this shape

**Two areas, because Shabir's own framing is two.** His Day 2 note closes: *"Ok that's it. That's
the two sides."* The structure matches how he describes the business, so nobody has to translate.

**Each area owns its SOP.** The VSL SOP used to sit at the root beside the work areas, which made
it look like a third area. It is not — it is the instruction manual for one of them. Moving it
inside means someone opening VSL Production finds the process and the trackers together.

**The briefs are kept apart from the SOPs on purpose.** Both SOPs were written *from* the voice
notes, so the notes are the primary source and the SOPs are interpretation. When they disagree, the
note is what he said. Collapsing them would lose the ability to tell the difference.

**Company-wide is a real category, not leftovers.** Open decisions and the founder's own words both
span the two sides. Filing them under either one would hide half of them.

## What the structure now supports

Three properties were added to the root sections database, which is what makes wiki-style grouping
possible:

| Property | Options | What it is for |
|---|---|---|
| `Area` | Start here · VSL Production · Creator Programs & UGC · Company-wide | What the wiki groups and tabs by |
| `Type` | Landing page · Work area · SOP · Tracker · Reference | Lets a reader tell a process doc from a live tracker at a glance |
| `Who uses it` | free text | Every section says who opens it and what for |

## How the two sides connect

Not two separate systems. The join is real and runs both ways:

```
Creator Deliveries ──[ VSL Creative ]──► Core Pipeline
Core Pipeline ──────[ Creator Footage ]──► Creator Deliveries
```

From Shabir's Day 2 note: *"sometimes an editor cuts it into something."* Follow a piece of UGC to
the ad it ended up in, or open a VSL and see which creator supplied the footage.

Within VSL Production the three databases are also joined: **Batches** ↔ **Core Pipeline** ↔
**Angles & Hypotheses**, with Batches also relating directly to Angles for priority angles. A batch
rolls up how many of its creatives are approved or live, so "what is ready for Thursday" is a
number rather than a count by hand.

## Automation — what is built, what needs the UI

**Built (properties and formulas):**

| Where | Property | Does |
|---|---|---|
| Core Pipeline | `Stage entered` | Date the card last changed status |
| Core Pipeline | `Days in stage` | How long it has sat there |
| Core Pipeline | `Stale?` | Flags 2+ days in the same status, excluding Live and Analyzed |
| Core Pipeline | `Approved or Later`, `Is Live` | Feed the Batches rollups |
| Batches | `Total`, `Approved or later`, `Live` | Batch progress without counting by hand |
| Creator Deliveries | `Days Since Delivered` | Surfaces footage rotting in the drive |
| Creators | `Days Since Contact` | Surfaces a creator going unanswered |
| Open Decisions | `Age (days)` | Surfaces a question nobody has answered |

Every one of those exists to replace someone remembering.

**Needs doing in the Notion UI — I cannot do these through the API:**

1. **The `Stage entered` automation.** Database automations: trigger *Property edited → Phase*,
   action *Edit property → Stage entered → Now*. Add a second on *Page added*. Without it,
   `Days in stage` and `Stale?` stay empty. Automations only act on changes made after they are
   created, so fill in `Stage entered` by hand once on the four existing cards.
   *If automations are not on this plan:* type `@today` into `Stage entered` whenever you move a
   card. A few seconds per move.
2. **Wiki views on the sections database.** Tabs filtered by `Area` — All, VSL Production, Creator
   Programs & UGC, Company-wide — which is what gives the template's tabbed look. Gallery layout
   for the cards.
3. **Views on Creator Deliveries**, the ones that make the creator side self-surfacing:
   - *Needs review* — Status is `5 Usability review`
   - *Gone quiet* — `Days Since Delivered` > 7 and Status is not `10 Used`
   - *Overdue payments* — `Payment Status` is `Overdue`
   - *Creator not told* — `Creator Told` unchecked and Status is `10 Used` or `Not usable`
   - *Needs Shabir* — Status is `7 Awaiting Shabir OK`
4. **Views on Creators:** *Waiting to hear* (`Waiting To Hear` is not empty) and *Gone silent*
   (`Days Since Contact` > 14, Relationship is `Active`).
5. **Database templates** so new cards start complete — a creative card with the review checklists,
   a hypothesis, a batch request, a creator delivery.

## Still outstanding, and not fixable by structure

- **The team cannot access any of this.** One member plus the integration bot. A wiki nobody can
  open is a document. This is the single biggest open decision.
- **The Creator Programs SOP is a draft from a second-hand account**, by Shabir's own admission. It
  needs Kayhan before it is shown to anyone as process.
- **`Phase` and `Select` are still swapped** relative to both the SOP and the Build Guide, which
  agree that the 13 stages are `Status` and Plan/Review/Make/Ship/Learn is `Phase`. Renaming is safe
  — Notion updates formula references automatically — but it is not mine to do unasked.
