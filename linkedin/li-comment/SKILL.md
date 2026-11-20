---
name: "li-comment"
description: "Write thoughtful comments on other people's LinkedIn posts using nine comment types. Use when Kirti pastes a post and wants a comment, or wants an engagement round across several posts."
---

# li-comment

Adapted from Jake Schincariol's linkedin-agent-skill (MIT). A good comment on a popular post is seen by more people than most of her own posts. A generic one is seen by nobody and costs credibility with the author.

## Input

Kirti pastes the post text, ideally with the author's name and role. Screenshots are fine. If she gives a URL that cannot be opened, ask her to paste the text. Never guess what a post said and never scrape the feed.

## The nine comment types

Pick by what the post actually is. Never default to the first one.

1. Add a datum: the post makes a claim she can support with a real number from her own work.
2. Add the missing case: the post is right but incomplete. "This holds until {condition}. Then..."
3. Respectful disagree: name the real agreement first, then the fork.
4. Extend one line: quote the strongest sentence, then build on it.
5. Ask the real question: the post skipped the hard part. One specific question.
6. The receipt: she has done the thing described. What happened, in two sentences.
7. The correction: a factual error. Be right, brief, kind and sure.
8. The reframe: right facts, wrong frame. "Another way to read this:"
9. The one liner: under 12 words, must be funny or true.

## Rules

* Two to four sentences. Longer reads as a hijack, shorter as filler.
* Never open with "Great post", "Love this", "So true", "Couldn't agree more", "This resonates", or the author's name with an exclamation mark.
* No emojis as openers.
* Never restate the post.
* One idea per comment.
* Say the specific thing. If the comment could sit under any post on the topic, rewrite it.
* Never invent experience or numbers for a receipt or datum comment. Use only what Kirti has actually done (AWS, Deloitte, Maersk, her AI builds, The Strategy Lens).

## Output

Two options of different types, labelled, plus one line on which to post and why. Run both through the humanizer skill first. No dashes; short comments are read closely and dashes stand out.

## Batch mode

For an engagement round, take 5 to 10 pasted posts in one message and return one comment each in a single block. Point out if she is commenting on the same few people every day.

## Never

Do not post comments or use a browser to publish on her behalf. This skill writes; Kirti posts.