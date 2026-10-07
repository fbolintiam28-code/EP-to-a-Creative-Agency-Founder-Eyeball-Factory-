# Data Room — what was built, and what it does and does not fix

Built 2026-10-07 in Notion: **Home → Data Room** (Company-wide).

## Contents

| Database | Rows | Purpose |
|---|---|---|
| **Drive Map** | 6 seeded | Every stable Drive location, with a direct link, an owner, access level, and `Last verified` |
| **Assets — Brand Kits** | Care & Bloom + a reusable template | Fonts, logos, colours **and claims rules**, one row per client |

Per-creative folders are deliberately **not** in the Drive Map — their link lives on the creative's
card in Core Pipeline, so there is only one place for it and it cannot disagree with itself.

## The honest assessment

The ask was that these two fix the handoff failures. They fix one completely and one partly, and the
difference matters because the remaining piece is the cheap one.

| Failure | Cause | Does the Data Room fix it? |
|---|---|---|
| **Brand font missing ~2.5 weeks.** Editor 2 blocked on hooks; CB-09 and CB-10 hooks built on a placeholder; CB-09 then went live. | Nobody had ever written down where it lives. | **Yes, completely.** This is exactly the problem a brand kit solves. |
| **CB-11, then CB-13.** *"Same folder as the scripts"*, then *"same folder as cb-12"*. Editor 1 did not have either. | Not that the folder was unfindable — Editor 1 could find it. **A folder with five scripts in it does not tell him which file is his.** | **Partly.** It makes the right link easy to produce. It does not make anyone produce it. |

**The missing third piece** is the rule, now stated at the top of the Data Room page:

> A file is handed over when its **direct link is on the card**. Not when it is "in the drive", not
> when it is "in the same folder". No link on the card means the work has not been handed over,
> whatever was said in Slack.

That rule already existed in SOP §7 and was not followed — because following it was harder than not
following it. With an agreed structure to link into, it stops being extra work.

**Sequencing matters here.** Announce the rule *after* the links exist and are backfilled onto the
live cards. Announcing first just asks people to do something harder than what they do now, which is
how the rule got ignored the first time.

## A limitation worth stating plainly

**Notion links to Google Drive. It does not mirror it.** There is no live folder sync, so nothing
here updates when someone moves or renames a folder. That is why every row carries `Last verified`
and a `Days since verified` formula where **999 means never checked**. A link nobody has verified is
a guess with a URL attached.

## What is needed from a human

1. **The Care & Bloom brand kit and claims list, in one request to the client.** Both come from the
   same person. The claims list is already an open blocking decision, and CB-09 went live with no
   recorded claims check — so this is the ask that closes two problems at once.
2. **Paste six Drive links**, set each `Access`, set `Last verified` to today.
3. **Backfill the folder link onto CB-07, 09, 10, 11, 12, 13.**
4. **Then announce the handoff rule** in Slack, once.
