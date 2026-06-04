# Apollo.io API Documentation Reference

This file contains the key Apollo API endpoints and patterns Claude needs to power Steps 1 and 3 of the pipeline. Replace placeholder values with your actual parameters.

> 📎 For the full documentation, see: https://apolloio.github.io/apollo-api-docs/

---

## Authentication

All requests use your Apollo API key as a query parameter or in the request body:

```
api_key: YOUR_APOLLO_API_KEY  (from .env)
```

---

## Step 1 — Search Companies (Mixed Companies API)

**Endpoint:** `POST https://api.apollo.io/v1/mixed_companies/search`

**Purpose:** Pull a list of companies matching your ICP filters.

**Key filters to use:**
```json
{
  "api_key": "{{APOLLO_API_KEY}}",
  "q_organization_keyword_tags": ["video editing", "motion graphics"],
  "organization_locations": ["United States"],
  "organization_num_employees_ranges": ["20,500"],
  "page": 1,
  "per_page": 25
}
```

**Response fields to extract:**
- `id` — Apollo company ID (needed for enrichment)
- `name` — Company name
- `website_url` — Domain
- `linkedin_url`
- `estimated_num_employees`
- `industry`
- `keywords`

**Save to:** `output/companies.csv`

---

## Step 3 — Find Decision Makers (People Search API)

**Endpoint:** `POST https://api.apollo.io/v1/mixed_people/search`

**Purpose:** Find contacts at Tier 1 companies matching decision-maker titles.

**Key filters:**
```json
{
  "api_key": "{{APOLLO_API_KEY}}",
  "organization_ids": ["APOLLO_COMPANY_ID_1", "APOLLO_COMPANY_ID_2"],
  "person_titles": ["founder", "co-founder", "CEO", "head of production", "director"],
  "contact_email_status": ["verified"],
  "per_page": 5
}
```

**Response fields to extract:**
- `first_name`
- `last_name`
- `title`
- `email`
- `linkedin_url`
- `organization.name`
- `organization.website_url`

**Save to:** `output/contacts.csv`

---

## Notes

- Apollo rate limits: 200 requests/minute on paid plans.
- Use `per_page: 5` when finding contacts (5 per company is enough).
- Always verify `contact_email_status: ["verified"]` to avoid bounces.
- Log the Apollo company `id` in `output/companies.csv` so it can be referenced in Step 3 without a second lookup.
