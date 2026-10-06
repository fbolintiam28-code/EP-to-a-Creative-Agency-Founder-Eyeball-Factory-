# Naming convention — Core Pipeline, Batches, Angles & Hypotheses

The VSL SOP §7 fixes naming at the **creative and file** level. It says nothing about how to name
**Batch** or **Angle** records. So this file does two things: restates what the SOP already
decides (which is not up for redesign), and extends it to the two databases it does not cover,
using the same logic.

---

## Part 1 — What the SOP already fixes

Straight from §7. Not a proposal.

| Thing | Format | Example |
|---|---|---|
| Creative ID | `[ClientCode]-[##]` | `CB-09` |
| File name | `CB-09_[Angle]_[Length]_v[#]` | `CB-09_Testimonial_90s_v2` |
| Folder | `/[Client]/CB-09/` → `01 Script + Brief` · `02 Assets` · `03 Edits` · `04 Final` · `05 Uploaded` | |

Plus the four version rules: the card is the source of truth; check the version before forwarding;
never overwrite, save a new version; a folder is not a handoff, send a direct link.

---

## Part 2 — Core Pipeline

The database has both a `Title` and a `Creative ID`, which need to do different jobs.

| Property | Format | Example |
|---|---|---|
| `Creative ID` | `[ClientCode]-[##]` | `CB-09` |
| `Title` | **the file stem, without the version** | `CB-09_Testimonial_90s` |
| `Version (e.g. v2)` | `v` + number | `v2` |

**Why the title is the file stem.** Title + Version reconstructs the filename exactly:

```
CB-09_Testimonial_90s   +   v2   →   CB-09_Testimonial_90s_v2.mp4
         Title                Version              the actual file
```

That makes rule 3 mechanical instead of a judgement call. Before forwarding anything, the card
title and the file name should match character for character up to the version. If they do not,
something is wrong and it is visible at a glance rather than discovered by a client.

**Why the version is a field and not in the title.** The card persists across every revision; the
file does not. Putting `v2` in the title means renaming the card on every round, which breaks links,
breaks relation chips, and loses the history of what the card was called. The card is the thing that
lasts, so it carries the stable part of the name.

### Client codes

`CB` = Care & Bloom. The rest are unknown — see open questions.

Rules: two or three letters, uppercase, drawn from the brand name, unique, and **never reused** even
after a client leaves. A reused code makes old files ambiguous forever.

### Numbering

Sequential per client, zero-padded to two digits, starting `CB-01`. Never reused, never renumbered,
not even for a creative that was killed at hypothesis stage — the gap is the record that it existed.

**Known ceiling:** two digits runs out at 99 per client, and `CB-100` sorts before `CB-11` in any
plain text sort. At current volume that is a long way off, and the SOP specifies two digits, so this
keeps to it rather than quietly contradicting Shabir's document. Flagged so it is a known decision
later, not a surprise.

---

## Part 3 — Angles & Hypotheses

The constraint that drives this: **the angle name goes inside every file name.** `CB-09_Testimonial_90s`.
So an angle is not just a label, it is a filename component, and it has to behave like one.

| Property | Format | Example |
|---|---|---|
| `Title` | `[ClientCode]-A[##] [AngleToken]` | `CB-A03 Testimonial` |

The **angle token** is the part that lands in filenames, and it must be:

- **One word.** No spaces — spaces in filenames break links and command-line tooling.
- **PascalCase** if it needs two concepts: `SleepQuality`, `BeforeAfter`, `FounderStory`.
- **Letters only.** No slashes, ampersands, apostrophes, accents or emoji.
- **Short.** Under about 15 characters, or filenames become unreadable on mobile.
- **Frozen once used.** The moment a token appears in a filename it cannot be renamed — the files
  already carry it. Rename the descriptive part in the card body instead.

Good: `Testimonial` · `SleepQuality` · `BeforeAfter` · `FounderStory` · `PriceObjection`
Bad: `Testimonial / UGC hybrid` · `Sleep & stress` · `the "does it work" angle`

Angles are numbered per client, because messaging differs per brand even when the format is shared.
Two clients can both have a `Testimonial` token; they are `CB-A03` and `XX-A01`.

---

## Part 4 — Batches

### First, a defect worth fixing before naming anything

Core Pipeline's `Need-by` is a **rollup that targets the Batches title property**. So whatever a
batch is called is literally what appears in the `Need-by` column on every creative card. Today,
with batches called `Batch 1`, that column reads "Batch 1" where a date should be.

Compounding it: **Batches currently has no properties at all** — just `Name`. The SOP's Stage 0 says
a batch request carries a need-by date, a quantity and priority angles. None of those exist as fields,
so none can be rolled up, filtered or sorted, and the `Current Batch` view has nothing to key on.

**Two fixes, in this order:**

1. Give Batches real properties: `Need-by` (date), `Quantity` (number), `Priority Angles`
   (relation → Angles & Hypotheses), `Requested By` (person), `Status`, `Requested On` (date).
2. Repoint the Core Pipeline `Need-by` rollup at the new `Need-by` **date** property instead of the
   title. Then it returns an actual date — sortable, filterable, and usable in a "due this week" view.

Naming cannot fix a rollup pointed at the wrong property. Do these first.

### Then, the naming

| Property | Format | Example |
|---|---|---|
| `Title` | `[ClientCode]-B[##] · [need-by, short date]` | `CB-B04 · 17 Oct` |

The date stays in the title even after the rollup is fixed, because the title is what shows in
relation chips on each creative card. Seeing `CB-B04 · 17 Oct` on a card tells you what it belongs to
and when it is wanted without opening anything.

Batches are numbered per client and sequential. The date in the title is the **need-by**, not the
date requested — need-by is what everything plans backwards from.

---

## Part 5 — The rules that keep it working

1. **Never rename a token that has reached a file.** Client codes and angle tokens are frozen on
   first use. The files already carry them and cannot be retroactively corrected.
2. **Never reuse a number.** Not after a kill, not after a client leaves. Gaps are information.
3. **The card title is the file stem.** If they diverge, the card is wrong — fix the card, never the
   file.
4. **Version lives in the field.** Only in the field.
5. **One creative, one ID, forever.** A creative that gets re-cut for a different length is a new
   creative with a new ID, not the same one renamed. `CB-09_Testimonial_90s` and
   `CB-09_Testimonial_30s` being the same ID is the beginning of confusion about which is live.

---

## Worked example

Media Buyer requests five creatives for Care & Bloom, needed 17 October:

```
Batch        CB-B04 · 17 Oct
             └─ Need-by 17 Oct, Quantity 5

Angle        CB-A03 Testimonial

Creative     Creative ID   CB-09
             Title         CB-09_Testimonial_90s
             Version       v2
             Batch         CB-B04 · 17 Oct
             Angle         CB-A03 Testimonial

Folder       /Care & Bloom/CB-09/
               01 Script + Brief
               02 Assets
               03 Edits/      CB-09_Testimonial_90s_v1.mp4
                              CB-09_Testimonial_90s_v2.mp4
               04 Final/      CB-09_Testimonial_90s_v2.mp4
               05 Uploaded
```

Before forwarding: card says `CB-09_Testimonial_90s` at `v2`; file reads
`CB-09_Testimonial_90s_v2.mp4`. They match, so it goes. That check takes a second and is the whole
of rule 3.

---

## Smaller cleanup spotted

Core Pipeline has a property literally called **`Select`**, holding Plan / Review / Make / Ship /
Learn. That is the SOP's phase grouping with a default property name never changed. Rename it to
**`Phase`** — it is one edit and it stops the column header reading like a leftover.

---

## Still open

- **Client codes beyond `CB`.** Cannot issue IDs consistently without the list.
- **Where the files actually live.** The SOP defines the folder structure but names no host — Drive,
  Dropbox, Frame.io. Rule 3 cannot be performed in a system nobody can open.
