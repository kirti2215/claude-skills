---
name: "li-repurpose"
description: "Turn one long asset (a Strategy Lens article, transcript, talk or call summary) into four to six standalone LinkedIn posts. Use when Kirti wants to repurpose an article or recording into posts."
---

# li-repurpose

Adapted from Jake Schincariol's linkedin-agent-skill (MIT). One good long asset usually contains four to six posts. Most people pull out one and waste the rest.

## Input

An article (often a Strategy Lens edition), transcript, script or call summary. If she gives a URL that cannot be read, ask her to paste the text. Read the whole thing before extracting anything.

## Extract, do not summarise

A summary is not a post. Pull out the things that stand alone:

* Claims: sentences that would start an argument.
* Numbers: every figure, cost, duration or percentage.
* Stories: moments with a person, a scene and a cost.
* Mechanisms: "the way this works is" explanations, such as how a Skill or Loop is built.
* Mistakes: admissions of something that went wrong.
* Lines: sentences already quotable as they are.

List what you found, with counts, before writing anything. If the asset yields fewer than four items, say it is thin.

## Build the week

Each extract becomes one post that stands completely on its own. The reader has not read the article. Never write "as I mentioned in my latest article" in the post body; a link can go in the first comment.

Assign a different hook formula from li-post to each. Order them so the strongest claim goes first, the story midweek, and the mechanism post last.

## Output

The source, what was found with counts, and a week plan (day, hook number, angle). End with: say "write Tuesday" and I will draft it. Draft one post at a time on request through li-post and the humanizer skill, with no dashes. Do not dump all posts at once.