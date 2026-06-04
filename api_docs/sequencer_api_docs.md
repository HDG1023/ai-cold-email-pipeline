# Cold Email Sequencer API Documentation

This file provides the key API patterns for deploying prospects and sequences into your cold email tool. **Choose the section for your tool** and provide the full documentation URL to Claude before running Step 5.

---

## 🔧 Supported Tools

Choose one. Set `SEQUENCER_TOOL` in your `.env` file.

---

## Saleshandy

> Full docs: https://developers.saleshandy.com/

**Base URL:** `https://api.saleshandy.com/v1`

**Auth header:** `x-api-key: {{SEQUENCER_API_KEY}}`

### Create a Sequence
```http
POST /sequences
Content-Type: application/json

{
  "name": "[CAMPAIGN NAME]",
  "scheduleId": "[YOUR SCHEDULE ID]"
}
```

### Add a Prospect to a Sequence
```http
POST /sequences/{sequenceId}/prospects

{
  "email": "{{email}}",
  "firstName": "{{first_name}}",
  "lastName": "{{last_name}}",
  "companyName": "{{company_name}}"
}
```

### Add Email Steps
```http
POST /sequences/{sequenceId}/sequence-steps

{
  "type": "EMAIL",
  "subject": "{{subject_line}}",
  "body": "{{email_body}}",
  "waitDays": 1
}
```

---

## Smartlead

> Full docs: https://docs.smartlead.ai/

**Base URL:** `https://server.smartlead.ai/api/v1`

**Auth:** `?api_key={{SEQUENCER_API_KEY}}` appended to every URL

### Create a Campaign
```http
POST /campaigns/create

{ "name": "[CAMPAIGN NAME]" }
```

### Add Leads
```http
POST /campaigns/{campaignId}/leads

{
  "lead_list": [
    {
      "email": "{{email}}",
      "first_name": "{{first_name}}",
      "company_name": "{{company_name}}"
    }
  ]
}
```

---

## Instantly

> Full docs: https://developer.instantly.ai/

**Base URL:** `https://api.instantly.ai/api/v1`

**Auth header:** `Authorization: Bearer {{SEQUENCER_API_KEY}}`

### Create a Campaign
```http
POST /campaign/create

{ "name": "[CAMPAIGN NAME]" }
```

### Add Leads to Campaign
```http
POST /lead/add

{
  "campaign_id": "{{campaign_id}}",
  "skip_if_in_workspace": true,
  "leads": [
    {
      "email": "{{email}}",
      "first_name": "{{first_name}}",
      "company_name": "{{company_name}}"
    }
  ]
}
```

---

## Notes for Claude

- Always read this file before Step 5.
- Use the tool matching the `SEQUENCER_TOOL` value in `.env`.
- Sequence email steps should be added in order: Day 1 → Day 3 → Day 7 → Day 12.
- Wait days: Step 1 = 0 (send immediately), Step 2 = 2 days after Step 1, Step 3 = 4 days after Step 2, Step 4 = 5 days after Step 3.
- Always confirm the campaign was created before adding prospects.
