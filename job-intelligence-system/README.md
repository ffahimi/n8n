# AI-Powered Job & Opportunity Intelligence System

Personal opportunity intelligence infrastructure using n8n, Zoho CRM, MCP, and OpenAI.

## MVP Goal

Build the first complete loop:

1. Discover relevant jobs and projects.
2. Normalize and deduplicate opportunities.
3. Score each opportunity with OpenAI.
4. Save results to Google Sheets.
5. Push qualified opportunities into Zoho CRM.
6. Generate a daily priority report.

## Project Layout

```text
job-intelligence-system/
├── docker/
├── workflows/
├── prompts/
├── reports/
├── logs/
├── exports/
├── latex/
├── scripts/
└── docs/
```

## First Run

1. Copy the environment template:

```bash
cp docker/.env.example docker/.env
```

2. Fill in the values in `docker/.env`.

3. Start n8n:

```bash
cd docker
docker compose up -d
```

4. Open n8n at:

```text
http://localhost:5678
```

5. Import:

```text
workflows/berlin-opportunity-intelligence-v1.json
```

For the Apify Upwork test, import:

```text
workflows/apify-upwork-intelligence-v1.json
```

6. Create the required n8n credentials:

- OpenAI API
- Google Sheets OAuth2
- Zoho OAuth2 or Zoho CRM credential

Optional:

- Set `UPWORK_POLL_URLS` for Upwork freelance search URL polling.

## MVP Data Model

The canonical opportunity object is documented in:

```text
docs/data-model.md
```

## Scoring Prompt

The OpenAI scoring prompt is in:

```text
prompts/opportunity-scoring.md
```

## Zoho Setup

Recommended CRM module and field setup is in:

```text
docs/zoho-crm-setup.md
```

The enrichment plan for turning leads into Accounts, Deals, Contacts, and Tasks is in:

```text
docs/zoho-enrichment-plan.md
```

The source rollout and implementation sequence is in:

```text
docs/source-and-zoho-implementation-plan.md
```

The later Apify integration path is in:

```text
docs/apify-roadmap.md
```
