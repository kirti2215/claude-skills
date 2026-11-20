---
name: "resume-quantifier"
description: "Ask Kirti discovery questions to help her recall real numbers behind her resume bullets. Use when she wants to quantify experience, jog her memory, or recover missing metrics."
---

# Resume Quantifier

Adapted from the resume-quantifier skill in github.com/paramchoudhary/resumeskills (MIT license). The original has two parts: discovery questions that help a person find metrics, and estimation techniques that fill in numbers when exact data is missing. This version keeps the discovery part in full. It changes the estimation part: reasoning toward a number is allowed as a way to help Kirti remember, but only a number she then confirms as true goes on a resume. The original also targets a metric in every bullet. That target is removed, because her resumes suffered from too many numbers, not too few.

## When to use

* She asks to quantify her experience, jog her memory, or recover missing metrics.
* A bullet has impact but no evidence of scale, and the experience bank has no number for it.
* A claim on a resume cannot be traced to the experience bank or master resume.

## Before asking anything

1. Read the project doc "experience bank", including its "Full impact metrics bank" and "Metrics and details to recover" sections.
2. Do not ask for numbers she has already confirmed.
3. Pick the bullets where a recovered number would matter most for the role she is targeting. Ask about those first.

## Metric categories to probe

* Money: revenue, pipeline, costs saved, budget, deal size
* Time: hours saved, cycle time, project duration, response time
* Percentages: growth, improvement, error reduction, conversion
* Volume and scale: users, identities, accounts, systems, projects, team size, regions
* Quality: satisfaction scores, accuracy, compliance, uptime
* Frequency: per week, per release, per quarter, cadence owned

## Discovery questions

For each accomplishment, choose from these. Make each question specific to her work, not generic.

Scale

* How many people, systems, accounts, or customers did this touch?
* How large was the team, and what was her part of it?
* How many regions or markets?

Impact

* What changed because of this work?
* What would have happened without it?
* What got faster, cheaper, or safer?

Comparison

* What did it look like before and after?
* What was the baseline, and who measured it?

Evidence

* Where would this number have been written down (a dashboard, a review document, an email, a performance review)?
* Who else would remember it?

## Role specific prompts

* Product marketing and GTM: pipeline influenced, opportunities, assets built, sellers reached, session attendance, win rate movement, adoption
* Security engineering: identities managed, systems integrated, incidents, response time before and after, vulnerabilities closed, release test coverage
* Consulting: markets covered, controls or data flows assessed, team size, timeline against plan, follow on work, audience for the readout

## How to run a round

* Ask in groups by employer, most relevant group first. Keep a round to about twelve questions.
* Tell her rough answers and "no idea" are both useful.
* If she is unsure, help her reason toward the figure out loud (for example, releases per month times hours of manual testing per release). Present the result as a question for her to confirm, never as a fact.

## What may go on a resume

* A number she states with confidence: yes.
* A number she reasons out and then confirms she can defend in an interview: yes, written with "about".
* A number she is guessing at, or one you calculated that she has not confirmed: no. Leave the bullet without it.
* A number that belongs to the team or the business: only with honest attribution such as "supporting" or "contributing to".

## After she answers

1. Sort each answer into confirmed, confirmed as approximate, or not usable.
2. Recommend which recovered numbers are worth adding. A bullet holds at most two or three numbers, so say which existing number would be displaced.
3. Use the resume-bullet-writer skill for any rewording.
4. Offer to add confirmed numbers to the experience bank so she does not have to recall them again. Update that doc only when she agrees.

## Style

No dashes in anything written for her. Full word forms, no contractions. Give results in chat and do not build a document or PDF unless she asks.