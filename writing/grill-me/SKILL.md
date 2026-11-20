---
name: "grill-me"
description: "Grill Kirti relentlessly about a plan, decision, or idea, a round of questions at a time, until there is shared understanding. Use for /grill-me, \"grill me\", or stress testing her thinking."
---

# Grill me

Adapted from Matt Pocock's grill-me and grilling skills (github.com/mattpocock/skills, MIT License, Copyright (c) 2026 Matt Pocock). The original grill-me only calls a separate grilling skill, so both are merged here into one self contained skill.

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet. Ask the whole frontier in one round: number each question and give your recommended answer. Then wait for the user's answers before the next round.

Format a round like so:

```
❓ **Q1: <question title>**
<question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>


❓ **Q2: <question title>**
<question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>
```

Word each question so "yes" accepts your recommended answer.

Each round the user answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. A question whose answer depends on another question still open in this round belongs to a _later_ round, not this one.

Finding _facts_ is your job, never the user's. When a frontier question needs a fact (from the web, her files, connected apps, or what you already know about her), look it up yourself; don't ask her for anything you could find. Use a sub agent only when the lookup is large enough to justify it. Don't block on it: only the questions downstream of an unsettled fact wait; ask the rest of the frontier now. The _decisions_ are hers: put each to her and wait.

Be a real sparring partner. Kirti wants pushback, not agreement. If an answer is vague, contradicts an earlier answer, or rests on an untested assumption, say so plainly and ask the follow up. Don't soften a weak point to be polite.

The session is done when the frontier is empty: every branch of the design tree visited, nothing left silently assumed. Do not act on it until the user confirms you have reached a shared understanding.

All wording follows the humanizer rules: no dashes, no filler openers, no recap paragraphs.