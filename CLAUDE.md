# Campaign Brain — AI Cold Email Pipeline

> ⚠️ Fill in every `[PLACEHOLDER]` below before running the pipeline. Claude reads this file at the start of every session.

---

## 🏢 Business Context

**Company / Product name:** [YOUR COMPANY OR PRODUCT NAME]

**What you sell (one sentence):** [e.g., "TiltIt is a 3D animation software that lets video editors produce 4K animations in under 30 seconds."]

**Target customer (ICP):** [e.g., "Video editing agencies in the USA with 20+ employees"]

**Key pain point you solve:** [e.g., "Manual 3D animation is slow and expensive — we automate it."]

**Pricing / Offer:** [e.g., "$99/month, free 14-day trial, no credit card required"]

**Proof / Results:** [e.g., "Used by 200+ agencies, average time saved: 8 hours/week"]

---

## 🔑 API Credentials

Store secrets in `.env`. Claude should read from `.env` and never log keys.

```
APOLLO_API_KEY=
SEQUENCER_API_KEY=
MAILDOSO_API_KEY=   # optional — for infrastructure management
```

---

## 🔄 Pipeline — Run in This Order

Execute each step sequentially. Store intermediate results as CSV files in `output/` so the pipeline can be resumed at any step.

1. **Find companies** — Use Apollo MCP to pull companies matching the ICP defined above. Apply filters from the scoring rubric. Save → `output/companies.csv`

2. **Score companies** — Apply `scoring/icp_rubric.md` to every row in `output/companies.csv`. Perform web research on each company (website, LinkedIn, job postings, revenue signals). Score and assign Tier 1 / 2 / 3. Save → `output/scored_companies.csv`

3. **Find decision makers** — For Tier 1 companies only, use Apollo to find decision makers (titles matching ICP criteria) with verified emails. Save → `output/contacts.csv`

4. **Write personalized sequences** — Using frameworks in `copy_frameworks/email_sequence_frameworks.md` and data in `output/contacts.csv`, generate a 4-step sequence (Day 1, 3, 7, 12) per contact with merge tags. Save → `output/sequences.csv`

5. **Deploy to sequencer** — Use the sequencer API (`api_docs/sequencer_api_docs.md`) to create a new campaign and import all contacts with their email copies.

6. **Manage infrastructure (optional)** — Use Maildoso API to monitor domain health, mailbox warm-up, and deliverability metrics.

---

## 📂 File References

| File | Purpose |
|------|---------|
| `scoring/icp_rubric.md` | Scoring criteria — read before Step 2 |
| `api_docs/apollo_api_docs.md` | Apollo endpoint reference — read before Steps 1 & 3 |
| `api_docs/sequencer_api_docs.md` | Sequencer API reference — read before Step 5 |
| `copy_frameworks/email_sequence_frameworks.md` | Copy templates & frameworks — read before Step 4 |
| `output_examples/example_campaign.md` | Reference for tone and structure — read before Step 4 |

---

## ✅ Output Requirements

- Every step must write a CSV to `output/` before proceeding.
- CSV column naming: use snake_case, descriptive names (e.g., `company_name`, `decision_maker_email`).
- Log reasoning for ICP scores in a `scoring_notes` column.
- Email copies should include merge tags in double curly braces: `{{first_name}}`, `{{company_name}}`, `{{personalization_line}}`.
- Subject lines: write 2 variants per email step.
- Never skip steps or combine them — each step's CSV output is the input for the next.

---

## ⚠️ Rules

- Keep this file under 200 lines to avoid context overflow.
- Never hardcode API keys — always read from `.env`.
- When in doubt about an API call, consult the relevant `api_docs/` file first.
- Use Python scripts for scoring (free, works at any scale).
- If a step fails, report the error and ask for guidance before retrying.
