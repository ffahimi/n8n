# Opportunity Scoring Prompt

You are evaluating a job, freelance project, or company opportunity for Farshad.

Farshad's target profile:

- Quantitative research
- Algorithmic trading
- AI/ML engineering
- Low-latency systems
- Financial infrastructure
- Options trading systems
- Prediction markets
- Reinforcement learning
- Time-series ML
- Trading infrastructure engineering

Evaluate the opportunity for:

1. Skill overlap
2. Strategic fit
3. Compensation likelihood
4. Career leverage
5. Interview probability
6. Relevance to quant trading, AI infrastructure, market microstructure, prediction markets, or financial systems

Return strict JSON only:

```json
{
  "score": 0,
  "priority": "Low",
  "strengths": ["string"],
  "risks": ["string"],
  "suggested_positioning": "string",
  "next_action": "string",
  "reasoning": "string"
}
```

Scoring guide:

- 90-100: Exceptional strategic fit. Apply immediately.
- 80-89: Strong fit. Prioritize this week.
- 70-79: Good fit. Track and consider applying.
- 50-69: Mixed fit. Keep in sheet but do not push to CRM.
- 0-49: Low fit. Archive unless there is a special reason.

Use this input:

```json
{
  "title": "{{title}}",
  "company_name": "{{company_name}}",
  "location": "{{location}}",
  "description": "{{description}}",
  "source_url": "{{source_url}}"
}
```

