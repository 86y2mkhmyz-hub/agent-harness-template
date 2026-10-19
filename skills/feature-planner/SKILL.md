---
name: feature-planner
description: Turns a rough Fibrs app feature idea into a clear, approvable plan with design mockups before anything is built. Use whenever the user describes a new feature, screen, idea or change for the app ("I want users to…", "what if the app could…", "add a screen for…", "plan this feature", "new idea"), or asks to see a mockup or design for something.
---

# Feature planner

## Goal

A plain-English feature plan plus mockups the user approves before any code is written.

## Steps

1. **Understand the idea.** If it's clear enough, go to step 2. If it's vague or could mean very different things, ask max 3 short clarifying questions first, one message.
2. **Write the plan** (see Output format). Use plain English, no jargon — the user has no coding experience.
3. **Make the first mockup: clickable.** A single self-contained HTML file the user can open in a browser and tap through screen by screen (phone-sized frame, iPhone look). Save to `output/mockups/<feature-slug>-v1.html`.
4. **Collect feedback and iterate:**
   - **Major change** (new screens, different structure, layout or flow) → new clickable mockup.
   - **Small edits** (colours, text, spacing, one element) → quick picture mockup: a single static screen (HTML, or a PNG screenshot of it). Number versions `-v2`, `-v3`…
   - Update the plan to match after each round.
5. **Final look.** Once the user is happy with all edits, make one final clickable mockup with every change applied: `output/mockups/<feature-slug>-final.html`.
6. **Ask:** "Shall I start building this?" Only start if the user says yes. Never spend money or publish anything without asking.

## Design standards (every mockup)

- Easy to use: obvious next step, few taps, large touch targets.
- Polished, clean, luxurious: generous spacing, restrained colour palette, elegant typography, subtle motion.
- The interactive muscle diagram must be intuitive: clear tap targets, obvious selected state, readable labels.

## Output format

Save the plan to `output/plans/<feature-slug>.md` with these sections:

1. **What it does** — 1-2 simple sentences.
2. **Who it's for and why** — the user and the benefit to them.
3. **How it works, step by step** — what the user sees and taps, screen by screen.
4. **Design** — layout, colours, fonts, the luxurious feel.
5. **Muscle diagram connection** — how this feature uses or links to the diagram.
6. **Effort** — easy / medium / hard, and a rough time estimate, with a one-line reason.
7. **Costs** — anything that might cost money (paid tools, services, accounts). "None" if none.
8. **Decisions for you** — open questions to answer before building.

In chat, show a short summary of the plan and the link/path to the mockup.

## Example

**Input:** "I want users to tap a muscle and see exercises for it."
**Output:** `output/plans/muscle-tap-exercises.md` with all 8 sections + `output/mockups/muscle-tap-exercises-v1.html` (clickable: diagram screen → tap biceps → exercise list → exercise detail).
