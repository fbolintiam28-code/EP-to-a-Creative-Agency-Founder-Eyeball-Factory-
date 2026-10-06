# Build state — 2026-10-06

What is actually built in Notion, verified against the Notion Build Guide.

## Batches — built to guide §3.2

| Property | Type | Guide asked for |
|---|---|---|
| `Name` | Title | ✓ |
| `Need-by` | Date | ✓ |
| `Requested By` | Person | ✓ |
| `Priority Angles` | Relation → Angles (two-way) | ✓ |
| `Quantity requested` | Number | ✓ |
| `Creatives` | Relation → Core Pipeline (two-way) | ✓ |
| `Total` | Rollup, count of Creatives | ✓ |
| `Approved or later` | Rollup, sum | ✓ |
| `Live` | Rollup, sum | ✓ |
| `Status` | Select | beyond the guide — see below |
| `Requested On` | Date | beyond the guide |
| `Performance Context` | Text | beyond the guide |

Three properties go beyond the guide, each tied to something in the SOP:

- **`Status`** with `Requested → Acknowledged → In production → Delivered → Cancelled`.
  `Acknowledged` is SOP Stage 0's exit condition — *"the batch exists with a need-by date and the
  strategist has acknowledged it."* Without that state there is no way to distinguish a request
  somebody has read and accepted from one nobody has opened.
- **`Requested On`** so a batch request that sits unacknowledged can be aged and chased.
- **`Performance Context`** for the one or two lines of results context the Next Batch Request
  template asks for. It is the link back to Stage 7, and the reason this batch exists.

## Angles & Hypotheses — built to guide §3.3

| Property | Type |
|---|---|
| `Angle` | Title (renamed from `Name`) |
| `Hypothesis` | Text |
| `Evidence` | Text |
| `Success signal` | Text |
| `Status` | Select: Backlog / Testing / Winner / Loser / Inconclusive |
| `Learning` | Text |
| `Creatives` | Relation → Core Pipeline (two-way) |
| `Batches` | Relation → Batches (two-way) |

**`Evidence` is text, not URL.** The guide says "Evidence (URLs)", plural. A Notion URL property
holds exactly one link, and the SOP's hypothesis template asks for several — reviews, comments,
competitor ads, past winners. Text holds all of them. The trade-off is that they are not
individually clickable as properties, which is the lesser cost.

**`Inconclusive`** is in the status list as a real outcome, not a failure to decide. "Not enough
signal yet" is genuinely different from "Loser", and collapsing them loses angles that deserve a
second test.

## What had to change in Core Pipeline to make the guide's rollups possible

The guide asks Batches for three rollups. None were possible as the system stood.

1. **Both relations were one-way.** `Batches` and `Angles & Hypotheses` pointed out of Core
   Pipeline with no return property, so neither target database could roll anything up or even see
   its own creatives. Both are now two-way, each surfacing a `Creatives` property.
2. **Two helper formulas.** A Notion rollup takes a function, not a condition, so
   "count where Status ≥ 5 Approved Script" cannot be expressed as a rollup alone. Added
   `Approved or Later` and `Is Live` to Core Pipeline, each returning 1 or 0, and the Batches
   rollups sum them. The alternative was a rollup filter set by hand in the UI, which is invisible
   in the schema and easy to lose.

## Not verified — flagged rather than claimed

The Notion API returns formula values as opaque `formulaResult://` references through every read
path available here, so **I could not confirm the two formulas evaluate correctly.** They are
stored; whether the status comparison works is unconfirmed.

**One-glance check:** look at the `Approved or Later` column on Core Pipeline.

- All four current rows sit at status 6, 7 and 9, so **every one should read 1**.
- `Is Live` should read **0** on all four, since none is at `12 Live`.

If `Approved or Later` reads 0 across the board, the status comparison is failing and the fix is to
swap `.includes(...)` for the nested `or(prop("Phase") == "5 Approved Script", ...)` form, which the
Build Guide itself names as the fallback in §5.

## Dependency worth knowing

Both formulas reference `prop("Phase")` — the current name of the 13-stage property. If it is
renamed to `Status` to match the SOP and the Build Guide, **Notion updates formula references
automatically on rename**, so the formulas survive. Renaming by deleting and recreating the property
would not.
