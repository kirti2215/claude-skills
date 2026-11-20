---
name: "li-human"
description: "Final AI tell scan on a finished draft, with a five check readout. Use after the humanizer skill has run, or when Kirti asks does this sound like AI or will this get flagged."
---

# li-human

Adapted from Jake Schincariol's linkedin-agent-skill (MIT). Kirti's humanizer skill is the main rulebook and always wins on any conflict. This is a last pass check on a finished draft, not a second set of writing rules.

The original version ships two Python scripts (humanize.py and detect.py) that compute real scores. They are not part of this skill. Without them, this check is a careful read, so never present its ratings as measured numbers or as a detector result.

## Step 1: Fingerprint scan

Find and remove:

* Any em dash, en dash, or hyphen used as a dash
* Curly quotes (replace with straight quotes) and the single ellipsis character (replace with three dots)
* Invisible characters: zero width spaces and joiners, soft hyphens, non breaking spaces, byte order marks. If text was pasted from another tool, mention that these can hide in it and suggest pasting through a plain text editor.

## Step 2: Structural flags

Flag each of these with the exact line, then rewrite it by hand keeping the meaning:

* "It's not just X, it's Y" and "not only X but also Y"
* Reflexive groups of three
* One word rhetorical question lines ("The result?")
* Rocket, fire, bulb, sparkle or dart emoji
* Hashtag walls
* Engagement bait ("Thoughts?", "Agree?", "Who else?")
* Every sentence or bullet the same length

## Step 3: Five check readout

Rate each as Strong, OK or Weak, with one line of reason:

* Burstiness: does sentence length vary?
* Specificity: are there real numbers, names and concrete details?
* Slop density: any stock AI vocabulary (delve, leverage, robust, seamless, crucial, testament, moreover)?
* Fingerprint: any dashes, curly quotes or invisible characters left?
* Voice: contractions, first person, no staged reveals?

If any check is Weak, fix that first and read again. If two rounds of fixes do not get there, the draft was written by formula; suggest a fresh draft instead of more passes.

## Be honest

This is not GPTZero, Originality or Turnitin and cannot predict their verdicts. Never tell Kirti a text is undetectable. The goal is writing a human reader trusts.

## Output

The cleaned text first, ready to copy, then the flags fixed and the five check readout. Never the readout alone.