# Google Sheets Setup

Create a spreadsheet with a tab named:

```text
Opportunities
```

Use these headers in row 1:

```text
external_id
source
source_url
title
company_name
location
region
description
employment_type
salary_min
salary_max
currency
posted_at
discovered_at
stage
score
priority
strengths
risks
positioning
next_action
reasoning
```

After creating the sheet:

1. Copy the spreadsheet ID from the URL.
2. Open the imported n8n workflow.
3. Replace `REPLACE_WITH_GOOGLE_SHEET_ID` in the `Append to Google Sheet` node.
4. Connect your Google Sheets OAuth2 credential.

