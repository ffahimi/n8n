# Zoho Enrichment Plan

The goal is not to dump every lead into Zoho. Zoho should become the operating layer for high-signal opportunities, companies, contacts, follow-ups, and application outcomes.

## Core Rule

Use Google Sheets as the raw ledger. Use Zoho CRM as curated memory.

```text
All discovered leads -> Google Sheets
Score >= 70 -> Zoho Deal
Company seen repeatedly or score >= 75 -> Zoho Account enrichment
Recruiter/contact found -> Zoho Contact
Action needed -> Zoho Task
```

## Lead Types

| Source Type | Zoho Object | Reason |
| --- | --- | --- |
| Full-time job | Deal | Track as application opportunity. |
| Freelance project | Deal | Track as revenue opportunity. |
| Target company | Account | Store strategic company intelligence. |
| Recruiter / hiring manager | Contact | Relationship memory. |
| Follow-up / application action | Task | Execution layer. |

## Deal Enrichment

Every qualified opportunity should enrich the Deal with:

- Source and source URL
- AI score
- Priority
- Stage
- Location / remote status
- Role category
- Suggested positioning
- Strengths
- Risks
- Next action
- Estimated compensation or budget, if available
- Deadline or freshness signal

Recommended role categories:

- Quant Research
- Quant Developer
- Trading Engineering
- Sports Betting Quant
- Prediction Markets
- Crypto Trading
- AI/ML Engineering
- Low-Latency Infrastructure
- Options Trading
- Freelance Project

## Account Enrichment

When a company appears, enrich or create an Account with:

- Company name
- Website
- Industry category
- Hiring regions
- ATS source: Greenhouse, Lever, Ashby, Workable, Personio, other
- Strategic relevance score
- Known roles discovered
- Notes from job descriptions
- Last seen hiring date
- Number of relevant postings

Account-level intelligence compounds over time. This is where the system becomes a career market map.

## Contact Enrichment

Create Contacts only when there is a real person:

- Recruiter name from posting
- Hiring manager from company site
- LinkedIn contact added manually
- Email contact from application process

Do not create fake contacts from generic job posts.

## Task Automation

Create Zoho Tasks for:

- Score >= 85: apply within 24 hours
- Score 75-84: review within 3 days
- Applied and no response after 7 days: follow up
- Interview scheduled: prepare company brief
- Freelance lead score >= 80: draft proposal

## Zoho Pipeline

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

Freelance projects can use the same pipeline for now. Later, split into a separate `Freelance BD` pipeline if it becomes noisy.

## Enrichment Workflow Design

```text
Source intake
  -> normalize
  -> dedupe against Sheet and Zoho
  -> OpenAI score
  -> Sheet ledger
  -> IF score >= 70
       -> find/create Account
       -> create/update Deal
       -> IF recruiter exists: find/create Contact
       -> create Task based on score and stage
       -> add AI notes
```

## MCP Layer Later

MCP should sit on top of Zoho and answer operational questions:

- Show my highest-scoring Berlin opportunities from the last 3 days.
- Which companies are repeatedly hiring for trading infrastructure?
- Create follow-up tasks for stale applications.
- Draft a proposal for this Upwork trading bot lead.
- Find companies similar to Optiver but closer to AI infrastructure.

## MVP Recommendation

Implement in this sequence:

1. Keep all leads in Google Sheets.
2. Push score >= 70 to Zoho Deals.
3. Add Account find/create before Deal creation.
4. Add score-based Tasks.
5. Add Contact enrichment only when person data is available.
6. Add MCP read-only queries.
7. Add MCP write actions.

