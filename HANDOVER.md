# Handover — Eyeball Factory Exec Ops
**2026-10-07, end of the three-day alignment sprint.**
Written so somebody who was not here can pick this up on Monday.

---

## 1. The headline

**Blockers were not hard. They were unasked.**

At 14:05 today six direct, specific chases went out. By 14:36 — thirty-one minutes — five had
answers, and these had been stuck for between one and two and a half weeks:

| Stuck | How long | Cleared by |
|---|---|---|
| CB-13 script never reached Editor 1 | 2 weeks, two identical failures | "Paste the direct link in this thread, not the folder" |
| Brand display font | ~2.5 weeks, an editor idle | "You used it on CB-09 — what is it?" |
| CB-10 hook line | 1 week | Strategist was out two days; nobody had told him a deadline existed |
| Editor 2's September invoice | Raised twice, unanswered | One batched yes/no to Shabir |
| Which creator was owed money | Unknown to anyone but Kayhan | One question |

The font was the clearest case. Editor 1 had **CB Display Medium installed the whole time** — it came
off an old project folder and was never filed anywhere. Two and a half weeks of an editor with
nothing to do, for a file on a colleague's machine.

The Strategist's line is the same shape: *"was out two days, nobody told me there was a deadline on
the cb-10 hook."* Not a slow person. A deadline that existed in Shabir's head and in the tracker and
never reached the one who had to act on it.

**That is the whole case for the system.** None of this needed more effort. It needed one place where
things are written down, and one person asking the specific question.

---

## 2. What exists, and where

**Notion → Eyeball Factory OPS** — [published view](https://local-line-21f.notion.site/Eyeball-Factory-3f0d5fafa31380f9a1bee9f387082658)

```
🏠 Home (Read First) ............... landing page, both sides, the three rules
🎬 VSL Production .................. paid video
   📘 VSL Production SOP ........... 13 stages, owners, gates, templates
   Core Pipeline ................... CB-09 to CB-13, live
   Batches ......................... CB-B01, need-by + rollups
   Angles & Hypotheses ............. Testimonial (winner) / FounderStory (loser)
📱 Creator Programs & UGC .......... creator content
   📘 Creator Programs SOP ......... draft v0.1, pending Kayhan
   Creator Deliveries .............. 4 clips awaiting review, backlog parked
   Creators ........................ Maya
   Creator Briefs .................. Thursday group call
🗂️ Data Room ....................... where every file lives (restructured by Ops: function-first,
   Drive Map ....................... client pages inside each)
   Assets — Brand Kits ............. per-client gallery
⛔ Decisions & Blockers ............ 18 rows, aged, routed by who can close them
🎙️ Founder Briefs .................. Shabir's two voice notes, verbatim
```

**Repo — the working layer** (`claude/eyeball-factory-ops-3xghvr`)

| File | What it is |
|---|---|
| `chaser/INSTRUCTIONS.md` | The chaser. Paste into a Claude Project. Turns raw messages + state into what's late, who to chase, and the messages to send |
| `chaser/README.md` | How to run it, and the 5 checks before acting on its output |
| `chaser/STATE-TEMPLATE.md` | State snapshot, refreshed to today |
| `chaser/runs/2026-10-07-RAW.md` | Today's unedited first pass |
| `chaser/runs/2026-10-07-CORRECTED.md` | Corrected, with the 7-change log |
| `08-daily-cadence.md` | **Start here Monday.** 5 min morning, 5 min end of day, and what to do when something slips |
| `09-offload-ranked.md` | The ranked list |
| `01-guardrails.md` | The three rules as procedures, with ready-to-send deflection language |
| `05-naming-convention.md` | Creative IDs, file names, angle tokens |
| `00-operating-brief.md` | How Shabir works, time zones, what he has not briefed |

---

## 3. For whoever runs Monday

**Open `08-daily-cadence.md` and work the morning list in order.** It takes five minutes. The order
matters: aged decisions → blocked → stale → **ownerless** → creator usability review → rotting
footage → overdue payments → creators owed an answer.

**If you only have one minute:** Open Decisions, sorted by Age. Anything 3+ days old goes to Shabir
today.

**The three rules are absolute.** Nothing to a client without his OK. Never commit a date or a rate.
Check the version before forwarding.

**On a second miss, stop chasing.** Two misses means the plan was wrong, the person is overloaded, or
the work is harder than scoped — different fixes, and only Shabir picks. Give him options, not a
complaint. There is no third miss.

### Live right now

| | State |
|---|---|
| **CB-11** | ⚠️ **Unaccounted for.** Not mentioned by anyone in a week. Promised to Care & Bloom as one of the three Autumn videos. Chased Editor 1 at 15:40, no reply yet. **Pick this up first.** |
| **CB-09** | Live — but went live with no recorded Copy Review, the only claims check in its path, on a consumer health brand. Open with Shabir. |
| **CB-10** | Strategist writing the hook now. Should close today. |
| **CB-12** | Edit revisions, hook being redone. Candidate for Thursday. |
| **CB-13** | Moved to next week. Unblocked — Editor 1 has the script. |
| **Maya** | Owed £300, past the only date anyone recalls agreeing. |
| **4 creator clips** | Owner = Nobody. Nobody reviews usability. |

---

## 4. What I would take off his plate — ranked

Full working in `09-offload-ranked.md`. **~6 h/wk**, range 5–7.

**Method:** count × frequency × minutes, counting *his* minutes not mine, rounding down, adding a
5-minute context switch only where a ping broke into creative work. Up slightly from Day 2's 5.5
because today supplied counted chases instead of estimated ones.

| # | What | Saves |
|---|---|---|
| 1 | **Status chasing + the daily digest** — who has what, what's due, who hasn't replied | 2–3 h/wk |
| 2 | **Review routing and feedback consolidation** — the assembly around his judgment, not the judgment | 1.5–2 h/wk |
| 3 | **Client review pack prep** | 1 h/wk |
| 4 | **Open decisions kept and re-asked** so nothing waits on him remembering | 0.5–1 h/wk |
| 5 | **Creator payment tracking** — now unblocked: Kayhan owns it, Maya identified | 0.5–1 h/wk |
| 6 | **Telling creators where they stand** | 0.5 h/wk |
| 7 | **Version hunting before anything goes out** | 0.3–0.5 h/wk |
| 8 | **Weekly performance report assembly** — once the review has a day | ~1 h/wk |
| 9 | **Batch requests → cards, drive hygiene** | ~0.5 h/wk |

### The first three I would take in week one

Highest hours at lowest risk, and **nothing blocked on an open decision**.

1. **Status chasing + the daily digest — 2–3 h/wk.** Proven today: six chases, five answers in
   thirty-one minutes, two and a half weeks of stuck work cleared. Needs no permission to start.
2. **Review routing and feedback consolidation — 1.5–2 h/wk.** Does not ask him to delegate
   judgment, only the assembly around it. That distinction is what makes it safe in week one.
3. **Client review pack prep — 1 h/wk.** Time-critical, and prep is the safe half: I build it, he
   approves it, nothing reaches the client without his OK.

**Week one: 4.5–6 h/wk.**

**Deliberately not in week one:** the weekly performance report, because the review still has no day
in the calendar and you cannot take over a meeting that does not happen. And anything requiring his
judgment — reviewing scripts and cuts, approving client sends, setting dates and rates. Those are
not inefficiencies. They are the work only he can do, and the point of all this is to give him more
room for them.

---

## 5. Still open, and who owns it

| Blocking | Owner |
|---|---|
| CB-11 unaccounted for | Editor 1 |
| CB-09 live with no claims check | Shabir |
| No written Care & Bloom claims list | Shabir |
| Team cannot access the tracker | Shabir |
| Team not told the Ops role exists | Shabir |
| Who reviews creator content for usability | Kayhan |
| Where the creator list lives | Kayhan |
| Maya's £300, overdue | Shabir |

**The two that unlock the most:** team Notion access, and a one-line note from Shabir telling the
team the role exists. Without both, every chase still routes through him — which is the exact thing
this was built to stop.

---

## 6. Claude chat links

| Day | Link |
|---|---|
| Day 1 — Mon 5 Oct | *(Ops Assistant's own chat links)* |
| Day 2 — Tue 6 Oct | https://claude.ai/share/8d9dadeb-1958-4be9-a5a9-16b914e0d6e6 |
| Day 3 — Wed 7 Oct | https://claude.ai/code/session_01Bvz8iFJ349SvywACAQ35ed |
