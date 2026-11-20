---
name: "resume-tailor"
description: "Tailor Kirti's baseline resume to a specific job posting by changing emphasis and order, never facts. Use when she shares a job description and asks for a tailored version."
---

# Resume Tailor

Adapted from the resume-tailor skill in github.com/paramchoudhary/resumeskills (MIT license), tightened to match Kirti's project instructions. Where this skill and her project instructions differ, her project instructions win.

## Principle

Tailoring selects and orders true material. Think of her experience bank as a library and each resume as the shelf chosen for one employer. Nothing new gets written into the library during tailoring.

## Process

### Step 1: Analyze the job

* Extract required skills, preferred skills, and the role's main responsibilities.
* Note the company's priorities and the vocabulary it uses.

### Step 2: Map evidence

Build a short table: requirement, her matching evidence, where it lives in the baseline resume. Separate true gaps (she has not done it) from wording gaps (she has done it under a different name).

### Step 3: Preservation list

Before proposing any edit, list the accomplishments and metrics that must survive. Keep AWS full time, AWS internship, Maersk, Deloitte, education, STEM OPT, and projects unless she authorizes removal.

### Step 4: Adjust

* Summary: rewrite to mirror the role's main function, leading with AWS.
* Core Expertise: reorder so the most relevant terms come first. Add a posting keyword only when the resume proves it. Keep it to about two lines.
* Experience: reorder bullets so the most relevant leads each role. Swap in a stronger bullet from the experience bank when it fits better.
* Bullet language: use the posting's term when it truthfully names what she did.

Use the resume-bullet-writer skill for any bullet you rewrite.

## Truth line

Acceptable:

* Reordering true information
* Emphasizing relevant experience
* Using the posting's terminology where accurate
* Compressing mechanism to make room for outcomes

Not acceptable:

* Adding skills, tools, or products she has not worked with
* Changing or estimating numbers
* Upgrading verbs beyond her real ownership
* Changing a job title
* Moving a metric to a different accomplishment
* Describing a prototype or public project as a production system

## Scenario notes

* Startup target after big company experience: lead with work she built from scratch, cross functional range, and hands on technical work. Trim process heavy bullets.
* Security product marketing target: lead the earlier roles with IAM engineering and GDPR work she can discuss in depth. Do not add security terms to AWS bullets that were not security work.
* Strategy and operations target: lead with planning, business reviews, forecasting, and reporting evidence.

## Output format

Give these in chat, in this order:

1. What stays unchanged
2. Exact changes required, each with before, after, and reason
3. What would be lost
4. True gaps she should know about before applying

Do not rewrite the whole resume unless she asks. Do not build a document or PDF until she approves the wording and asks for it.

## Checklist before calling it ready

* Summary names the role's function
* Top Core Expertise terms match the posting's top requirements, each backed by evidence
* Each role's first bullet speaks to a main requirement
* All claims traced to the experience bank or her confirmation
* Three AI bodies of work still distinct: internal AWS workflows, Lex and Lambda chatbot, public portfolio
* Facts consistent with her other resume versions
* No dashes, no casual verbs, no bullet over two lines
* PDF only, distinct filename with role and month, rendered page inspected, links tested