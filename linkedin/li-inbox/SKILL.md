---
name: "li-inbox"
description: "Triage Kirti's LinkedIn inbox: sort pasted DMs and connection requests into opportunities, recruiters, peers, asks and spam, and draft the replies worth sending."
---

# li-inbox

Adapted from Jake Schincariol's linkedin-agent-skill (MIT). Most of an inbox is noise, and the cost is that the important messages wait a week. This separates them and drafts only what is worth sending.

## Input

Kirti pastes the messages or screenshots. Do not log into her account or read the inbox with a browser.

## Sort into five

* RECRUITER: a role, company or hiring conversation. Highest priority while she is job searching. Reply today.
* OPPORTUNITY: a hiring manager, founder, leader at a target company, or a referral or intro offer. Reply today.
* PEER: someone in her field with something real to say. Reply this week.
* ASK: wants advice, time or an intro. Reply if it is cheap and specific; decline warmly in one sentence if not.
* SPAM: agency pitches, automated sequences, "quick question" with no question. Archive, no reply.

Print the counts first.

## Detecting a sequence

Automated outreach has a shape: a generic invite note, a message minutes after accepting, "I noticed you're in {industry}", a calendar link in message one, a bump exactly four days later. Mark it SPAM and say which tell gave it away.

## Replies

* RECRUITER: if the role fits, reply with interest and ask what the message left out: level, team, location or remote policy, and next steps. Never raise visa sponsorship or work authorization in the message.
* OPPORTUNITY: answer what they asked, show she knows what their company does, and propose one small next step.
* ASK: if it takes under ten minutes, do it. For "can I pick your brain", give the one useful answer in the reply.
* Declines are short, warm and final.

Follow her outreach rules: no shorthand (write product marketing, go to market), no stock phrases like "I'd welcome", no generic compliments.

## Output

Grouped by bucket with counts first, drafts only for the buckets that get replies, each run through the humanizer skill with no dashes. Kirti sends them herself.