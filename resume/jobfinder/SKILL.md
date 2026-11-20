---
name: "jobfinder"
description: "Run Kirti's job search across four streams (big companies, startups, Y Combinator early stage outreach, contract roles), match each job's responsibilities against her experience, and rank with sponsorship as a hard filter."
---

# jobfinder

Finds fresh roles and outreach targets that fit Kirti, matches each job description against her real experience, and returns ranked lists in chat, one section per stream. Write everything without contractions and without dashes, following her humanizer rules.

The core idea: titles vary too much to trust. A role makes the list only when its responsibilities match work she has actually done, and every pick shows that evidence. There is no cap on how many roles appear: everything that passes the match bar is shown, and nothing weaker is added to fill space.

## 1. Run rules

1. Run only when Kirti asks. Never start a sweep on your own. She may ask for one stream or all four.
2. Spend cap: $5 per run. Set maxTotalChargeUsd on every Apify call. Most of the sweep should cost nothing, because career board APIs are free.
3. Her Apify plan allows only 5 actors at once and 16GB total memory. Set callOptions memory to 1024 and queue the rest as slots free up.
4. Save every raw result to a file in the workspace before processing, so nothing is lost if the conversation gets long. Process large results with Python, never by reading them into the conversation.
5. Resurfacing roles from earlier runs is fine. Do not go back months, and do not filter against past applications.
6. If an actor input fails validation, fetch its input schema with fetch-actor-details and fix the input.

## 2. Inputs to read before every run

1. Big company list: memory file areas/big-company-target-list.md in the project.
2. Startup list: memory file areas/startup-target-list.md in the project (five tiers, Cornell and UNC channels, visa signals). Tier 1 is the core: cybersecurity, databases and data infrastructure, identity. Drop companies found to be acquired.
3. Experience bank: project doc "experience bank", plus the current baseline resume (Kirti_Gupta_Cyber_Startup_November unless a newer one exists). This is the evidence library for matching.
4. LinkedIn export Connections.csv, if present, for network counts and named contacts.
5. Callback history (section 6), refreshed from Gmail when the Gmail connector is available.

Who she is: 8+ years across AWS, Deloitte and Maersk; UNC Kenan-Flagler MBA; product marketing and GTM, with security as the differentiator and cloud databases and AI as recent proof. Resume versions to assign: PMM, GTM Strategy, Cybersecurity, Program Management.

## 3. The four streams

### Stream A: Big and established companies

1. Companies: everything on the big company list. Mid size B2B companies there (Procore, ThoughtSpot, Amplitude, Box, Gong, Samsara) rank as high as the giants, since that is where most of her product marketing callbacks came from.
2. Sources: LinkedIn (section 8) filtered to these companies, plus career APIs where the company has one (Greenhouse, Ashby, Lever). Most big companies use Workday or custom pages; for the top names use web search or Chrome on their career site when LinkedIn coverage looks thin.
3. Lyft: strategy and operations roles only, not product marketing.
4. Lambda: included again at her request. She earlier said Lambda does not sponsor and she interviewed there in Aug 2026, so read each Lambda description for sponsorship language and flag the earlier concern on every Lambda role.

### Stream B: Startups

1. Companies: Tiers 1 to 3 of the startup list. Tier 4 only with a trigger or warm intro. Tier 5 only after checking citizenship, clearance and export control.
2. Sources: career board APIs (section 8), which are free and fast. Companies on Workday, Comeet or custom pages (for example Cyera, ScyllaDB, Spectro Cloud, Applied Compute, Glean, Retool, Wiz) get checked by web fetch or Chrome, prioritizing Tier 1 and explicit sponsors.
3. Note Cornell or UNC channel when a company has one.

### Stream C: Y Combinator and early stage outreach

This stream finds companies, not just postings. Any early stage B2B company at the point of hiring its first or second GTM person is a target, whether or not it has an opening.

1. Sources: the Y Combinator company directory and Work at a Startup (nomad-agent/ycombinator-was-scraper for postings: postedWithin "14d", schemaVersion nomad-agent-simple-inventory-search-v2, dedupe as an object {"enabled": false, "key": ""}), plus VC portfolio boards (Lightspeed, Sequoia, Kleiner, Felicis, Battery, Bain Capital Ventures, Costanoa) and recent funding news.
2. Filter: roughly the last six YC batches or seed to Series B; selling B2B in security, data and databases, AI infrastructure or developer tools; US based; about 5 to 100 people.
3. Signals to check: no marketing or GTM hire yet, founders doing sales themselves, a recent raise, a GTM or marketing posting, or founders posting about needing GTM help.
4. For each target return: company, one line on what it sells, batch or stage, team size, founder names (verified only), the GTM gap signal, why her background fits in one line, any posting link, and whether it is already on her startup list.
5. Sponsorship risk: tiny companies often cannot sponsor and may not be enrolled in E Verify, which STEM OPT requires. Mark sponsorship Unknown and suggest she confirm E Verify early in the conversation. Never put this in outreach drafts.
6. Add good new finds to the startup list only when she says so.

### Stream D: Contract and agency roles

1. Sources: ZipRecruiter (silentflow/ziprecruiter-scraper-ppe, postedWithin week, includeDetails false), LinkedIn agency posts, and firms she already works with: Aquent, Randstad, Insight Global, Judge Group, Cella, Collabera, 24seven.
2. Tag W2, 1099 or C2C when stated. Flag 1099 and C2C as likely incompatible with STEM OPT. W2 works only if the agency is enrolled in E Verify and signs the I 983; tell her to confirm with her DSO.
3. When an agency post repeats a role she can apply to directly, show the direct one.
4. Skip vague confidential client posts unless title and pay are a real match.

## 4. Hard filters (Streams A, B and D; Stream C uses its own filter)

1. Sponsorship: not an explicit no. Labels are Explicit yes, Restricted (explicit no), Unknown. Never guess.
2. Level: Senior PMM, Senior Technical PMM, PMM, Manager, Senior Manager, Strategy and Operations Lead, GTM Lead, Program Manager or Senior Program Manager. At startups also Founding PMM, First GTM Hire, Business Operations Lead and Chief of Staff when the scope matches. Staff titles are allowed but flagged. Associate Manager only when the scope is clearly strong, and flagged.
3. Drop: Director, Head of, VP, Principal, Senior Staff, Group PMM, Associate, Specialist, Analyst.
4. Pay: no minimum. Show posted pay so she can judge.
5. Function: the core of the job must be product marketing, GTM strategy and planning, GTM programs, enablement and readiness, competitive intelligence, or partner and alliance GTM.
6. Product: B2B, technical or enterprise. Drop consumer marketing.
7. Geography: San Francisco Bay Area first (San Francisco, Mountain View, Sunnyvale, Santa Clara, Palo Alto, San Jose, Menlo Park and nearby), Seattle, Bellevue and Redmond second, US remote third. Other US cities only for an exceptional match, and flagged. Hybrid or flexible preferred.
8. Exclusions: no AWS roles (she cannot go back). Ask before including Amazon roles outside AWS.
9. Red flags that remove a role: sales quota or account executive work, security clearance or US person requirement, events only field marketing, CRM admin or revenue operations analyst work, finance and FP&A, customer success, clinical or healthcare operations.

## 5. Responsibility match (the main step)

For every role that passes the filters, read the full job description. Do not score from the title.

1. Pull out the 5 to 8 real responsibilities and the must have requirements (years, domain, technical depth).
2. Map each responsibility to her evidence and mark it:
   1. Strong: she has done this directly, with a proof point.
   2. Partial: adjacent work that transfers.
   3. Gap: nothing in her history covers it.
3. A role needs Strong matches on at least half of its core responsibilities, and no Gap on a must have, to make the list. This bar, not a count, is what keeps the list tight.
4. Write one evidence line per pick that names the requirement and her proof. Example: "Wants competitive battlecards for security buyers; she built battlecards, TCO models and win/loss for 300+ sellers." If you cannot write that line, the role does not make the list.

Evidence library (confirm details against the experience bank before using):

1. Product marketing: enterprise positioning and message houses for executive, technical and practitioner buyers; launches; the Aurora DSQL readiness session for about 300 people.
2. Competitive intelligence: battlecards against MongoDB and Cassandra, TCO models, win/loss analysis, delivered through Highspot to 300+ sellers and solutions architects.
3. Campaigns and pipeline: 12 GTM workstreams, six campaigns, five GTM motions across NAMER, EMEA and ASEAN; $153.4M modernization pipeline across 447 opportunities; $86.3M GenAI pipeline; Nubank (118M+ customers); 400+ webinar attendees at 4.89/5.
4. Enablement and readiness: 7 enablement sessions with 487 attendees; Highspot content; the NoSQL newsletter.
5. GTM strategy and planning: annual strategy, gap to goal analysis, propensity based targeting with 2.3x per customer consumption growth, 40% reporting cycle reduction for 200+ sales teams.
6. Technical and POCs: AI fraud detection POCs with 3 financial institutions and about 20% better accuracy; Python, SQL, APIs; generative AI chatbot with 30% faster response.
7. Internal AI: four AI enabled GTM workflows.
8. Security: cloud IAM for millions of identities at Maersk (ForgeRock, OpenIDM, SailPoint, Kubernetes, Helm); ML anomaly detection with 1.5x faster incident response; GDPR assessment helping avoid about $20M in penalties; identity governance for a $30B UK financial institution; 40% vulnerability reduction.
9. Regulatory GTM: DORA.
10. Partner GTM: joint plays with the AWS ISV team for financial services ISVs.
11. Public AI work: three Agent Skills, four decision Loops, an AI agent IAM policy engine prototype, two articles.

## 6. Scoring out of 100

1. Responsibility match: 40.
2. Must have requirements met: 15.
3. Industry fit: 15. Security, cloud databases and data infrastructure, and AI infrastructure get full points equally. Developer tools, fintech and B2B SaaS get partial points.
4. Level and scope: 10.
5. Freshness: 10. Last 72 hours ranks highest; past 7 days is acceptable. Flag reposts, stale listings (200+ applicants or an old job ID) and duplicates.
6. Geography and work arrangement: 5.
7. Network and callback signal: 5. Count first degree connections from Connections.csv and name specific people.

Callback signal adds weight but never decides. Role families that have produced recruiter calls or interviews for her, as of Nov 2026 from her Gmail:

1. GTM strategy and planning: Adobe, Cisco Strategy and Planning Manager, DoorDash Sales Planning and Strategy, Uber.
2. Enablement, readiness and GTM programs: Cisco Product Readiness Manager, NetApp enablement, A-LIGN GTM Program Manager.
3. Product marketing at B2B companies of mid size: Procore, ThoughtSpot Competitive Intelligence, Middesk, Amplitude, commercetools, TapClicks, Bitmovin.
4. Partner and AWS ecosystem: Supabase AWS segment role, LinkedIn GTM operations, Lambda.

Refresh from Gmail when possible. A perfect responsibility match with no callback history still outranks a weak match in a callback family. Say the score is a judgment, not an ATS number.

## 7. Sponsorship

1. Sponsorship is a must have. Read every shortlisted description for sponsorship language.
2. For Unknown roles, check h1bdata.info by employer for the current or prior year, with the job title filter empty (it matches titles too strictly), and under the legal name (Teleport is Gravitational, Cursor is Anysphere, 1Password is AgileBits). Common names like Factory or Harvey can collide with other employers; flag that.
3. A filing count shows willingness, not a promise. Suggest confirming at the recruiter screen.
4. Explicit no roles go to a short skipped section only.
5. Never mention sponsorship or visa status in outreach drafts.

## 8. Source mechanics

1. Career board APIs (free):
   1. Greenhouse: boards-api.greenhouse.io/v1/boards/{token}/jobs?content=true
   2. Ashby: api.ashbyhq.com/posting-api/job-board/{name}?includeCompensation=true
   3. Lever: api.lever.co/v0/postings/{name}?mode=json
   4. Try each slug on all three; tokens are not always the company name. Keep a working token map in the workspace and reuse it.
2. LinkedIn, Apify actor cheap_scraper/linkedin-job-scraper:
   1. Search exact title phrases, not single words: "senior product marketing manager", "product marketing manager", "technical product marketing", "product marketing manager security", "GTM strategy", "strategy and operations manager", "go to market program manager", "enablement manager", "readiness manager", "competitive intelligence", "partner marketing manager", "alliances manager".
   2. Locations San Francisco Bay Area and Seattle, plus a US remote pass. publishedAt r604800. experienceLevel mid senior only (not director). saveOnlyUniqueItems true.
   3. excludeRecruitingAgencies only flags agencies; keep them and route them to Stream D.
   4. Pull jobDescription for every candidate, since the match step needs it.
   5. Expect throttling; note gaps in the run notes rather than padding the list.
3. H-1B lookups: h1bdata.info index.php?em={EMPLOYER}&job=&city=&year={YEAR}.
4. Dropped unless Kirti asks: Glassdoor (copies LinkedIn), Hiring Cafe (only with a hiring.cafe search link from her), Welcome to the Jungle, Himalayas.

## 9. Output (in chat only)

1. No spreadsheet or doc unless she asks; CO Career is her tracker.
2. No cap on count. Every role or target that passes the match bar is shown; nothing weaker is added to fill space. If a stream comes back thin, say so.
3. One section per stream, ranked separately so strong startup roles are not buried under big names:
   1. Streams A, B and D: the top 10 in each stream get full detail: company and role (linked), location, pay if posted, posted date and applicants, score, resume version, sponsorship label, the evidence line, any Partial or Gap worth knowing, and named connections. Every other passing role gets one line: linked role, location, pay if posted, score and the evidence line.
   2. Stream C: the top 10 targets in the full format from section 3, the rest one line each, all marked "open role" or "no role yet".
   3. Stream D roles also carry their employment type tag.
4. Close but no: up to 10 roles cut at the match step across streams, one line each on why.
5. Skipped for explicit no sponsorship: one line.
6. Companies to network with even without a matching role.
7. Hiring manager, recruiter or founder names only when verified.
8. Run notes: sources that failed or were throttled, companies whose boards could not be read, approximate Apify cost, and what to change next run.

## 10. What to avoid

1. Do not pad the lists. Show everything that passes, and only what passes.
2. Do not score from titles or keywords alone.
3. Do not suggest AWS roles, and do not present explicit no sponsorship roles as options.
4. Do not invent pay, dates, contacts, founder names, sponsorship policy or availability. Mark missing information as not listed.
5. Do not assume sponsorship from company size or past filings.
6. Do not run without her go ahead, and do not exceed $5.
7. No contractions and no dashes anywhere in the output.