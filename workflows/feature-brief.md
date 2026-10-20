---
name: feature-brief
description: Turns a Fibrs feature idea into an approved plan, a reviewed clickable mockup and a polished one-page PDF brief to share with a designer, developer or investor. Use when the user asks for a "feature brief", a shareable summary or PDF of a feature, or to take an idea "all the way" to a brief.
---

# Feature brief

**Input:** a feature idea (e.g. "tap a muscle to see exercises for it")
**Output:**
- `output/plans/<feature-slug>.md` (full plan)
- `output/mockups/<feature-slug>-final.html` (final clickable mockup)
- `output/briefs/<feature-slug>.md` + `output/briefs/<feature-slug>.pdf` (one-page brief)

## Steps

| # | Who | Does | Hands over |
|---|---|---|---|
| 0 | `competitor-check` workflow (optional) | If the user wants it, or the idea is a big new feature, run it first | standout ideas |
| 1 | Ramy, with the `feature-planner` skill | Writes the 8-part plan + first clickable mockup (uses step 0's standout ideas if there are any) | plan + mockup path |
| 2 | `design-critic` subagent | Reviews the mockup: verdict + top 3 fixes | feedback |
| 3 | Ramy + the user | Show mockup and feedback side by side; the user picks the fixes. Apply them (picture mockup for small edits, clickable for big ones), then back to step 2. Repeat until the user is happy | approved design |
| 4 | Ramy | Makes the final clickable mockup and updates the plan to match | final plan + mockup path |
| 5 | `writer` subagent | Turns the final plan into a one-page brief (see Brief structure) in plain English | brief draft |
| 6 | `critic` subagent | Checks the brief: `ship` or `revise` + max 3 fixes | feedback |
| 7 | `writer` subagent | If `revise`: applies the fixes, back to step 6 | final brief |
| 8 | Ramy, with the `doc-creator` skill | Builds the branded PDF from the final brief | PDF path |

## Brief structure

1. Feature name + one-sentence summary
2. The problem it solves and who it's for
3. How it works (3-5 steps, what the user sees and taps)
4. Design highlights (the luxurious feel, the muscle diagram's role)
5. Effort, costs and open decisions (short table)
6. Link/path to the final clickable mockup

## Rules

- Each subagent step gets only its handover, not the whole chat.
- Design rounds (steps 2-3) are the user's call: never apply a fix they didn't pick.
- Brief review (steps 6-7): max 2 loops, then stop and show the result.
- At the end show: the brief summary, the PDF path, the mockup path, and the critic's last verdict.
- Then ask "Shall I start building this?" — only build if the user says yes.
- Never send or share the PDF anywhere without asking.
