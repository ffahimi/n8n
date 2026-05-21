# MCP Roadmap

MCP becomes useful after the first loop produces reliable data in Zoho and Google Sheets.

## Stage 1: Read-Only Intelligence

Natural language queries:

- Show highest-scoring Berlin quant jobs from the last 3 days.
- Which companies overlap with prediction markets?
- Find stale applications with no follow-up task.
- Summarize weekly opportunity quality by region.

Recommended tools:

- Zoho CRM search/read tool
- Google Sheets read tool
- Local prompt library access

## Stage 2: Action Layer

Natural language actions:

- Move these 5 deals to High Priority.
- Create follow-up tasks for applications older than 7 days.
- Generate a tailored application brief for this opportunity.
- Draft a recruiter message based on the job and Farshad's profile.

Recommended tools:

- Zoho CRM update/create task tool
- Document generation tool
- Email draft tool

## Stage 3: Memory and Retrieval

Add embeddings and a vector store for:

- Companies
- Recruiters
- Historical job descriptions
- Application outcomes
- Resume variants
- Proposal templates

This enables similarity search:

- Companies similar to Jane Street but with AI infra roles.
- Roles similar to previous interviews.
- Recruiters connected to crypto trading or HFT firms.

