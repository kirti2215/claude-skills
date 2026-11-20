---
name: "llm-council"
description: "Run a decision, idea, or draft through a council of 5 advisors who answer independently, peer review each other anonymously, and end in a chairman verdict. Use for 'council this', 'run the council', 'pressure test this', 'stress test this', 'debate this'."
---

# LLM Council

Built by Ole Lehmann (github.com/aiwithremy/claude-skills-llm-council), adapted from Andrej Karpathy's LLM Council (github.com/karpathy/llm-council). Karpathy sends one question to several different models, has them review each other anonymously, and has a chairman write the final answer. This skill does the same inside Claude, using sub agents with five different thinking styles in place of different models.

Adapted for Kirti: output follows her writing rules (no dashes, no contractions, humanizer rules), and the council runs only when she asks for it.

## When to run it

Run the council when Kirti uses a trigger phrase: "council this", "run the council", "war room this", "pressure test this", "stress test this", "debate this".

If she brings a real decision with stakes and several options ("I am torn between", "which option", "is this the right move") but uses no trigger phrase, answer normally and offer the council in one line. Do not start it unasked. One session uses 11 sub agent runs.

Good council questions:

* "Should I take the contract role or keep holding out for full time?"
* "Which of these three positioning angles is strongest?"
* "Here is my resume summary. What is weak?"
* "Should I lead my outreach with the AWS story or the AI workflows?"

Do not council these. Just answer them:

* Factual lookups with one right answer
* Creation tasks ("write me a post")
* Processing tasks ("summarize this article")

If she already knows the answer and wants validation, the council will probably say things she does not want to hear. That is the purpose.

## The five advisors

These are thinking styles that pull against each other. They are not job titles.

1. **The Contrarian.** Looks for what is wrong, what is missing, what will fail. Assumes there is a fatal flaw and tries to find it. If everything looks solid, digs deeper. This is the friend who asks the questions she is avoiding.
2. **The First Principles Thinker.** Ignores the surface question and asks what she is really trying to solve. Strips away assumptions and rebuilds the problem. Sometimes the most useful output is "you are asking the wrong question".
3. **The Expansionist.** Looks for upside everyone else is missing. What could be bigger? What adjacent opportunity is hiding? What is undervalued? Does not weigh risk, because the Contrarian covers that.
4. **The Outsider.** Has zero context about her, her field, or her history. Responds only to what is on the page. Catches the curse of knowledge: things obvious to her and confusing to everyone else.
5. **The Executor.** Cares about one thing: can this be done, and what is the fastest path? Asks "what do you do Monday morning?" If an idea has no clear first step, says so.

The tensions: Contrarian against Expansionist (downside against upside). First Principles against Executor (rethink it against just do it). The Outsider keeps the other four honest.

## How a session works

### Step 1: gather context and frame the question

First, collect context. Use what is already in the conversation, files she attached or referenced, and relevant project files or memory (for example her experience bank or master resume for a resume question). Spend very little time here. Look for the two or three sources that let advisors give specific advice.

Then reframe her question as a clear, neutral prompt all five advisors receive. Include:

1. The core decision or question
2. Key context from her message
3. Key context from files (constraints, past results, real numbers)
4. What is at stake

Do not add an opinion or steer it. If the question is too vague to frame, ask one clarifying question, then proceed.

### Step 2: convene the council (5 sub agents in parallel)

Spawn all five advisors in one message so they run in parallel and cannot see each other. Sequential runs let earlier answers bleed into later ones.

Advisor prompt template:

```
You are [Advisor Name] on an LLM Council.

Your thinking style: [advisor description from above]

A user has brought this question to the council:

---
[framed question]
---

Respond from your perspective. Be direct and specific. Do not hedge or try to be balanced. Lean fully into your assigned angle. The other advisors cover the angles you are not covering.

Keep your response between 150 and 300 words. No preamble. Go straight into your analysis.
```

For the Outsider, strip background about Kirti from the framed question where possible, so the response comes from a cold reader.

### Step 3: anonymous peer review (5 sub agents in parallel)

Collect the five responses. Label them Response A through E, with the mapping from advisor to letter shuffled so position gives nothing away. Remove any line where an advisor names its own role.

Spawn five new reviewers in one message. Each sees all five anonymized responses.

Reviewer prompt template:

```
You are reviewing the outputs of an LLM Council. Five advisors independently answered this question:

---
[framed question]
---

Here are their anonymized responses:

**Response A:**
[response]

**Response B:**
[response]

**Response C:**
[response]

**Response D:**
[response]

**Response E:**
[response]

Answer these three questions. Be specific. Reference responses by letter.

1. Which response is the strongest? Why?
2. Which response has the biggest blind spot? What is it missing?
3. What did ALL five responses miss that the council should consider?

Keep your review under 200 words. Be direct.
```

### Step 4: chairman synthesis

One agent (or the main session) receives the framed question, all five advisor responses with names restored, and all five peer reviews.

Chairman prompt template:

```
You are the Chairman of an LLM Council. Synthesize the work of 5 advisors and their peer reviews into a final verdict.

The question brought to the council:

---
[framed question]
---

ADVISOR RESPONSES:

**The Contrarian:**
[response]

**The First Principles Thinker:**
[response]

**The Expansionist:**
[response]

**The Outsider:**
[response]

**The Executor:**
[response]

PEER REVIEWS:
[all 5 peer reviews]

Produce the verdict using this exact structure:

## Where the council agrees
[Points several advisors reached independently. These are high confidence signals.]

## Where the council clashes
[Real disagreements. Present both sides. Explain why reasonable advisors disagree. Do not smooth them over.]

## Blind spots the council caught
[Things that only came out in peer review.]

## The recommendation
[A clear, direct recommendation with reasoning. "It depends" is not an answer. You may side with a lone dissenter if that reasoning is strongest.]

## The one thing to do first
[A single concrete next step. One thing, not a list.]

Write in plain language. Do not use em dashes, en dashes, or contractions. Do not invent facts or numbers that are not in the question.
```

### Step 5: present the verdict in chat

Present the verdict in the conversation as markdown under the heading "Council verdict: [short topic]", with the five sections above. Keep it scannable. Do not create a document, HTML report, or file unless Kirti asks for one.

Before showing it, apply her writing rules to the verdict: no dashes of any kind, no contractions, no AI writing patterns (run the humanizer rules).

Offer the five raw advisor responses if she wants to see them. Do not paste them by default.

### Step 6: transcript (only on request)

Save a transcript only if she asks.

## Rules that matter

* Always run all five advisors in parallel, and all five reviewers in parallel.
* Always anonymize before peer review. Reviewers who know the roles defer to a style instead of judging the argument.
* The chairman may disagree with the majority and must explain why.
* Advisors and chairman work only from real facts in the framed question. For resume or outreach questions, nobody invents a metric. Missing facts become questions for Kirti.
* Limit to be honest about: all five advisors are the same underlying model. The council widens the angles on a question. It does not give the independent check that different models from different companies would.