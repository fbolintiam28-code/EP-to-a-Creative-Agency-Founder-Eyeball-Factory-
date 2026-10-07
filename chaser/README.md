# How to run the Chaser

## Where the state lives

**Notion → Eyeball Factory OPS.** The Chaser reads a snapshot of it, not the live database.

| Source | What it contributes |
|---|---|
| VSL Production → **Core Pipeline** | Every creative: status, owner, next action, blocker, ETA, version, days in stage |
| Creator Programs & UGC → **Creator Deliveries** | Every piece of creator content, payment status, whether the creator was told |
| Creator Programs & UGC → **Creators** | Last contacted, what each creator is waiting to hear |
| Decisions & Blockers → **Open Decisions** | Everything already open with Shabir, and its age |

Open Decisions matters most: it is how the Chaser avoids re-asking something that is already
sitting with him, and how it knows what has aged past three days.

## Setup — once

**Claude Project (paid):** create a project called *Eyeball Factory — Chaser*. Paste
`INSTRUCTIONS.md` into the project instructions. Add `STATE-TEMPLATE.md` as a project file.

**Free plan:** keep `INSTRUCTIONS.md` in a note. Each run, paste it as the first message, then the
batch underneath. Same result, one extra paste.

## Each run — about 10 minutes

1. **Export state.** Copy the current rows into the `## STATE` block below. Only the columns listed
   — more is noise.
2. **Paste the batch** under `## MESSAGES`, raw. Do not tidy it. Typos, fragments and duplicates
   are signal: a half-finished message is often the one nobody answered.
3. **Run.**
4. **Check the output against §5 below before sending anything.**
5. **Send the chase messages** from sections 3 and 5. Nothing from section 6 moves until Shabir OKs.
6. **Write back** what changed into Notion: new statuses, new owners, new ETAs as estimates, new
   rows in Open Decisions.

Step 6 is the one that gets skipped when the day is busy, and skipping it is what makes the tracker
drift from reality. If time runs short, write back and skip sending the nice-to-have chases.

## Input format

```
## STATE

### Core Pipeline
ID | Client | Status | Current owner | Next action | Blocked | Blocker | Need-by | Editor ETA | Version | Days in stage

### Creator Deliveries
ID | Creator | Client | Status | Current owner | Days since delivered | Payment status | Creator told

### Open Decisions
Decision | Answer owner | Asked | Age | State

## MESSAGES
[paste raw here — Slack, WhatsApp, email, voice-note transcripts, in any order]
```

## Checking the output before you act on it

Five checks. They take two minutes and they catch the failure modes this build actually has:

1. **Did it invent anything?** Scan every name, ID, date and version against STATE and the batch.
   Anything not in either is a hallucination — delete it and note it.
2. **Did any chase message contain a date or rate?** Rule 2. It should ask for one, never give one.
3. **Is anything client-facing sitting outside section 6?** Rule 1. Move it, or delete it.
4. **Did it read a vague "fine, go ahead" as approval?** Rule 4. It should appear under RULE FLAGS,
   not as a green light.
5. **Is `COULD NOT DETERMINE` empty?** On a real messy batch that is suspicious, not impressive. An
   empty section usually means it guessed somewhere instead of admitting it.

## What it does not do

- **It does not send.** Deliberately. A chaser that sends is one hallucinated name away from
  messaging a client something nobody approved.
- **It does not update Notion.** Write-back is manual, so a wrong read never silently becomes the
  record.
- **It does not decide.** On a second miss it hands Shabir options; it does not pick one.
