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

## n8n Environment Variables

```text
APIFY_TOKEN=
APIFY_UPWORK_ACTOR_ID=
```

## Compliance Rule

Prefer official APIs and public employer ATS feeds first. Use Apify only in ways that respect the target site's terms, access controls, and rate limits.

