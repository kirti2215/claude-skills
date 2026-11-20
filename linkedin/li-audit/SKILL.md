---
name: "li-audit"
description: "Audit Kirti's published LinkedIn posts to find what actually worked and what to stop. Use when she pastes post analytics or past posts and asks what's working or why a post flopped."
---

# li-audit

Adapted from Jake Schincariol's linkedin-agent-skill (MIT). Every LinkedIn rule is a guess until her own posts confirm it. Her last 20 to 30 posts are the evidence.

## Input

Ask for whichever she has:

* The post analytics export (LinkedIn Analytics, Content, Export) as a CSV.
* Screenshots per post with impressions, reactions, comments and reposts.
* Or just the posts with reaction counts, enough for a first pass.

If she knows which li-post hook formula each post used, include it.

## What to measure

Raw impressions mostly reflect follower count. Compute these instead and show the working:

* Engagement rate: (reactions + comments + reposts) / impressions. Did the post earn its reach?
* Comment ratio: comments / reactions. Did it start a conversation or just get a nod?
* Reach multiple: impressions / follower count. Did it travel past her existing audience?
* Save or send rate, if available.

Rank by engagement rate and reach multiple, not impressions.

## Find the pattern

Put the top 5 and bottom 5 side by side and look for what separates them:

* Hook formula
* Format (text, document, image, video, newsletter)
* Length
* Theme (security, AI building, cloud GTM, Strategy Lens topics)
* Whether she replied to comments in the first hour
* Day and time, checked last and only if nothing else explains it

State each finding as a claim with the evidence and a confidence level. With 30 posts a pattern can show; with 6 it cannot, so say that instead of inventing one. Be willing to conclude something she will not like.

## Output

Top 5 and bottom 5 with their metrics, then numbered findings, then one STOP line and one DO MORE line. Hand the conclusions to li-plan so next week's plan uses her own evidence. Humanize the text and use no dashes.