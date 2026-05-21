# Opportunity Data Model

Use this object shape between n8n nodes, Google Sheets, Zoho CRM, and future MCP tools.

## Opportunity

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| `external_id` | string | yes | Stable hash or source ID. Used for deduplication. |
| `source` | string | yes | LinkedIn, Indeed, Lever, Greenhouse, Wellfound, Upwork, company site, etc. |
| `source_url` | string | yes | Canonical posting URL. |
| `title` | string | yes | Job/project title. |
| `company_name` | string | yes | Normalized company name. |
| `location` | string | no | City, country, remote, hybrid. |
| `region` | string | no | Germany, Berlin, London, Remote, etc. |
| `description` | string | no | Cleaned posting text. |
| `employment_type` | string | no | Full-time, contract, freelance, internship. |
| `salary_min` | number | no | Optional estimate. |
| `salary_max` | number | no | Optional estimate. |
| `currency` | string | no | EUR, GBP, USD, CHF, AED, SGD. |
| `posted_at` | date | no | Source posting date if available. |
| `discovered_at` | datetime | yes | Pipeline discovery timestamp. |
| `score` | number | no | 0-100 OpenAI score. |
| `priority` | string | no | Low, Medium, High, Critical. |
| `stage` | string | yes | Discovered, Evaluated, High Priority, Applied, Interview, Offer, Rejected, Archived. |
| `strengths` | string | no | AI-generated strengths. |
| `risks` | string | no | AI-generated risks. |
| `positioning` | string | no | Suggested application angle. |
| `next_action` | string | no | Recommended action. |
| `raw_payload` | object | no | Raw source response for debugging. |

## Company

| Field | Type | Notes |
| --- | --- | --- |
| `company_name` | string | Primary key candidate. |
| `website` | string | Main company URL. |
| `industry` | string | Trading, fintech, AI infra, crypto, prediction markets, etc. |
| `region` | string | Main hiring region. |
| `strategic_relevance` | number | 0-100 company-level fit. |
| `notes` | string | Accumulated research notes. |

## Deduplication Key

Use this fallback order:

1. Source-native job ID.
2. Canonical URL.
3. Hash of `lower(company_name) + lower(title) + lower(location)`.

