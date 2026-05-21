# Apify Roadmap

Use URL polling now. Add Apify when simple HTTP polling becomes too brittle or when you need structured extraction from dynamic pages.

## Current MVP

```text
n8n cron
  -> configured poll URLs
  -> fetch HTML
  -> extract candidate job links
  -> normalize
  -> score
  -> Sheet / Zoho
```

This is enough to prove the business logic and Zoho enrichment model.

## When To Add Apify

Add Apify when you need:

- JavaScript-rendered page support
- Pagination
- Reliable field extraction
- Screenshots / evidence
- Proxy management
- Retry logic
- Structured actor outputs

## Future Apify Flow

```text
n8n cron
  -> Apify run actor
  -> wait for dataset
  -> fetch dataset items
  -> normalize into opportunity object
  -> dedupe
  -> OpenAI score
  -> Sheet / Zoho
```

## Current n8n Template

Import this workflow for the first Apify test:

```text
workflows/apify-upwork-intelligence-v1.json
```

It uses Apify's synchronous actor endpoint:

```text
/v2/acts/:actorId/run-sync-get-dataset-items
```

This is best for small tests because n8n receives dataset items directly. For larger scheduled runs, switch to async actor runs plus polling.

## n8n Environment Variables

```text
APIFY_TOKEN=
APIFY_UPWORK_ACTOR_ID=upwork-vibe~upwork-job-scraper
```

## Compliance Rule

Prefer official APIs and public employer ATS feeds first. Use Apify only in ways that respect the target site's terms, access controls, and rate limits.
