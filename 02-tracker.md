# Tracker

The thing that replaces "it lives in his head." Empty of real rows until I'm given the live work
or the channel access to read it — see `04-open-questions.md`. The structure below is what I'll
fill, and it's built backwards from the three things Shabir chases today:

> who has which file · what is due when · who has not replied

---

## A. Deliverables in flight

| ID | Client | Deliverable | Line | Owner | Current version | Status | Due | Last touch | Waiting on | Next nudge | Needs Shabir |
|---|---|---|---|---|---|---|---|---|---|---|---|
| — | — | *(no rows yet)* | — | — | — | — | — | — | — | — | — |

**Column meanings** — these are the whole point, so they're defined, not assumed:

- **Owner** — the one person who moves it next. Never two names. Never a team.
- **Current version** — the marker the file actually carries, verbatim. Feeds rule 3.
- **Status** — one of: `Brief needed` · `In progress` · `Internal review` · `Shabir review` ·
  `Approved to send` · `Sent to client` · `Client feedback in` · `Revisions` · `Live` · `Parked`
- **Due** — what was actually agreed, with who agreed it. A date nobody confirmed is not a due
  date; it goes in `Waiting on` as a date that needs confirming.
- **Last touch** — when this row last genuinely moved. Rows that haven't moved in 48h get chased.
- **Waiting on** — the named person, not "the team." This column is the follow-up queue.
- **Next nudge** — when I chase, set the moment I log `Waiting on`. A blank here is how things
  get forgotten.
- **Needs Shabir** — `yes` / `no`. The only column he has to read. Everything marked `yes` becomes
  a numbered line in the end-of-day note.

## B. Open with Shabir — decisions only he can make

Because he replies in bursts and silence means he assumes it's handled, every ask gets aged. Age
is what gets a stalled decision answered.

| ID | The ask | Why it needs him | Blocks | Asked | Age | Re-asked | Answer |
|---|---|---|---|---|---|---|---|
| — | *(no rows yet)* | — | — | — | — | — | — |

Rules for this table:
- Anything hitting **3 days** goes to the top of the end-of-day note with its age stated plainly.
- **Blocks** names what stops moving until he answers. An ask with nothing behind it probably
  shouldn't be on his plate.
- Every ask is phrased as yes/no or pick-one unless open-ended is genuinely the honest framing.
- An unanswered ask is never closed by assumption. It stays open with its age climbing.

## C. Client-facing sends — the rule 1 log

| Date | Client | What went out | Version | Shabir OK'd | Approval evidence |
|---|---|---|---|---|---|
| — | — | *(no rows yet)* | — | — | — |

Every client send has a row here, with the approval recorded before the send, not after. If a row
can't be completed, the send doesn't happen.

## D. People — who hasn't replied

Rolling view, rebuilt daily from column `Waiting on` above. Keeps the chase off Shabir.

| Person | Channel | Waiting on them | Since | Chased | Next chase |
|---|---|---|---|---|---|
| — | — | *(no rows yet)* | — | — | — |

---

## Where this should actually live

Markdown is right for today — fast, reviewable, versioned here. It is not right for month one,
because Shabir reads on his phone and the team works in Slack. This repo has a **Notion**
connection available, which would let the tracker be a live database he can open from a phone
link and the team can update in place.

I haven't touched the Notion workspace — that's a question for you, not a decision for me. It's
in `04-open-questions.md`.
