# Day 1 Runbook

## 1. Start Infrastructure

```bash
cd docker
cp .env.example .env
docker compose up -d
```

Open:

```text
http://localhost:5678
```

## 2. Import Workflow

Import:

```text
workflows/berlin-opportunity-intelligence-v1.json
```

## 3. Add Credentials

Create credentials in n8n:

- Google Sheets OAuth2
- Zoho CRM OAuth2

Set these in `docker/.env`:

```text
OPENAI_API_KEY
OPENAI_SCORING_MODEL
UPWORK_POLL_URLS
```

`UPWORK_POLL_URLS` is optional. If it is empty, the Upwork branch produces no items.

Restart n8n after changing env vars:

```bash
docker compose restart n8n
```

## 4. Prepare Google Sheet

Follow:

```text
docs/google-sheets-setup.md
```

## 5. Prepare Zoho

Follow:

```text
docs/zoho-crm-setup.md
```

## 6. Test

Run `Manual Test Trigger`.

Expected result:

- Search results pulled from Arbeitnow's Germany/EU job API.
- Freelance lead links pulled from configured Upwork poll URLs, if present.
- Jobs scored by OpenAI.
- All scored jobs appended to Google Sheets.
- Jobs with score >= 70 created as Zoho Deals.

## 7. Improve

After the first successful run:

1. Reduce or expand keywords.
2. Add one source at a time.
3. Review low-scoring false negatives.
4. Tune `prompts/opportunity-scoring.md`.
5. Add follow-up task creation in Zoho.
