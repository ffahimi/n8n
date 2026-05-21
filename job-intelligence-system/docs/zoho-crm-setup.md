# Zoho CRM Setup

## Recommended Modules

For the MVP, use standard modules where possible:

- `Accounts` for companies.
- `Contacts` for recruiters and hiring managers.
- `Deals` for opportunities.
- `Tasks` for follow-ups.

Later, add a custom module named `Job Opportunities` if standard Deals becomes awkward.

## Deal Pipeline

Create a pipeline named:

```text
Opportunity Intelligence
```

Stages:

```text
Discovered
Evaluated
High Priority
Applied
Interview
Offer
Rejected
Archived
```

## Deal Fields

Add these custom fields to Deals:

| Field | Type |
| --- | --- |
| `Source` | Picklist |
| `Source URL` | URL |
| `External ID` | Single Line |
| `AI Score` | Number |
| `Priority` | Picklist |
| `Location` | Single Line |
| `Region` | Picklist |
| `Employment Type` | Picklist |
| `Salary Min` | Currency |
| `Salary Max` | Currency |
| `Currency` | Single Line |
| `Posted At` | Date |
| `Discovered At` | Date/Time |
| `AI Strengths` | Multi-Line |
| `AI Risks` | Multi-Line |
| `Suggested Positioning` | Multi-Line |
| `Next Action` | Multi-Line |

## n8n Mapping

Map canonical opportunity fields to Zoho as:

| Canonical Field | Zoho Field |
| --- | --- |
| `title` | Deal Name |
| `company_name` | Account Name |
| `source` | Source |
| `source_url` | Source URL |
| `external_id` | External ID |
| `score` | AI Score |
| `priority` | Priority |
| `stage` | Stage |
| `location` | Location |
| `region` | Region |
| `strengths` | AI Strengths |
| `risks` | AI Risks |
| `positioning` | Suggested Positioning |
| `next_action` | Next Action |

## MVP Rule

Only push opportunities to Zoho when:

```text
score >= 70
```

Keep all discovered and evaluated opportunities in Google Sheets for review and tuning.

