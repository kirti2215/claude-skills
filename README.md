# claude-skills

A personal library of Claude skills built for strategy, GTM, job search, and LinkedIn — by a practitioner, for a practitioner.

Each skill is a reusable instruction set that runs inside Claude (Cowork or Claude Code). Invoke with `/skill-name` or by describing what you need.

---

## Structure

```
claude-skills/
├── linkedin/       11 skills for content, engagement, and outreach
├── resume/         5 skills for job search and resume work
├── gtm/            3 skills for campaigns, launches, and sales prep
└── writing/        3 skills for drafting, thinking, and voice
```

---

## LinkedIn (`/linkedin`)

| Skill | What it does |
|---|---|
| [li-post](linkedin/li-post/) | Write a post from a raw idea using 21 hook formulas |
| [li-plan](linkedin/li-plan/) | Plan your LinkedIn week — what to post, when, who to engage |
| [li-carousel](linkedin/li-carousel/) | Write slide-by-slide copy for a LinkedIn document post |
| [li-comment](linkedin/li-comment/) | Write thoughtful comments on other people's posts |
| [li-reply](linkedin/li-reply/) | Triage and reply to comments on your own posts |
| [li-inbox](linkedin/li-inbox/) | Triage DMs and connection requests, draft replies |
| [li-dm](linkedin/li-dm/) | Write connection notes and DM follow-up sequences |
| [li-audit](linkedin/li-audit/) | Audit your past posts to find what actually worked |
| [li-repurpose](linkedin/li-repurpose/) | Turn a long asset into 4–6 standalone posts |
| [li-profile](linkedin/li-profile/) | Score and rewrite your LinkedIn profile for recruiter discovery |
| [li-human](linkedin/li-human/) | Final AI-tell scan before you post anything |

---

## Resume & Job Search (`/resume`)

| Skill | What it does |
|---|---|
| [jobfinder](resume/jobfinder/) | Run job search across 4 streams with sponsorship as a hard filter |
| [resume-tailor](resume/resume-tailor/) | Tailor your resume to a specific job posting |
| [resume-ats-check](resume/resume-ats-check/) | Check ATS parsing and keyword coverage against a JD |
| [resume-bullet-writer](resume/resume-bullet-writer/) | Rewrite bullets to show defensible achievements |
| [resume-quantifier](resume/resume-quantifier/) | Discovery questions to surface real numbers from your experience |

---

## GTM & Strategy (`/gtm`)

| Skill | What it does |
|---|---|
| [gtm-sales-enablement](gtm/gtm-sales-enablement/) | Account-specific pitch, discovery questions, objection responses |
| [gtm-product-launch-planner](gtm/gtm-product-launch-planner/) | Full launch package: messaging, personas, FAQ, enablement |
| [gtm-regional-campaign-builder](gtm/gtm-regional-campaign-builder/) | Regional campaign brief with narrative, segments, pipeline model |

---

## Writing & Thinking (`/writing`)

| Skill | What it does |
|---|---|
| [humanizer](writing/humanizer/) | Strip AI tells from any draft so it reads human |
| [grill-me](writing/grill-me/) | Hard questions on any plan or idea until it holds or breaks |
| [llm-council](writing/llm-council/) | 5 independent advisors + peer review + chairman verdict |

---

## How to use

These skills are installed as Claude plugins. Invoke any skill with `/skill-name` in a Claude session, or describe what you need and Claude will trigger the right one.

To install: import the SKILL.md content into Claude via the skill creator, or install the plugin directly if published.

