# Source Strategy

Start with stable, lawful, API-friendly sources. Add fragile or terms-sensitive sources later.

## MVP Sources

| Source | Method | Notes |
| --- | --- | --- |
| Adzuna | API | Useful broad-market source with salary/location fields. Use after Berlin-first loop is stable. |
| Arbeitnow | Public API | Best first source for Berlin/Germany/Europe and English-speaking tech jobs. |
| Greenhouse | Public board API | Excellent for company-specific scanning. |
| Lever | Public postings API | Excellent for company-specific scanning. |
| Ashby / Workable / Personio | Public or semi-structured career feeds | Useful for startups, especially Germany/EU via Personio. |
| Google Custom Search / SerpAPI | Search API | Broad discovery when no job API exists. |
| Upwork URL polling | HTTP polling | Useful for freelance lead discovery when RSS is unavailable. Keep it compliant and light. |
| Bundesagentur fuer Arbeit / Arbeitsamt | API | Useful for Germany coverage, but less targeted for elite quant/AI roles. |
| Wellfound | Manual/API-like later | Add after core loop works. |
| Company career pages | Greenhouse/Lever first | Build a target-company list before broad scraping. |

## Defer

| Source | Reason |
| --- | --- |
| LinkedIn | Terms-sensitive and anti-automation heavy. Use manual exports or alerts first. |
| Google Jobs | Better reached via search APIs or alerts, not direct scraping. |
| Indeed | Terms-sensitive. Prefer API/partner/search-alert methods. |

## Recommended Order

1. Arbeitnow Germany/EU discovery.
2. Upwork URL polling for freelance leads.
3. Greenhouse company boards.
4. Lever company boards.
5. Curated target-company list.
6. Adzuna broad EU/worldwide discovery.
7. Ashby, Workable, and Personio.
8. Google Custom Search / SerpAPI.
9. Bundesagentur fuer Arbeit / Arbeitsamt if Germany coverage needs to be broader.
10. LinkedIn manual enrichment and networking only.

## Target Company Categories

- HFT and proprietary trading firms
- Crypto market makers
- Prediction market companies
- AI trading infrastructure companies
- Quant research platforms
- Financial data companies
- Low-latency infrastructure vendors
- Options analytics companies

## Strongest Search Terms

- sports betting quant
- betfair trading
- trading automation
- quantitative developer
- algorithmic trading
- market microstructure
- low latency python
- prediction markets
- crypto quant
- options trading
- reinforcement learning trading

## Upwork Polling Notes

Upwork RSS is not a dependable path. Treat Upwork as a polling source now and an Apify source later:

- Poll narrow saved-search URLs.
- Store extracted job URLs and only process unseen links.
- Keep frequency modest.
- Avoid credential/session automation unless you have a compliant API/Apify actor setup.
- Move to Apify when you need robust extraction, pagination, dedupe, and structured fields.

Suggested Upwork searches:

- quant trading
- sports betting model
- python trading bot
- algorithmic trading
- betfair trading
- prediction market
- crypto trading bot
- machine learning finance
