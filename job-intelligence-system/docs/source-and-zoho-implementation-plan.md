# Source and Zoho Implementation Plan

This plan turns raw job/project discovery into a useful Zoho operating system.

## Source Priority

Use sources in layers, from easiest and cleanest to broadest and most exploratory.

| Priority | Source | Purpose |
| --- | --- | --- |
| 1 | Arbeitnow | Berlin/Germany/EU and remote tech roles. |
| 2 | Upwork URL polling | Freelance leads and proposal opportunities. |
| 3 | Greenhouse | Direct company career boards. |
| 4 | Lever | Direct company career boards. |
| 5 | Adzuna | Broad worldwide/EU aggregation with salary/location fields. |
| 6 | Ashby / Workable / Personio | Startup and EU company careers, especially Personio in Germany. |
| 7 | Google Custom Search / SerpAPI | Discovery when no clean API exists. |
| 8 | LinkedIn | Manual validation, networking, and application path only. |

## Why This Order

Arbeitnow and Upwork URL polling are fast to run and low-friction. Greenhouse and Lever are high-quality because they come directly from employers. Adzuna is useful, but it should enrich coverage rather than define the Berlin-first system. SerpAPI is powerful but noisier, so it belongs after direct APIs.

## Intake Workflow

```text
Daily cron
  -> source branches
  -> source-specific normalization
  -> common opportunity object
  -> dedupe
  -> AI scoring
  -> Google Sheets ledger
  -> Zoho enrichment for qualified leads
```

## Upwork URL Polling

The workflow reads `UPWORK_POLL_URLS` from the n8n environment.

Use one URL per line or comma-separated URLs:

```text
UPWORK_POLL_URLS=https://www.upwork.com/nx/search/jobs/?q=quant%20trading,https://www.upwork.com/nx/search/jobs/?q=betfair%20trading
```

Recommended searches:

- quant trading
- sports betting model
- python trading bot
- algorithmic trading
- betfair trading
- prediction market
- crypto trading bot
- machine learning finance

## Zoho Enrichment Rules

| Condition | Action |
| --- | --- |
| Any discovered lead | Append to Google Sheets. |
| Score >= 70 | Create/update Zoho Deal. |
| Score >= 75 or repeated company | Create/update Zoho Account. |
| Score >= 85 | Create urgent Task. |
| Freelance score >= 80 | Create proposal drafting Task. |
| Applied and stale for 7 days | Create follow-up Task. |
| Named recruiter/hiring manager exists | Create/update Contact. |

## Zoho Object Strategy

Deals answer:

```text
Should I act on this opportunity?
```

Accounts answer:

```text
Is this company strategically important over time?
```

Contacts answer:

```text
Who can I build a relationship with?
```

Tasks answer:

```text
What should I do next, and when?
```

## Enrichment Fields to Add Next

Add these fields once the first workflow runs:

- `Role Category`
- `Lead Type`
- `Remote Type`
- `Strategic Relevance`
- `Application Deadline`
- `Freshness`
- `ATS Source`
- `Company Relevance`
- `Follow-Up Due`
- `Application Asset Needed`

## Next n8n Build Steps

1. Add Account find/create before Deal creation.
2. Add Deal search by `External ID` before creating new Deals.
3. Add score-based Task creation.
4. Add Greenhouse scanner from target company slugs.
5. Add Lever scanner from target company slugs.
6. Add Adzuna as optional broad-market branch.
7. Add SerpAPI discovery only after direct APIs are stable.
8. Add MCP read-only queries over Zoho.
9. Add MCP write actions for tasks, stages, and application packets.
