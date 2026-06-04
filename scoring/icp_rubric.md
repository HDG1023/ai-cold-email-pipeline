# ICP Scoring Rubric

This file defines how Claude should evaluate and score each company pulled from Apollo. Customize every section for your specific offer and ideal customer profile.

---

## 🏷 Product / Offer Context

**Product:** [YOUR PRODUCT NAME]
**What it does:** [One sentence]
**Who it's for:** [ICP description]

---

## 📊 Scoring Criteria

Each company is scored out of **100 points** across the dimensions below. Be accurate — Claude will perform real web research on each company.

### 1. Company Size (0–25 pts)

| Employee Count | Points |
|---------------|--------|
| 500+ employees | 25 |
| 100–499 | 20 |
| 50–99 | 15 |
| 20–49 | 10 |
| < 20 | 0 |

### 2. Revenue / Budget Signals (0–25 pts)

| Signal | Points |
|--------|--------|
| Revenue > $2M/year (Crunchbase, LinkedIn, press) | 25 |
| Revenue $500K–$2M | 15 |
| Revenue < $500K or unknown | 5 |
| Non-profit / gov / no budget signals | 0 |

### 3. Service / Offering Fit (0–25 pts)

Does the company's core service align with what your product enables or enhances?

| Fit Level | Points |
|-----------|--------|
| Core offering directly matches ICP (e.g., video editing agency for a video tool) | 25 |
| Adjacent / partial fit | 15 |
| Tangential — could use it but not obvious | 5 |
| No fit | 0 |

### 4. Growth Signals (0–15 pts)

Check LinkedIn for recent hiring activity, job postings, and headcount growth.

| Signal | Points |
|--------|--------|
| Actively hiring in relevant roles (e.g., editors, designers) | 15 |
| Some relevant hires in last 6 months | 8 |
| No recent hiring signals | 0 |

### 5. Tech Stack / Tool Usage (0–10 pts)

Does their current tool stack suggest they're a good buyer for your product?

| Signal | Points |
|--------|--------|
| Uses tools that complement yours (verified via G2, LinkedIn, website) | 10 |
| Unknown tech stack | 3 |
| Uses a direct competitor | 0 |

---

## 🏆 Tier Thresholds

| Score | Tier | Action |
|-------|------|--------|
| 75–100 | **Tier 1** | Find decision makers & write sequences |
| 50–74 | **Tier 2** | Find decision makers (optional) |
| 25–49 | **Tier 3** | Do not target |
| 0–24 | **Disqualified** | Skip entirely |

---

## 📝 Scoring Instructions for Claude

1. For each company in `output/companies.csv`, search the web for their website, LinkedIn page, and any press mentions.
2. Score each dimension individually with a brief note explaining the score.
3. Sum the scores and assign a Tier label.
4. Write your output to `output/scored_companies.csv` with columns: `company_name`, `domain`, `total_score`, `tier`, `size_score`, `revenue_score`, `fit_score`, `growth_score`, `tech_score`, `scoring_notes`.
5. Only proceed to finding decision makers for **Tier 1** companies.
