---
name: competitor-check
description: Researches how top fitness apps handle a feature, compares them with Fibrs' idea or plan, and returns concrete ways for Fibrs to stand out. Use when the user asks how competitors or other apps do something, wants a competitor comparison, or asks how to make a feature stand out.
---

# Competitor check

**Input:** a feature idea, or an existing plan in `output/plans/`
**Output:** `output/research/<feature-slug>-competitors.md`

## Steps

| # | Who | Does | Hands over |
|---|---|---|---|
| 1 | `researcher` subagent | Researches how 4-6 leading fitness apps handle this feature (e.g. Strava, Fitbod, Strong, Hevy, Nike Training Club, Apple Fitness+, plus any app known for muscle maps). For each: what it does, what users like, what users complain about (App Store reviews, Reddit), and whether it's free or paid. Sources for every fact | research notes |
| 2 | `writer` subagent | Writes the report (see Report structure), comparing the apps with Fibrs' idea or plan | draft report |
| 3 | `critic` subagent | Checks the report: is it concrete, sourced and useful for decisions? `ship` or `revise` + max 3 fixes | feedback |
| 4 | `writer` subagent | If `revise`: applies the fixes, back to step 3 | final report |

## Report structure

1. **The feature** in one sentence
2. **Comparison table:** app · how it does it · strengths · weaknesses · free/paid
3. **What users wish existed** — the gaps that keep coming up in reviews
4. **How Fibrs can stand out** — max 5 ideas, each tied to Fibrs' strengths: ease of use, luxurious design, the interactive muscle diagram
5. **What to avoid** — mistakes competitors made
6. **Sources**

## Rules

- Each step is its own subagent. Pass only the handover, not the whole chat.
- Never invent facts. Anything not verified gets left out or marked `[unverified]`.
- Max 2 review loops, then stop and show the result.
- Save the final report to the output path, then show: the top 3 standout ideas, the critic's last verdict, and the file path.
- Offer to feed the standout ideas into the `feature-planner` skill or the `feature-brief` workflow.
