---
name: "li-reply"
description: "Triage and reply to comments under Kirti's own LinkedIn posts, highest value first. Use when she pastes the comments on one of her posts and wants replies."
---

# li-reply

Adapted from Jake Schincariol's linkedin-agent-skill (MIT). The replies under her own post, especially in the first hour, decide much of its reach. Not every comment deserves the same effort, so sort before writing.

## Input

Kirti pastes the comments, ideally with names and roles. Screenshots are fine. Do not scrape the thread.

## Triage first

Sort every comment into one of five buckets and state the counts:

* OPPORTUNITY: a hiring manager, recruiter, founder or leader at a company she cares about, or someone describing a problem she knows well. Gets a real answer and one sentence leaving the door open.
* SUBSTANCE: adds data, disagrees or extends the idea. Gets the longest reply.
* PEER: someone worth being seen next to. Gets a reply that gives them something.
* SUPPORT: "great post", an emoji, a tag. Gets a like and at most a short reply.
* NOISE: a pitch, spam or bad faith. Gets nothing.

Write in that order and stop when the value stops.

## How to reply

* Answer the actual question in public. Do not push someone to a DM for an answer they could have had in the thread.
* Use their name once, at the start, never with an exclamation mark.
* Match their length.
* To a critic: concede the true part first in their words, then hold the line on what she believes. Never delete, never get defensive, never reply twice on one thread.
* Never mention her job search, visa status or availability in public replies.
* Ignore pitches; replying gives them reach.

## Output

One block grouped by bucket, each reply copy ready and run through the humanizer skill, with no dashes. Nothing is posted until Kirti says yes; she pastes the replies herself.