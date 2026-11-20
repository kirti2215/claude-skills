---
name: "resume-ats-check"
description: "Check Kirti's resume against a job posting for ATS parsing problems and keyword coverage. Use when she asks if a resume will pass ATS or wants a keyword match check."
---

# Resume ATS Check

Adapted from the resume-ats-optimizer skill in github.com/paramchoudhary/resumeskills (MIT license). The original opens with a claim that 75% of resumes are rejected by ATS. That figure has no source, so do not repeat it to her. Treat this skill as a parsing and keyword hygiene check, not a guarantee of a callback.

## Part 1: Parsing check

Run on the actual file, not on source text.

* File is a text based PDF. Extract the text and confirm it reads in the right order.
* Job title and dates extract on the same line or adjacent lines, in a sensible order. Her layout puts employer and location, then title and dates, in two column rows. If those rows are built as tables, confirm the extraction keeps each title next to its dates. If the order scrambles, rebuild the rows with a right aligned tab stop.
* Contact details sit in the body, not in a page header or footer.
* No text boxes, images, or multi column body text.
* Standard section names: Summary, Core Expertise or Skills, Experience, Education.
* One consistent date format: Month Year to Month Year.
* Standard font, body text large enough to read.
* Hyperlinks work and show readable text.

## Part 2: Keyword check

### Extract

Pull three groups from the posting:

* Hard skills and tools
* Functional skills (positioning, enablement, forecasting, program management)
* Industry and domain terms

Mark each as critical (repeated or listed under requirements) or secondary.

### Match

For each keyword, record:

* Exact match, close variant, or missing
* Where it appears (Summary, Core Expertise, Experience)

Report coverage as a count, for example 14 of 20 critical terms. Do not present the count as a predicted score or pass rate.

### Recommend

For each missing or variant keyword, choose one:

* She has done it and the resume uses another name: change to the posting's exact term.
* She has done it and the resume omits it: point to the experience bank entry and suggest where it fits.
* She has not done it: report it as a true gap. Do not add it.

Placement priority: Summary first, then Core Expertise, then Experience bullets. A critical term appearing two or three times is enough. Do not stuff.

## Guardrails

* Never add a skill, tool, or product name she has not worked with to raise coverage.
* Never weaken or delete an impact metric to make room for a keyword.
* A keyword edit must not change what a bullet claims she did.
* Use the resume-bullet-writer skill for any bullet that needs rewording.

## Output format

Give in chat:

1. Parsing problems found, each with a fix
2. Keyword table: term, critical or secondary, status, location
3. Coverage count for critical terms
4. Recommended wording changes, each with before and after
5. True gaps

No dashes in anything you write for her. Do not build a document or PDF unless she asks.